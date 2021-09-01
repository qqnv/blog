---
title: mac环境变量配置
tags:
  - mac
  - environment variable
categories: 教程
description: mac环境变量配置
abbrlink: 55469
date: 2021-07-24 18:40:31
top_img:
---

# 配置过程

1. 命令行输入：echo $PATH，查看已配置的环境变量
2. sudo vi ~/.bash_profile，进入环境变量配置文件
3. 默认是只读状态，键入i进入编辑状态
4. 编辑完成后，键入esc，然后键入:wq保存即可
5. 配置完成后可能需要重启才能生效，若想立即生效，需键入source ~/.bash_profile即可

# Mac环境变量的加载顺序

- /etc/profile
- /etc/paths
- ~/.bash_profile
- ~/.bash_login
- ~/.profile
- ~/.bashrc

前两个是系统级别的，系统启动就会加载，后面三个是用户级别，按照从前往后的顺序读取，若bash_profile存在，后面的几个文件就会被忽略不读了，~/.bashrc没有上述规则，它是bash shell打开的时候载入的。
也就是说在当前用户的目录下，如果又了.bash_profile文件就不会去加载.bashrc文件。
所以如果要能正常加载.bashrc文件，需要在.bash_profile文件的最末尾上加入如下语句：

```html
if [ -f ~/.bashrc ]; then
   source ~/.bashrc
fi
```

# 全局设置

- /etc/paths （全局建议修改这个文件）
  编辑时一行一个路径。<p style="color:red">注意：输入环境变量时，不用一个一个输入，只要拖拽文件夹到 Terminal 里就可以了。</p>
- /etc/profile （建议不修改这个文件）
  全局（公有）配置，不管是哪个用户，登录时都会读取该文件。
- /etc/bashrc （一般在这个文件中添加系统级环境变量）
  全局（公有）配置，bash shell 执行时，不管是何种方式，都会读取此文件。

# 若mac环境变量报错

找到.bash_profile文件

将以下代码添加到文件中

```javascript
#将maven bin加到PATH变量中
export PATH=$M2:$PATH
export PATH=/bin:/usr/bin:/usr/local/bin:${PATH}
```

# mac升级git版本

1. 安装Homebrew，终端输入
   
   ```html
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```
   
2. 安装最新版git
   `brew install git`
   
3. 配置环境变量，在环境变量配置文件中添加
   `export PATH="/usr/local/Cellar/git/2.32.0_1/bin:$PATH"`
   其中版本号可到`/usr/local/Cellar/git`下查看并修改
   
4. 键入`source ~/.bash_profile`使配置生效，输入`git --version`即可查看最新版本号
