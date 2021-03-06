---
title: "开源入门"
date: 2021-08-20
description: ""
tags: [开源]
featured_image: ""
images: []
categories: 技术
comment: true
draft: false
---


今年夏天有幸参与了 OSPP 2021 这个活动，终于第一次真正接触到向往已久的开源，以这篇文章记录我在这条路上的旅程，希望能越走越远，以后有更多经验分享给大家。

# 前言

首先我想说的是，参与开源并不是必须贡献代码，文档写作、视觉设计、组织宣传等也是项目中非常重要的部分。以及在项目社区或者 GitHub Issues 里进行反馈和解答其他人提出的问题，这些都是对开源社区很好的贡献。

参与开源你需要知道的最重要的事情就是，大胆提问，大胆提交 PR。

如果项目文档和谷歌搜索都不能解决你的疑问，不要害怕提问，项目维护者能够快速帮助你找到解决问题的方向，而且换个角度想，其他拥有同样疑惑的人也能搜索到你与项目维护者的交流过程，从中受益。也不要担心自己的代码不够好，项目维护者会对你提交的代码进行 review，如果有问题会给出建议，这其实是一个很好的学习机会。

在[这篇文章](https://www.igor.pro.br/publica/papers/saner2016.pdf)里有提到，实际上 28% 的贡献都是随意贡献（比如修正语法排版错误等），修补 bug 的贡献其实也只占到 30%。所以，不要担心，勇敢地在项目中积极交流贡献。

最后一点，保持礼貌！

# 开源指南放送

[GitHub 开源软件指南](https://opensource.guide/zh-hans/)

[Gitee 开源指北](https://gitee.com/opensource-guide/)

[开源最佳实践](http://surenpi.com/open-source-best-practice/)

# 参与项目的基本流程

## 找到你想要参与的项目

如果毫无头绪，我认为最好从自己熟悉的项目开始下手。在之前做项目的过程中肯定用过许多其他工具，在 GitHub 上搜索它们的项目仓库会是一个不错的开始。当然你也可以通过 GitHub 的 [Explore](https://github.com/explore/) 板块，或者 [Open Source Friday](https://opensourcefriday.com/) 之类的网站来寻找项目。

我的经验以前端为例，大多数项目都会有 website 仓库，用来维护官网，这是不错的入门方向。据我观察很多项目也会有专门的 console 或者 dashboard 仓库，我看过的几个都是用 React 搭建的。以及也可以尝试自己做一些博客主题开源。

请注意一个项目的活跃度以及最后活跃时间，项目维护者对 issue 以及 PR 的响应速度如何，以及整个项目的交流氛围，这些都是非常重要的考虑因素。 

较大的开源项目都会有 CONTRIBUTING 文档，用来说明如何为项目做贡献，请仔细阅读。

## 看看 `Issues` 都有些什么

很多开源项目在 Issues 板块都会有 `good first issue` ，这些 Issue 通常都比较容易上手，有的项目负责人还会给出一些参考指引，是为了让第一次参与该项目的贡献者能够快速熟悉和参与到项目中来。

如果你想要做出某个实际贡献，先看看 Issues 里有没有类似的问题以及是否被解决，如果没有，你可以先创建一个 Issue 让参与项目的其他人知道你要进行这方面的工作，总之，将问题进度公开，以避免重复劳动。

创建 Issue 要注意的问题：

- 提供具体的环境配置、操作步骤以及问题的详细情况
- 用文字描述，方便其他人检索
- 做好标签分类

## Pull Request 基本流程

如果你对项目里的一些问题有了解决方案，可以通过 pull request 提交代码。

1. `fork` 你想要参与的项目，它就会出现在你的仓库列表里
2. 将你自己仓库里的这个项目 `git clone` 到本地
3. 在本地仓库 `git remote add upstream 原仓库地址` ，与原仓库建立连接
4. 创建一个新的分支，然后开始修改代码 
5. 把改好的代码推送到自己的远程仓库
6. 在 GitHub 自己的仓库页面上就可以看到 `New pull request` 按钮

## 等待 review 结果

项目维护者会对你提交的代码进行 review，如果你提交的代码存在问题，对方会做出说明，希望调整代码或者是代码不被接受的原因。如果没有问题，你的代码就将会被 merge 到项目源码里，一次贡献就这样完成了！

如果你的 PR 暂时没有得到回应，请耐心等待，如果时间超过一周，可以尝试 @ 相关负责人。

# 参与到开源社区中

如果你对某个社区产生兴趣想要参与，在社区的官网或者 GitHub 以及各种社交媒体上都能找到联系方式（比如邮件列表、Slack、SIG 会议），很多开源社区还会专门举办关于如何参与开源贡献的主题会议。

SIG (Special Interest Group) ：很多社区会定期举办 SIG 会议，不要害怕参与进去。一般来说社区会维护每次 SIG 会议的会议文档以及会议录屏，也可以通过这些方式了解社区或者项目的动态。

# GitHub 上常见的交流缩写

- WIP：Work in progress, do not merge yet.  // 开发中
- LGTM：Looks good to me.  // PR 经过 review 没有问题
- CC：Carbon copy.  // 抄送某人
- RFC：request for comments.  // 我们来讨论下这个问题
- ACK：acknowledgement.
- NACK/NAK：negative acknowledgement. 
