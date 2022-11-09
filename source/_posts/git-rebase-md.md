---
title: git-rebase.md
date: 2022-11-09 15:58:35
tags:
- git
- rebase

categories:
- git
---

1. issue:

执行`git pull origin master --rebase`后发生冲突，开始解冲突，发现写的很多代码都没了。

2. reason:

rebase是一个一个commit执行的，前面的commit会有一些代码没有，正常现象

3. 解决:
    1. `git rebase --abort`退出，可完全回到rebase之前的状态，即使没解完冲突也没关系。
    2. 将多次commit合并成一个后再rebase
