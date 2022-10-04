---
title: hexo在多台设备上同时写blog.md
date: 2022-10-04 16:30:10
tags:
- hexo
- blog
category:
- hexo
---

1. 参考: 
   >https://cccshuang.github.io/2018/09/28/%E4%BD%BF%E7%94%A8%E5%A4%9A%E5%8F%B0%E7%94%B5%E8%84%91%E5%86%99Hexo%E5%8D%9A%E5%AE%A2/

2.需要在.zshrc中加入的本地配置:
```
# hexo
alias hexo-p="git add .; git commit -am "back up hexo files"; echo 11111111; git checkout hexo; git pull"
alias hexo-s="hexo clean; hexo g; hexo s"
alias hexo-c="rm -rf .deploy_git; hexo d -g; git add .; git commit -m 'back up hexo files'; git push"
```
3. 写blog前的准备和写完blog推送到远程仓库的方式
    1. 写blog前执行: `hexo-p`
    2. 写blog
    3. 写完blog后检查写的内容: `hexo-s`
    4. 推送blog到远程仓库：`hexo-c`
