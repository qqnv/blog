---
title: hexo自定义页面做首页
tags:
  - hexo
  - github
categories: 教程
description: hexo自定义页面做首页
abbrlink: 36418
date: 2021-07-24 19:12:29
top_img:
---

1. 新建一个仓库，可取名blog

2. 原博客根目录下修改_config.yml的内容

   ```yml
   url: https://xxx.com
   root: /blog/
   ```

   ```yml
   deploy:
   	repo: https://github.com/blog.git
   ```

3. 重新部署博客
   博客会重新上传到blog仓库中

4. 清空原来的仓库，上传自定义的首页代码即可
