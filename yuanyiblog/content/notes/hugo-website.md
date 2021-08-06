---
title: "利用 Hugo 搭建网站"
weight: 10
---

本篇笔记介绍了如何利用 Hugo 框架搭建网站并部署到 GitHub 上，以及我在建站过程中遇到的一些问题

# 快速开始

## windows:
    
最简单的方法是直接下载 [最新版本的 hugo](https://github.com/gohugoio/hugo/releases) 安装

直接安装 extended 版本，可以对 scss 文件进行编译，否则在之后使用模板时会出现问题

注意：要把 hugo 的路径添加到环境变量 Path 中！

    我在下载安装扩展版本的时候有点问题，最后重新用 [Chocolatey](https://gohugo.io/getting-started/installing/#chocolatey-windows) 安装成功

## MacOS：

`brew install hugo`

## 新建网站

`hugo version` 检查安装是否成功

`hugo new site [sitename]` 创建一个新的网站

`hugo server` 开启 Hugo 服务器，可以在本地预览调试网站

# 结构目录
```
.
├── archetypes 
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
```

## `content` 文件夹
存放网站的主要内容 md 文件

在该文件夹下的文件结构目录直接对应网站结构

通常md文件开头如下（一般可以在 `archetypes` 文件夹中找到）：
```
---
title: "Helloworld"
date: {{ .Date }}
draft: true
---
```
除了 `title` 必需，其他可以省略

## `layouts` 文件夹
存放网站 HTML 模板，包括 index、particials、single page、list pages 等

## `themes`文件夹
存放现有的 Hugo 主题模板

## `config.toml` 文件
配置文件，最基础的设置如下：
```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "Blog"

[menu]
[[menu.main]]
    identifier = "about"
    name = "about"
    url = "/about"
    weight = 1  #weight数字越小排序越靠前
```

# 主题外观

可以直接使用 Hugo 现有的主题模板，也可以自己编写主题模板

## 使用现有主题

1. 在 [Hugo 官网](https://themes.gohugo.io/) 或者 GitHub 上寻找合适的 Hugo 主题

2. 进入 `themes` 文件夹，`git clone` 想要使用的主题

3. 在配置文件中添加主题：`theme = "themename"`

### 现有主题模板的个性化

在`themes`文件夹里主要修改 `assets` 和 `layouts` 两个文件夹，前者主要存放 css 和 js 文件，后者主要存放 html 文件

`layouts` 文件夹里主要修改 `partials` 和 `shortcodes` 文件夹里的 html 文件

## 自己创建主题

1. 在 `layout` 中创建 `_default` 文件夹、 `index.html` 和 `404.html` 文件

2. 在 `_default` 文件夹中创建 `single.html` 和 `list.html` 文件
    
3. 在 `static` 文件夹中创建 `css` 文件定义样式

注意：在 `_index.md` 中的内容永远都会依照 list 模板渲染，而非 single

# 站点部署

## 把网站部署到 GitHub 上

1. 在 GitHub 上创建一个新仓库，名字随便起（例如 blog），用于存放完整的代码。

2. 创建另一个新仓库，起名为 `github_id.github.io` （例如 yuanyi-au.github.io ），该仓库用于网站部署

3. 将本地代码与 GitHub 第一个仓库关联

4. 进入本地代码文件根目录：

`git submodule add -b main <第二个仓库的地址> public` 

生成 `public` 文件夹并将其关联到第二个仓库上，push 之后可以在 GitHub 第二个仓库页面上看到 `public` 文件夹的内容

5. 在第二个仓库的设置中可以找到 GitHub Pages，可以看到网站地址，也就是 `github_id.github.io`，就可以进行访问了

# 过程中遇到的问题

## Public 文件夹渲染出错

问题描述：`hugo server` 在本地运行时没有任何问题，但部署上线后打开网页发现渲染缺失 css 和 js 文件

搜索到别人提的 [issue](https://github.com/matcornic/hugo-theme-learn/issues/125) ,问题出在 Hugo 本身处理 URL 的方式上。

解决方法：

```
baseURL = "//example.org"
relativeURLs = true
uglyURLs = true
```

我尝试了没有用，简书上有人说可以直接把 `baseURL` 注释掉，我试了确实可行

# 参考链接

Hugo 官网上的视频教程，比较详细 [ YouTube Playlist ](https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)

如何创建自己的 Hugo 主题 [Creating your own Hugo Theme!](https://www.youtube.com/watch?v=wcMqrb3v2SM&list=LLm-KB0VAVChbSZPeDA_WqSg)

如何把个人博客部署到 GitHub 上 [Creating a Blog with Hugo and Github in 10 minutes](https://www.youtube.com/watch?v=LIFvgrRxdt4&t=247s)
