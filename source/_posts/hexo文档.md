---
title: hexo文档
date: 2022-08-18 06:56:31
tags:
- hexo
- github
- next
- 标题编号
categories:
- hexo
---

# 命令

# 学习资料

- 官网：https://hexo.io/
- 视频教程：https://www.bilibili.com/video/BV1q741167PJ?p=9
- hexo+github: https://zhuanlan.zhihu.com/p/26625249
- 主题相关：
    - next主题：https://theme-next.js.org/

# 常见问题

## next主题配置文件位置

node_modules/hexo-theme-next/_config.yml

## next主题取消自动标题编号

将next主题配置文件的toc:number设为false

## hexo使用自动标题编号

在 Hexo 中，使用了一个 hexo 的插件， Hexo 根目录执行下面的命令

```
npm install hexo-heading-index --save

然后在 Hexo 根目录的 _config.yml 最后加上下面的配置:

heading_index:
  enable: true
  index_styles: "{1} {1} {1} {1} {1} {1}"
  connector: "."
  global_prefix: ""
  global_suffix: " "
  
重新生成即可。
```

