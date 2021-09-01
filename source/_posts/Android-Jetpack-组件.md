---
title: Android Jetpack 组件
abbrlink: b16bf6c
date: 2021-08-23 01:02:18
tags:
categories:
description:
cover:
top_img:
---

Jetpack是一个由多个库组成的套件，可帮助开发者遵循最佳做法，减少样板代码并编写可在各种Android版本和设备中一致运行的代码，让开发者精力集中编写重要的代码。

为何使用Jetpack

* 遵循最佳做法
  Android Jetpack组件采用最新的设计方法构建，具有向后兼容性，可以减少崩溃和内存泄露。
* 消除样板代码
   Android Jetpack可以管理各种繁琐的Activity（如后台任务、导航和生命周期管理），以便您可以专注于打造出色的应用。
* 减少不一致
  这些库可在各种Android版本和设备中以一致的方式运作，助您降低复杂性。

# LifeCycle

## 作用

* 帮助开发者建立可感知生命周期的组件
* 组件在其内部管理生命周期，从而降低模块耦合度
* 降低内存泄漏发生的可能性
* Activity、Fragment、Service、Application均有LifeCycle支持

## 应用

* 使用LifeCycle解耦页面与组件
* 使用LifeCycleService解耦Service与组件
* 使用ProgressLifeServiceOwner监听应用程序生命周期

# ViewModel

## 要解决的问题

* 瞬态数据丢失（保证屏幕旋转之后用户数据仍然存在）
  ViewModel的生命周期特性：独立与配置变化，无论Activity生命周期怎么变化，对ViewModel数据都没有影响，finish()时数据才会清空
* 异步调用的内存泄漏
* 类膨胀提高维护难度和测试难度

## 作用

* 是介于View（视图）和Model（数据模型）之间的桥梁
* 使视图和数据能够分离，也能保持通信

## 注意的问题

* 不要向ViewModel中传入Context，会导致内存泄漏
* 如果要使用Context，请使用AndroidViewModel中的Application

# LiveData

## 在ViewModel的数据发生变化时通知页面

## 优点

* 确保界面符合数据状态
* 不会发生内存泄漏
* 不会因为Activity停止而导致内存崩溃
* 不再需要手动处理生命周期
* 数据始终保持最新状态
* 适当的配置更改
* 共享资源

## DataBinding

## 意义

让布局文件承担了部分原本属于页面的工作，使页面与布局耦合度进一步降低

## 优势

* 不再需要findViewById，项目更加简洁，可读性更高
* 布局文件可以包含简单的业务逻辑

# Room

* Entity：实体类，对应的是数据库的一张表结构使用注释@Entity标记
* Dao：包含一系列访问数据库的方法，使用注解@Dao标记
* Database：数据库的持有者，作为与应用持久化相关数据的底层连接的主要接入点。使用注解@Database标记，另外需要满足以下条件：定义的类必须是一个继承于RoomDatabase的抽象类，在注解中需要定义与数据库相关联的实体类列表。包含一个没有参数的抽象方法并返回一个Dao对象

# Navigation

## 优势

* 可视化的页面导航图，类似于Apple Xcode中的StoryBoard，便于我们理清页面关系。
* 通过destination和action完成页面间的导航。
* 方便添加页面切换动画。
* 页面间类型安全的参数传递。
* 通过NavigationUl，对菜单、底部导航、抽屉菜单导航进行统一的管理。
* 支持深层链接DeepLink。

## 主要元素

* Navigation Graph，一种新的XML资源文件，包含应用程序所有的页面，以及页面间的关系。
* NavHostFragment，一个特殊的Fragment，可以将它看作是其他Fragment的容器，Navigation Graph中的Fragment正是通过NavHostFragment进行展示的。
* NavController，用于在代码中完成Navigation Graph中具体的页面切换工作。
*  他们三者之间的关系
  当你想切换Fragment时，使用NavController对象，告诉它你想要去Navigation Graph中的哪个Fragment，NavController会将你想去的Fragment展示NavHostFragment中。
