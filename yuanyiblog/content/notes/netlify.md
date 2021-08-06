---
title: "使用 netlify 预览 GitHub 上的 PR"
weight: 200
---

netlify 是一个可以用来构建、部署、协作处理 Web 应用程序的云平台

本篇笔记介绍了如何在 GitHub 上添加 netlify 以便预览提交的 pull request 效果

# 安装准备

在 GitHub 上安装 [ Netlify ](https://github.com/apps/netlify)，授权 GitHub 账号

# New site from Git

选择平台 - 选择仓库 - 选择分支 - 基本设置 - deploy site

## 基本设置

[常见框架对应的 Build command 和 Publish directory](https://docs.netlify.com/configure-builds/common-configurations/)

## 为 PR 生成预览

进入 `Site settings > Build & deploy > Deploy notifications`

![](netlify-1.png)

选择 ”Add notification“ ，在下拉菜单中选择 “GitHub Pull Request Comment” ，然后选择 “Deploy Preview succeeded” ，保存

![](netlify-2.png)

现在每个新出现的 PR 都会自动生成一个评论，包含预览链接

## 修改域名

netlify 会自动以你的 site name 生成一个域名：`[name-of-your-site].netlify.app`

进入 `Domain Setting > Domain management > Custom domains`，可以通过修改 site name 修改域名

![](netlify-3)

# 参考资料

[ netlify 官网文档](https://docs.netlify.com/site-deploys/deploy-previews/)

[ How to Setup Previews For PRs on Your GitHub Repo Using Netlify ](https://levelup.gitconnected.com/how-to-setup-previews-for-prs-on-your-github-repo-using-netlify-105c80574875)