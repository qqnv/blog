---
title: hexo搭建博客
tags:
  - hexo
  - github
  - blog
categories: 教程
description: hexo+github搭建博客教程
abbrlink: 56024
date: 2021-07-24 18:32:14
top_img:
---

 [我的hexo博客](https://qqnv.github.io)

# 安装git

# 安装node.js

# 命令行依次执行

1. npm install hexo-cli -g
2. hexo init blog
3. cd blog
4. npm install
5. hexo server

出现**图示1**即安装成功，blog即为新创建的博客文件夹，登陆图示网址即可本地访问
![图示1](https://cdn.qqnv.com/hexo1.png)

# 配置SSH

1. 创建和github同名的项目，项目名必须为github名
2. 命令行输入cd ~/. ssh检查本机已存在的ssh密钥，若提示No such file or directory，则说明是第一次使用git，否则说明ssh曾经配置过，直接执行第7步
3. 命令行执行git config --global user.name "username"//输入注册时的项目名，命令行执行git config --global user.email  "yourname@yourmail.com"//填写注册邮箱
4. 命令行输入ssh-keygen -t rsa -C '第3步中的邮箱'
5. 命令行输入cat ~/.ssh/id_rsa.pub查看本机的ssh配置
6. 进入GitHub主页，进入settings，左侧选SSH and GPG keys，将第5步shh配置内容粘贴到对应位置，title随便填个
7. 命令行输入ssh -T git@github.com,提示**图示2**即为成功![图示2](https://cdn.qqnv.com/hexo2.png)

# 配置blog文件夹中的_config.yml文件


```yml
title: **My Blog** #博客名称
subtitle: to be continued... #副标题
description: My blog #给搜索引擎看的，对网站的描述，可以自定义
author: **Yourname** #作者，在博客底部可以看到
email: yourname@yourmail.com #你的联系邮箱
language: **zh-CN** #中文，如果不填则默认英文
timezone: Asia/Shanghai
url: https://yoursite.com
deploy:
  type: git #部署的服务器类型
  repo: #username为你的github名称
    github: https://github.com/username/username.github.io.git
  name: username
  email: yourname@yourmail.com #你的电子邮件
  branch: master
```

# 连接到GitHub

cd到blog文件夹下，命令行依次执行

1. npm install hexo-deployer-git --save
2. hexo d
3. hexo g

登陆username.github.io即可访问

# 更换主题

1. 去GitHub上下载想要的主题放在themes目录下
2. 更改_config.yml中的theme属性为下载的主题文件夹名
3. 返回主目录命令行依次执行
   1. hexo generate
   2. hexo deploy

等待一分钟刷新页面即可

# 更改本地数据

命令行执行cd到blog目录下，依次执行

1. hexo clean（清除缓存）
2. hexo g（生成）
3. hexo s（启动本地服务，进行文章预览调试，退出服务用Ctrl+c）

# Hexo命令行常用命令

- npm install hexo-cli -g（Hexo安装）
- hexo init blog（Hexo第一个项目博客）
- cd blog（cd到blog目录下）
- npm install（安装依赖包）
- hexo server（启动本地服务器，开启预览访问端口（默认端口4000，'ctrl + c'关闭server））
- hexo new "postName" （新建文章）
- hexo new page "pageName" （新建页面）
- hexo generate （生成静态页面至public目录）
- hexo deploy （部署到GitHub）
- hexo help （查看帮助）
- hexo version （查看Hexo的版本）

缩写：

- hexo n == hexo new
- hexo g == hexo generate
- hexo s == hexo server
- hexo d == hexo deploy
- hexo s -g（生成本地预览）
- hexo d -g（生成并上传）

<p style="color:red">注：本文中所有username即为自己的GitHub注册名</p>
