---
title: AndroidStudio的Gradle配置
tags:
  - android
  - gradle
categories: 教程
description: AndroidStudio的Gradle配置
abbrlink: 1403
date: 2021-07-24 18:42:30
top_img:
---

# Gradle自动配置

最近由于更新了AndroidStudio所以相应的Gradle要更新下载

1. 关于Gradle下载推荐使用联通或电信网络，不要用移动网络

2. Gradle下载成功后便可以通过阿里云镜像源下载其他的jar包和相关插件

   1. 在本地.gradle文件夹下新建一个init.gradle的文件，内容为：

      ```gradle
      allprojects{
      repositories {
      def ALIYUN_REPOSITORY_URL = 'http://maven.aliyun.com/nexus/content/groups/public'
      def ALIYUN_JCENTER_URL = 'http://maven.aliyun.com/nexus/content/repositories/jcenter'
      all { ArtifactRepository repo ->
      if(repo instanceof MavenArtifactRepository){
      def url = repo.url.toString()
      if (url.startsWith('https://repo1.maven.org/maven2')) {
      project.logger.lifecycle "Repository ${repo.url} replaced by $ALIYUN_REPOSITORY_URL."
      remove repo
      }
      if (url.startsWith('https://jcenter.bintray.com/')) {
      project.logger.lifecycle "Repository ${repo.url} replaced by $ALIYUN_JCENTER_URL."
      remove repo
      }
      }
      }
      maven {
      url ALIYUN_REPOSITORY_URL
      url ALIYUN_JCENTER_URL
      }
      }
      }
      ```

      

   2. 然后再Android项目build.gradle文件的buildscript中repositories内和allprojects中repositories内添加如下代码

      ```gradle
      maven { url 'http://maven.aliyun.com/nexus/content/groups/public/' }
              maven { url 'http://maven.aliyun.com/nexus/content/repositories/jcenter' }
              maven { url 'http://maven.aliyun.com/nexus/content/repositories/google' }
              maven { url 'http://maven.aliyun.com/nexus/content/repositories/gradle-plugin' }
      ```

      之后重新build项目即可
   
   # 手动修改Gradle版本及Gradle插件版本
   
   详见[gradle版本及插件对应版本](https://developer.android.google.cn/studio/releases/gradle-plugin#updating-plugin)、[gradle国内下载网址](https://services.gradle.org/distributions/)、[gradle官网下载地址](https://gradle.org/releases/)

