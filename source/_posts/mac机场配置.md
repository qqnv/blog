---
title: mac机场配置
tags:
  - mac
  - vpn
categories: 教程
description: mac机场配置
abbrlink: 35442
date: 2021-07-24 19:16:58
top_img:
---

1. 首先访问[vultr网站](https://my.vultr.com/)购买服务器
   1. Choose Server选择默认
   2. Server Location最好选择Los Angeles
   3. Server Type选择Ubuntu最新的即可
   4. Server Size选择$5每月的即可
   5. Additional Features选择Enable IPv6
   6. 其他的默认然后跳转新的页面会显示服务器正在下载，等大概1分钟后下载完成后会出现IP，copy等待使用，然后点击该条目进入详情可查看密码，IP及密码下步备用
2. 打开mac终端，依次输入
   `ssh root@上步中copy的IP`（连接服务器）
3. 按照提示输入yes然后输入密码
4. `git clone -b master https://github.com/Flyzy2005/ss-fly`（下载一键搭建ss脚本文件）
5. `ss-fly/ss-fly.sh -i password 1024`（运行搭建ss脚本代码，其中password为你想要设置的密码，1024为你想要设置的端口号，都可以自己更改）
6. 大概等5分钟后，终端会提示搭建完成，然后开启bbr加速`ss-fly/ss-fly.sh -bbr`
7. 之后下载小飞机填写提示搭建完成后给的信息即可，若搭建过程中有什么疑问可与我联系（Gmail:[qqnvblog@gmail.com](mailto:qqnvblog@gmail.com)）
