---
title: git-command
date: 2018-09-29 17:09:02
tags: git
---

# Git command

## update a forked repo from remote repo.

```bash
git remote add upstream git@github.com:<custom>.git

git remote -v

git fetch upstream

git merge upstream/master

git push
```

## git 合并多个commits

[合并多个 Commit](https://www.jianshu.com/p/964de879904a)

## git拉取远程分支到本地

### 查看远程分支
```bash
git branch -r
```

### 拉取远程分支到本地分支
```bash
git checkout -b 本地分支名x origin/远程分支名x
```
### 取消最近的一次add
```bash
git reset <file>
git reset
```

### 取消本地修改
```bash
git checkout . #本地所有修改的。没有的提交的，都返回到原来的状态
git stash  #把所有没有提交的修改暂存到stash里面。可用git stash pop回复。
git reset --hard HASH #返回到某个节点，不保留修改。
git reset --soft HASH #返回到某个节点。保留修改 
```