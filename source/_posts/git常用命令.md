---
title: git常用命令
abbrlink: 423abe9e
date: 2021-08-16 16:16:18
tags: git
categories: Git
description: git相关知识
cover:
top_img:
---

# Git 命令行操作

## 设置签名

* 项目（仓库）级别`仅在当前本地库有效`

  ```
  git config user.name username
  git config user.email email
  ```

* 系统用户级别`仅在当前登录的操作系统用户有效`

  ```
  git config --global user.name username
  git config --global user.name email
  ```

## 进入文件目录`git init`初始化本地库

## 查看工作区状态git status

## 添加文件到暂存区
   `git add filename` 添加指定文件
   `git add .` 添加所有文件

## 暂存区文件提交到本地库`git commit -m 'commit message' fileName`

## 查看历史记录

   ```
   git log
   git reflog #常用
   git log --greph #图形显示，更直观
   git log --pretty=oneline #漂亮一行显示
   git log --oneline #简洁显示
   说明：HEAD@{移动到当前版本需要多少步}
   ```

## 前进后退版本

   * 基于索引值`推荐`

     ```
     git reset -- hard 版本号 #回到该版本
     ```

   * 使用^符号`只能后退`

     ```
     git reset --hard HEAD^ #几个^表示回退几步
     ```

   * 使用~符号`只能后退`

     ```
     git reset --hard HEAD~n #n代表回退几步
     ```


   reset的三个参数比较

   ```
   soft:
   	- 仅本地库移动HEAD指针
   mixed:
   	- 在本地库移动HEAD指针
   	- 重置暂存区
   hard:
   	- 在本地库移动HEAD指针
   	- 重置暂存区
   	- 重置工作区
   ```

## 分支管理

   | 命令名称             | 作用                         |
   | -------------------- | ---------------------------- |
   | git branch 分支名    | 创建分支                     |
   | git branch -v        | 查看分支                     |
   | git checkout 分支名  | 切换分支                     |
   | git merge 分支名     | 把指定的分支合并到当前分支中 |
   | git branch -b 分支名 | 创建分支并直接切换到该分支   |
   | git branch -d 分支名 | 删除分支                     |

   解决冲突：

   1. 修改冲突文件
   2. 添加到缓存区`git add 文件名`
   3. 提交到本地库`git commit -m '日志信息' `**注意：后面不能带文件名**

# Github

   ## 创建远程库别名

```
git remote -v #查看远程库地址别名
git remote add 别名 远程地址
```



   ## 推送
开发修改完把本地库的文件推送到远程仓库

```
git push 别名 分支名
git push -u 别名 分支名 #-u指定默认主机
```



   ## 克隆 `git clone 远程地址`

克隆下来后不要在主分支里面做开发

   ## 拉取

 本地存在clone下来的文件 就用pull更新

```
pull = fetch + merge
  	git fetch 别名 分支名
  	git merge 别名 分支名
git pull 别名 分支名
```

## 克隆

`git clone 链接`clone会自动有三步操作

1. 拉取代码
2. 初始化本地仓库
3. 创建别名

## 解决冲突
  不是基于远程库最新版做的修改不能推送，必须先pull下来解决冲突才能推送
  **解决冲突后提交的文件不能带文件名**

# Git相关问题及解决办法

1. remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
   解决办法：重新登录github账号，密码使用token，token在github中生成，然后复制保存留用
2. 若push时不提示输入用户名或密码
   解决办法：命令行输入`git config --system --unset credential.helper`
3. error: could not lock config file /usr/local/git/etc/gitconfig: Permission denied
   解决办法：命令行输入`sudo chgrp -R admin /usr/local`及`sudo chmod -R g+w /usr/local`

