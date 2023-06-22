---
title: "Hacker News Digest - 2023.06.22"
summary: "探索云原生领域的多样性景观, Quirky, Hashing, DevPod: 无服务商锁定的代码即开发环境平台, Exit traps 让你的 Bash 脚本更加健壮, pg_easy_replicate 实现零停机的 Postgres 版本迁移"
tags: ["hacker news"]
date: 2023-06-22
draft: false

---



{{< button href="https://www.craft.do/s/EgsKE518ubSsH8" target="_blank" >}}
Reading on Craft.do
{{< /button >}}
*2023.06.20 - 06.22*

<br/>

## 探索云原生领域的多样性景观


*Explore the Variety of Cloud-Native Landscape: the Dynamic World of Kubernetes and Beyond, Seifeddine Rajhi.*

[https://itnext.io/explore-the-variety-of-cloud-native-landscape-the-dynamic-world-of-kubernetes-and-beyond-dbf14d73d22c](https://itnext.io/explore-the-variety-of-cloud-native-landscape-the-dynamic-world-of-kubernetes-and-beyond-dbf14d73d22c)

文章从以下 6 个方面系统地梳理了 CNCF 生态的主要类别景观：


- 供应商（Provisioning）；
- 运行时（Runtime）；
- 编排管理（Orchestration & Management）；
- 应用开发（App Definition & Development）；
- 可观测性分析（Observability & Analysis）；
- 平台（Platforms）

很适合作为了解云原生生态概览的入门文章，另，这张 meme 我双手赞同 🙌🏻。

![image](https://miro.medium.com/v2/resize:fit:700/0*qpz3BAbT-VpLts-D)

<br/>

## Quirky: AI 制作炫酷二维码工具

{{< github repo="replicate/quirky" >}}

在 [Hacker News Digest - 2023.06.19](craftdocs://open?blockId=2FAB8450-37A4-4627-AC30-10444DE8CB90&spaceId=3244b567-56c9-a9dc-69a6-e81686ade52e) 中介绍了文章《*如何通过 Stable Diffusion 生成艺术二维码》*，Quirky 带来了一个云上的版本，基于 [Replicate](https://replicate.com/) 云机器学习平台和 Multi-ControlNet 分层控制模型，可以直接访问 [quirky.replicate.dev](https://quirky.replicate.dev/) 进行体验。

![image](https://res.craft.do/user/full/3244b567-56c9-a9dc-69a6-e81686ade52e/doc/21CE6B7A-7386-49E4-BBA7-25B81BABEF99/7AA2E7E4-E708-4A0E-AB55-579AD6ED1639_2/AO15eCq9DkShGWzN6QsmDXMZ1decJtzuPbkm2DyNT98z/Image.png)

**HN Ref**：[https://news.ycombinator.com/item?id=36411246](https://news.ycombinator.com/item?id=36411246)

<br/>

## Hashing：图解哈希函数原理



[https://samwho.dev/hashing/](https://samwho.dev/hashing/)

文章以图例、可视化交互的形式解释了 Hash 函数的工作原理，介绍了 Hash 函数的一个重要的评估标准雪崩效应（Avalanche Effect）。着重对比了 murmur3 和 stringSum 两种 Hash 算法，以可视化互动的方式演示了 murmur3 如何通过 randomisation 解决高相似输入引发的冲突。

![image](https://res.craft.do/user/full/3244b567-56c9-a9dc-69a6-e81686ade52e/doc/21CE6B7A-7386-49E4-BBA7-25B81BABEF99/1DA2EDD5-D731-4D6F-AB13-F43F0B83C454_2/hmLwdb1ul8p7aocNnZd2a8HynOODyhF343hDDxyxbJYz/Image.png)

**HN Ref**：[https://news.ycombinator.com/item?id=36401747](https://news.ycombinator.com/item?id=36401747)

<br/>

## DevPod：无服务商锁定的代码即开发环境平台


{{< github repo="loft-sh/devpod" >}}


类似 [Coder](https://coder.com/) 的代码即开发环境平台（Dev-environment-as-code），[Codespaces](https://github.com/features/codespaces) 的开源替代品。可以在任意基础设施启动可复制的开发环境，兼容 Intellij、VSCode 等主流 IDE，支持本地 Docker、Kubernetes、GCP、AWS、Azure 等基础设施供应方。

![image](https://github.com/loft-sh/devpod/raw/main/docs/static/media/devpod-flow.gif)

**HN Ref**：[https://news.ycombinator.com/item?id=36407477](https://news.ycombinator.com/item?id=36407477)

<br/>

## "Exit traps" 让你的 Bash 脚本更加健壮



*How "Exit Traps" Can Make Your Bash Scripts Way More Robust And Reliable.*

[http://redsymbol.net/articles/bash-exit-traps/](http://redsymbol.net/articles/bash-exit-traps/)

文章介绍了在 Bash script 中使用 exit traps 来实现过脚本过早退出时的资源清理行为，从而提高脚本的健壮和稳定。

**HN Ref**: [https://news.ycombinator.com/item?id=36400465](https://news.ycombinator.com/item?id=36400465)

<br/>

## pg_easy_replicate 实现零停机的 Postgres 版本迁移

{{< github repo="shayonj/pg_easy_replicate" >}}

pg_easy_replicate 是一个开源的 Postgres 逻辑复制 CLI 工具，可以实现不同版本 PG 之间的数据逻辑复制，其中最主要的场景实现零数据丢失、最小停机时间的 PG 在线升级。

类似项目有 pgEdge 于 2022 年开源的 PG 拓展 Spock：

{{< github repo="pgEdge/spock" >}}

**HN Ref**：[https://news.ycombinator.com/item?id=36405761](https://news.ycombinator.com/item?id=36405761)
