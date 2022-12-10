---
title: git-rebase.md
date: 2022-11-09 15:58:35
tags:
- git
- rebase

categories:
- git
---

## Steps

1. `git pull origin master --rebase`
2. 遇到第一个冲突，解决第一个冲突
3. 解决完后`git add .`
4. `git rebase --continue`
5. 循环执行2-3-4
6. 完成



## Issues:

   1. 执行`git pull origin master --rebase`后发生冲突，开始解冲突，发现写的很多代码都没了。

      1. reason:
        rebase是一个一个commit执行的，前面的commit会有一些代码没有，正常现象

      2. 解决:
          1. `git rebase --abort`退出，可完全回到rebase之前的状态，即使没解完冲突也没关系。
          2. 将多次commit合并成一个后再rebase: 
               > https://www.w3docs.com/snippets/git/how-to-combine-multiple-commits-into-one-with-3-steps.html#running-git-rebase-in-interactive-mode-4
