---
title: hexo配置.md
date: 2022-10-04 14:35:22
tags:
- hexo
categories:
- hexo
---
alias hexo-p="git commit -am "back up hexo files"; git checkout hexo; git pull"
hexo new xxx.md
alias hexo-s="hexo clean; hexo g; hexo s"
alias hexo-c="rm -rf .deploy_git; hexo d -g; git add .; git commit -m 'back up hexo files'; git push"

