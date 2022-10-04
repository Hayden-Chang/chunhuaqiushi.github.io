---
title: git.md
date: 2022-10-01 22:08:28
tags:
- git
categories:
- git
---

- `git rebase [branch-name]/[commit-id] `

    - 将当前分支rebase到xxx分支上，head仍然指向的是当前分支。
    - 也可以直接rebase到某次commit上

    - 疑问
        - head指向的哪一个commit?

- `git checkout`

    - `git checkout commit-id/branch-name `

    head 直接指向commit-id，或

    - `git checkout branch-name^ `

    切换到branch-name分支最新commit的父节点

    - `git checkout branch-name^^ `

    切换到branch-name分支最新commit的父父节点

- `git branch -f [branch-name] [commit-id]`

    - 将某个branch-name指向某次commit-id 

- `git reset [commit-id]`

    - 将当前分支指向某个commit

- `git revert [commit-id]`

    - 回退某次commit-id

- `git rebase -i [commit-id]`

    - 以交互式的方式将当前分支rebase到某次提交上

- `git cherry-pick [commit-id-1] [commit-id-2] ......`

    - 在当前分支下面加入commit-id-1和commit-id-2

- `git commit -amend`

    - 在当前的commit-id中进行一些修改，合并到当前的commit-id中

- `git tag [tag-name] [commit-id]`

    - 给某个commit打标签，可以使用`git checkout [tag-name]`切换到某个标签上

- `git fetch`

    - 更新本地的远程分支

- `git pull`

    - 等价于`git fetch` + `git merge`

- `git pull --rebase`

    - 等价于`git fetch` + `git rebase`

- `git checkout -b [branch-name] [origin-branch-name] `

    - 跟踪远程分支

- `git branch -u [origin-branch-name]  [branch-name]`

    - 跟踪远程分支

- `git push origin [branch-name]`

    - 将branch-name的commit推送到远程仓库，同时指定了提交记录的来源和去向

- `git push origin [source]:[destination]`

    - 将本地源分支推送到目的远程分支
    - tip: source是本地的，destination是远程的

- `git fetch origin [source]:[destination]`

    - 将远程分支的提交下载到本地分支
    - tip: source是远程的，destination是本地的
    - `git fetch origin :[destination]`
        - 在本地新建destination分支

- `git pull origin [source]:[destination]`

    - 相当于两步操作：`git fetch origin [source]:[destination]` + `git merge [destination]`

- ！！！危险操作

    - `git push origin :foo`
        - 删除远程的foo分支
