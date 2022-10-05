---
title: git修改历史commit.md
date: 2022-10-05 11:36:36
tags:
- git
- commit
- 修改
categories:
- git
---

目的：修改commit 14的文件和commit message

1. 添加commit

    1. `vim 14.txt`
    2. `git add 14.txt`
    3. `git commit -m "14"`
    4. `vim 15.txt`
    5. `git add 15.txt`
    6. `git commit -m "15"`
    7. `vim 16.txt`
    8. `git add 16.txt`
    9. `git commit -m "16"`

2. 将代码推送到远程仓库: `git push`

3. 查看历史提交记录: `git log`:

    ```
    commit e44e19ae40a237eb79c979be90e29c2e416b6414 (HEAD -> main, origin/m
    ain)
    Author: haichao.zhang <haichao.zhang@momenta.ai>
    Date:   Wed Oct 5 11:09:40 2022 +0800
    
        16
    
    commit 534f6e17db76010959c7b0a6dbaee813eafc84ce
    Author: haichao.zhang <haichao.zhang@momenta.ai>
    Date:   Wed Oct 5 11:09:24 2022 +0800
    
        15
    
    commit eb7adcbac440735d7152b2cdc5fd3f8e42ca3d2b
    Author: haichao.zhang <haichao.zhang@momenta.ai>
    Date:   Wed Oct 5 11:09:04 2022 +0800
    
        14
    
    commit 2b1dfcb4ee2f99cefde134dcaba3a54984af7c1a
    Merge: 5d7182e 56891cf
    Author: haichao.zhang <haichao.zhang@momenta.ai>
    Date:   Wed Oct 5 11:05:00 2022 +0800
    
        merge
    ```

4. 以交互的方式选择要修改的commit`eb7adcbac440735d7152b2cdc5fd3f8e42ca3d2b`

    1. `git rebase -i eb7adcbac440735d7152b2cdc5fd3f8e42ca3d2b`

        result:

        ```
          1 pick eb7adcb 14
          2 pick 534f6e1 15
          3 pick e44e19a 16
          4
          5 # Rebase 2b1dfcb..e44e19a onto 2b1dfcb (3 commands)
          6 #
          7 # Commands:
          8 # p, pick <commit> = use commit
          9 # r, reword <commit> = use commit, but edit the commit message
         10 # e, edit <commit> = use commit, but stop for amending
         11 # s, squash <commit> = use commit, but meld into previous commit
         12 # f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
         13 #                    commit's log message, unless -C is used, in which case
         14 #                    keep only this commit's message; -c is same as -C but
         15 #                    opens the editor
         16 # x, exec <command> = run command (the rest of the line) using shell
         17 # b, break = stop here (continue rebase later with 'git rebase --continue')
         18 # d, drop <commit> = remove commit
         19 # l, label <label> = label current HEAD with a name
         20 # t, reset <label> = reset HEAD to a label
         21 # m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
         22 # .       create a merge commit using the original merge commit's
         23 # .       message (or the oneline, if no original merge commit was
         24 # .       specified); use -c <commit> to reword the commit message
         25 #
         26 # These lines can be re-ordered; they are executed from top to bottom.
         27 #
         28 # If you remove a line here THAT COMMIT WILL BE LOST.
        ```

        

    2. 将第一行的`pick eb7adcb 14`改为`edit eb7adcb 14`，输入`wq`保存退出。此时终端变成: `~/p/practice-git @eb7adcba rebase-i 1/3 >`

5. 输入 `vim 14.txt`，在文件的最下面加一行`xxxxxxxxxxxxxxxx`。(模拟对文件的修改)

6. 输入`git add 14.txt`，将文件加入到暂存区。

7. 输入`git commit --amend`，result如下

    ```
     1 COMMIT_EDITMSG                                                                                                               Buffers
      1 14
      2
      3 # Please enter the commit message for your changes. Lines starting
      4 # with '#' will be ignored, and an empty message aborts the commit.
      5 #
      6 # Date:      Wed Oct 5 11:09:04 2022 +0800
      7 #
      8 # interactive rebase in progress; onto 2b1dfcb
      9 # Last command done (1 command done):
     10 #    edit eb7adcb 14
     11 # Next commands to do (2 remaining commands):
     12 #    pick 534f6e1 15
     13 #    pick e44e19a 16
     14 # You are currently editing a commit while rebasing branch 'main' on '2b1dfcb'.
     15 #
     16 # Changes to be committed:
     17 #       new file:   14.txt
     18 #
    ```

    将第三行的`14`改为`14-x`，输入`wq`保存退出。此时终端变成`~/p/practice-git @2a24d213 rebase-i 1/3 >`。(模拟对commit-message的修改)

8. 输入`git rebase --continue`，使head指向此分支的最新commit。此时终端变成`~/practise/practice-git main <3>3 >`

9. 输入`git push -f`，将代码推送到远程仓库。（加-f的目的是强制使远程仓库是用本地仓库提交的结果，否则git不知道到底要对14.txt文件使用哪一次的结果。所以如果commit已经推送到了远程仓库，一定要加`-f`；如果commit还未推送到远程仓库，不需要要加`-f`）

10. 注意：在使用`git rebase --continue`命令时，可能会遇到各种各样的问题。需要问题后再补充。
