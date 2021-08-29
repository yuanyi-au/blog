---
title: "git 笔记 (2)"
weight: 50
---

# git rebase

## 合并不同分支的提交

将 b 分支上的提交合并到 a 分支上成为一条直线

```
git checkout b
git rebase a
```

## 与 merge 的区别

*永远不要在公共项目里使用 rebase*

merge 采用的是三方合并的原则，没有公共提交节点就无法进行合并

git rebase:
![](../images/git-rebase.jpg)

git merge:
![](../images/git-merge.jpg)

rebase 和 merge 的另一个区别是 rebase 的冲突是一个一个解决，先解决第一个，然后用命令

```
git add -u
git rebase --continue
```

继续后才会出现第二个冲突，直到所有冲突解决完，而 merge 是所有的冲突都会显示出来。另外如果 rebase 过程中，你想中途退出，恢复 rebase   前的代码则可以用命令 

`git rebase --abort`

## 合并本地的多次提交

合并最新的三次提交

`git rebase -i HEAD~3`

git reabse -i 合并 commit 之后会出现一个匿名的分支，并不是在原来的分支上把 commit 给合并，而是从合并的 start point 开始新生成一个匿名分支然后把原来分支那几个 commit 作为一个 commit 放到新分支上

# cherry-pick

将其他分支上的提交应用于 a 分支

```
git checkout a
git cherry-pick <CommitID>
```

## 与 rebase 的区别

rebase 相当于剪切粘贴， cherry-pick 相当于复制粘贴

# git reset 与 git revert

## git reset

回退到指定的提交版本

## git revert

用一个新的提交来消除之前的提交，原来的 commit 内容依旧会保存在提交历史中

## 两者的区别

reset 是在正常的提交历史中,删除了指定的 commit ，HEAD 向后移动，而 revert 是在正常的提交历史中再 commit 一次，只不过是反向提交可以抵消之前的提交，它的HEAD 是一直向前的

# git pull 和 git fetch 的区别

打开本地 `.git/refs` 文件夹我们可以看到代表本地分支的 `head` 文件夹和代表正在跟踪的远程分支的 `remotes` 文件夹

使用 git pull 会将两个文件夹里的 commit ID 都更新至远程库的最新 commit ID

使用 git fetch 只会将 `remotes` 文件夹中的 commit ID 更新至远程库的最新 commit ID

# git blame

可以查看某个文件里每一行代码的最后修改提交记录

`git blame <filename>`

# sign-off

在做开源项目时遇到要求 sign-off，用于证明提交作者

`git commit -s -m ""`

# 参考资料

[git rebase简介(基本篇)](https://blog.csdn.net/hudashi/article/details/7664631?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0.control&spm=1001.2101.3001.4242)

[你真的懂git rebase吗？](https://www.jianshu.com/p/6960811ac89c)

[Git应用详解第九讲：Git cherry-pick与Git rebase](https://blog.csdn.net/qq_43425487/article/details/105620270)

[Git版本恢复命令reset和revert](https://blog.csdn.net/xybelieve1990/article/details/62885292?utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control)

[详解git pull和git fetch的区别](https://blog.csdn.net/weixin_41975655/article/details/82887273)

[git fetch和git pull之间的区别](https://blog.csdn.net/a19881029/article/details/42245955)