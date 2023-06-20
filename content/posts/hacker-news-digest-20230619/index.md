---
title: "Hacker News Digest - 2023.06.19"
summary: "Novel：Notion 风格的文本编辑器, Bloop：基于 GPT-4 代码库阅读工具, Dolt: Git 版本化数据, Resend: 现代化邮件发送 API 平台, 通过 Stable Diffusion 制作艺术化的二维码"
tags: ["hacker news"]
date: 2023-06-19
draft: false

---

{{< button href="https://www.craft.do/s/tNGQAzPWECEHvP" target="_blank" >}}
Reading on Craft.do
{{< /button >}}

<br/>
<br/>


## Novel：Notion 风格的文本编辑器

{{< github repo="steven-tey/novel" >}}

Novel 是一个开源的 Notion 风格的 WYSIWYG（所见即所得）文本编辑器，基于 Next.js、TailwindCSS 编写，并借助 OpenAI 提供了 AI 自动补全的特性。具有十分浓烈的 Vercel 味，毕竟是 Vercel 的 Senior DA Steven Tey 的作品。

![opengraph-image.png](https://github.com/steven-tey/novel/raw/main/app/opengraph-image.png)

Steven Tey 最近有一期接受 kfund 采访的关于开发者关系的 Podcast 十分值得一听：

[#PodKast 181 Steven Tey (Vercel): understanding the role of developer relations](https://www.youtube.com/watch?v=MfaeF8q9RJA)

**HN Ref**：[https://news.ycombinator.com/item?id=36360789](https://news.ycombinator.com/item?id=36360789)

<br/>

## Bloop：基于 GPT-4 代码库阅读工具

{{< github repo="BloopAI/bloop" >}}

Bloop 是一个 Rust 编写的代码检索引擎，基于 GPT-4 以自然语言对话的方式来检索、回答有关代码库的问题，支持本地、远程 Github 代码仓库两种来源。这对于理解陌生项目十分有效，同时支持基于已有上下文编写新代码，由于对索引了整体代码，从结果的相关性上要略好于 Github Copilot。

Bloop 的查询索引由 [Tantivy](https://github.com/quickwit-oss/tantivy) 和 [Qdrant](https://github.com/qdrant/qdrant) 提供，Tantivy 是一个 Rust 编写的类似 Apache Lucene 的全文搜索引擎，Qdrant 是 Rust 编写的矢量数据库，而客户端则是这几年广受欢迎的 [Tauri](https://github.com/tauri-apps/tauri)，All in Rust 了属于是 🤣。

![Image.gif](https://camo.githubusercontent.com/ea2837b902958a2ea33a08f3e1819e11e93d1a43137417931bbcbf82ffd7ac36/68747470733a2f2f6173736574732e626c6f6f702e61692f6769746875625f617574685f346b2e676966)

属实良心的是，Bloop 的免费帐户目前没有硬性限制，只有在个人超过 20 个用户或 100 个同步仓库才会降低相应的性能。

**HN Ref**：[https://news.ycombinator.com/item?id=36260961](https://news.ycombinator.com/item?id=36260961)

<br/>

## Dolt: Git 版本化数据

{{< github repo="dolthub/dolt" >}}

Dolt 是一个以类 Git 进行版本控制的 SQL 数据库，即类似 Git 一样的 fork、clone、branch、merge、pull、push 的操作来更新数据，同时以 SQL 来查询数据，就像Git 和 MySQL 的缝合怪（It's like Git and MySQL had a baby）。

![Image.png](https://res.craft.do/user/full/3244b567-56c9-a9dc-69a6-e81686ade52e/doc/9C07E684-DE6B-472A-9D31-E0AEEEDC07A4/66750C31-66F2-4648-B65A-2C5AB1F3A8BA_2/BL5xRfiM1w2dNNoBop6JpYPpifF3PGRR5Udg50FFewQz/Image.png)

此外他们还创建 DoltHub 项目用于共享用户公开的 Dolt 数据，这为解决公共领域的数据集的变迁、溯源提供了一种新的思路。

[https://www.dolthub.com/](https://www.dolthub.com/)

**HN Ref**：[https://news.ycombinator.com/item?id=36152590](https://news.ycombinator.com/item?id=36152590)

（原 HN 其实是讨论 DoltHub 上一个美国社区医院价格数据集的 XD）

<br/>

## Resend: 现代化邮件发送 API 平台

[resend.com](https://resend.com/)

Resend 提供了一个现代化的邮件发送平台，专注于提供最佳的开发人员体验。核心卖点是可以基于 React 而非过时的布局来编写复杂的 HTML 邮件内容，同时提供邮件发送的事务性、可观察性和高速性能。

![Image.png](https://res.craft.do/user/full/3244b567-56c9-a9dc-69a6-e81686ade52e/doc/9C07E684-DE6B-472A-9D31-E0AEEEDC07A4/CBB7A11F-2D00-4782-9767-B230291C1BB9_2/0PfonfSQMw1yqxQzsewMEAa9M6W7aDk6uYxxixDhfyAz/Image.png)

**HN Ref**：[https://news.ycombinator.com/item?id=36309120](https://news.ycombinator.com/item?id=36309120)

<br/>

## 通过 Stable Diffusion 制作艺术化的二维码

[How to make a QR code with Stable Diffusion - Stable Diffusion Art](https://stable-diffusion-art.com/qr-code/)

文章介绍了如何通过 Stable Diffusion ControlNet 拓展生成艺术化的二维码。

![01091-2150462366.png](https://i0.wp.com/stable-diffusion-art.com/wp-content/uploads/2023/06/01091-2150462366.png?resize=750%2C750&ssl=1)
![image-57.png](https://i0.wp.com/stable-diffusion-art.com/wp-content/uploads/2023/06/image-57.png?resize=750%2C750&ssl=1)

**HN Ref**: [https://news.ycombinator.com/item?id=36285630](https://news.ycombinator.com/item?id=36285630)

<br/>
<br/>

[🦑  Hacker News Digest Archive](https://www.craft.do/s/G2rGE9r4sCSydi)