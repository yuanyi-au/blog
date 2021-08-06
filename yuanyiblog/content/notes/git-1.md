---
title: "git 笔记(1) 基础入门"
weight: 40
---

本篇笔记的内容包括常用命令以及 commit message 规范

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


# `commit message` 规范




# 参考资料

[常用 Git 命令清单](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

