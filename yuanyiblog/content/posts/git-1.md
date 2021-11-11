---
title: "git 笔记 (1)"
date: 2021-07-24
description: ""
tags: [Git]
featured_image: ""
images: []
categories: 技术
comment: true
draft: false
---

本篇笔记内容包括常用命令以及 commit message 规范

# 常用命令

## 名词

workplace 工作区 

stage 暂存区

repository 本地仓库

remote 远程仓库

![](https://www.ruanyifeng.com/blogimg/asset/2015/bg2015120901.png)

## 新建仓库

`git init` 在当前目录新建一个本地仓库

`git clone` 将一个远程仓库的内容下载到本地

## 文件的增加、删除、提交

`git add [filename]` 将文件从工作区添加到暂存区

`git rm [filename]` 删除工作区文件

`git rm --cached [filename]` 停止追踪指定文件，但该文件会保留在工作区

`git mv [originalname] [newname]` 文件重命名，并将该文件放入暂存区

`git commit - "message"` 将暂存区文件提交到本地仓库

`git commit -amend -m "message"` 用一次新的 commit 代替上次 commit，可以用来改写 commit message

## 分支管理

`git branch` 查看所有本地分支

`git branch -a` 查看所有本地分支与远程分支

`git branch [branch]` 新建一个分支，但依然停留在当前分支

`git checkout -b [branch]` 新建一个分支并切换到该分支

`git checkout [branch]` 切换到指定分支，并更新工作区

`git merge [branch]` 将指定分支合并到当前分支

`git branch -d [branch]` 删除本地分支

`git push origin --delete [branch]` 删除远程分支

## 远程仓库

`git remote -v` 查看所有远程仓库

`git remote add [name] [url]` 添加远程仓库

`git remote remove [name]` 删除远程仓库

`git fetch [remote]` 下载远程仓库的所有变动

`git pull [remote] [branch]` 下载远程仓库的变动并与本地仓库合并

`git push [remote] [branch]` 将本地分支推送到远程分支

## 其他

`git config --list` 显示当前配置

`git config -e` 编辑配置文件

`git status` 显示所有变更文件

`git log` 显示当前分支的版本历史

`git reset --soft [commit_id]` 回退到某一个 commit 版本，工作区和暂存区不变

`git reset --hard [commit_id]` 回退到某一个 commit 版本，工作区和暂存区也随之更改

`git diff` 显示暂存区与工作区的差异


# commit message 规范

![不同的 commit message 规范](https://d33wubrfki0l68.cloudfront.net/eb16595d0c6862c0c013a36c339317a4d82bdce7/9195b/images/posts/2019-11-01-understanding-semantic-commit-messages-using-git-and-angular/conventions-diagram.png)

通常我们都用 Angular 的规范，具体可以参见 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

## 组成

commit message 包括三部分：header，body 和 footer

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Header

- type：用于说明 commit 的类别
    - feat：增加新功能
	- fix：修 bug
	- docs：文档变动
	- style：格式变动，不改变代码逻辑
	- refactor：重构（既非feat又非fix的影响代码运行的改动）
	- test：增加测试
	- chore(or build)：构建过程或辅助工具变动
	- ci：与持续集成相关的变动
	- perf：改善性能
- scope：用于说明 commit 影响的范围，例如数据层、控制层、视图层等
- subject：用于描述 commit 目的

### Body

对 commit 的详细描述，可以分成多行

### Footer

只用于两种情况：
  - 当前代码与上一版本代码不兼容，则 footer 以 BREAKING CHANGE 开头，接着描述变动的内容、理由及迁移方法
  - 针对某个 Issue，可以在 footer 部分关闭这个 Issue `Close #65 #77`

### Revert

如果当前 commit 是用来撤销之前的 commit，则必须以 `revert:` 开头，后面跟着被撤销的 commit 的 header 

body 部分则必须写成:
 ```
 This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
 ```

## 规则

优秀的 commit massage 应该遵循以下七条规则：

1. subject 和 body 之间空一行
2. subject字数限制在50字符以内
3. 行首字母大写
4. subject 不要以句号结尾
5. subject 使用祈使句
6. body 不超过72个字符
7. 用 body 部分解释此次 commit 的改动及其原因

## 示例

```
feat(lang): add polish language
```

```
refactor!: drop support for Node 6 //使用感叹号代表 breaking change
``` 

```
fix: correct minor typos in code

see the issue for details

on typos fixed.

Reviewed-by: Z
Refs #133
```

# 参考资料

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)

[How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)

[Understanding Semantic Commit Messages Using Git and Angular](https://nitayneeman.com/posts/understanding-semantic-commit-messages-using-git-and-angular/)

[常用 Git 命令清单](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

[Commit message 和 Change log 编写指南](https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)