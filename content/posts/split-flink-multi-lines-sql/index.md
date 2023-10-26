---
title: "如何切分多行 Flink SQL ?"
summary: "在编写烂大街的 Flink SQL 应用提交设施时，将多行 Flink SQL 文本切分成多行是一个再正常不过的步骤..."
tags: [ "Flink", "SQL" ]
date: 2023-10-26
draft: false

---

在编写烂大街的 Flink SQL 应用提交设施时，将多行 Flink SQL
文本切分成多行是一个再正常不过的步骤了，毕竟 `TableEnvironment.executeSql` API 仅能接收单个 statement。

```java
public static List<String> splitSqls(String sqls)
```

大摆烂直接 `sqls.split(";").toArray`  再朴素不过，但是 `;`  本身是可以作为 SQL 字面量，比如以下情况显然无法满足：

```sql
select replace(';', '_')
from datagen;
```

## 基于字符规则

依旧是朴素的逐字符匹配方式，但是考虑 `;`  作为字面量。

```java
public static List<String> splitSqls(String sqls){
        List<String> sqlList=new ArrayList<>();
        boolean insideDoubleQuotes=false;
        boolean insideSingleQuotes=false;
        StringBuilder currentSql=new StringBuilder();

        for(char c:sqls.toCharArray()){
        if(c=='"'){
        insideDoubleQuotes=!insideDoubleQuotes;
        }else if(c=='\''){
        insideSingleQuotes=!insideSingleQuotes;
        }

        if(c==';'&&!insideDoubleQuotes&&!insideSingleQuotes){
        sqlList.add(currentSql.toString());
        currentSql=new StringBuilder();
        }else{
        currentSql.append(c);
        }
        }

        if(currentSql.length()>0){
        sqlList.add(currentSql.toString());
        }
        return sqlList.stream().map(String::trim).filter(e->!e.isBlank()).collect(Collectors.toList());
        }
```

## 基于 Calcite Parser

Flink SQL 本身使用 Calcite 作为 Parser，直接通过 Calcite 来切分 SQL 也算是某种程度上的原汤化原食。

```java
import org.apache.calcite.avatica.util.Casing;
import org.apache.calcite.avatica.util.Quoting;
import org.apache.calcite.sql.SqlNode;
import org.apache.calcite.sql.SqlNodeList;
import org.apache.calcite.sql.parser.SqlParser;
import org.apache.flink.sql.parser.impl.FlinkSqlParserImpl;

public static List<String> astSplit(String sqls)throws SqlParseException{

        SqlParser.Config config=SqlParser.config()
        .withParserFactory(FlinkSqlParserImpl.FACTORY)
        .withIdentifierMaxLength(256)
        .withQuoting(Quoting.BACK_TICK)
        .withQuotedCasing(Casing.UNCHANGED)
        .withUnquotedCasing(Casing.UNCHANGED);

        SqlParser parser=SqlParser.create(sqls,config);
        SqlNodeList nodes=parser.parseStmtList();

        return nodes.stream()
        .map(SqlNode::toString)
        .collect(Collectors.toList());
        }
```

