---
title: "利用 Hugo 搭建网站"
weight: 10
---

# 快速开始

## windows:
    
最简单的方法是直接下载 [最新版本的 hugo](https://github.com/gohugoio/hugo/releases) 安装

建议安装 extended 版本，可以对 scss 文件进行编译，否则在之后使用模板时会出现问题

注意：要把 hugo 的路径添加到环境变量 Path 中！

*我在下载安装扩展版本的时候有点问题，最后重新用 [Chocolatey](https://gohugo.io/getting-started/installing/#chocolatey-windows) 安装，也很方便大家可以试试*

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

## 自己创建主题

1. 在 `layout` 中创建 `_default` 文件夹、 `index.html` 和 `404.html` 文件

2. 在 `_default` 文件夹中创建 `single.html` 和 `list.html` 文件
    

3. 在 `static` 文件夹中创建 `css` 文件定义样式

注意：在 `_index.md` 中的内容永远都会依照 list 模板渲染，而非 single

# 站点部署