---
title: More about Flutter
date: 2023-04-13 14:43:51
description: Flutter 的生命周期、高级布局、控制组件状态、高级状态管理、网络请求等内容。
tags:
typora-root-url: More-about-Flutter
---

> 首先说明，该教程会教给大家很多先进技术，但并不是为了教会大家某种单项技能，因为只会单项技能只能做打工人。我们的目的是在创业实践中锻炼大家的管理能力、项目能力，以期为社会创造价值。

## Design Philosophy

### 解耦原本混乱不堪的 CSS

CSS 是 Web 开发的标准语言，因语法简洁、功能强大也被设计界所接纳。但是新标准不断提出，而 CSS 依然保持着以往的平铺直叙的语法（现在 CSS 标准有五百多条，算上非官方标准有一千余条），工程变得越来越难以维护。

很大一个影响因素是，CSS 中很多属性是相互依赖的，比如 `position`、`float`、`display`、`overflow`、`z-index` 等等，这些属性的值是相互影响的，这种例子不胜枚举，比如

* `display` 的值为 `inline` 时，`width`、`height`、`margin`、`padding` 的值就没有意义了
* 对于文本，`overflow` 的值为 `hidden` 时，`width`、`height` 的值才有意义
* `position` 非 `static` 时，`z-index`，`top`、`left`、`right`、`bottom` 的值才有意义，否则被忽略也不报错。
* `float` 和 `margin` 一起使用时，谁用谁知道。

这样的代码不分层级散落在大括号里，很难维护，也很难调试。即使有原子 CSS 库，也不能从本质上解决问题。

在 Flutter 的 Material 库中，我们可以看到 `Container`、`Padding`、`SizedBox` 等组件，它们的功能是相互独立的，不会相互影响，代码容易编写、容易维护、容易复用、容易重构。

### 组合大于继承

在 `Flutter` `Widget` 是页面布局的基本组件，它可以被组合、被继承，也可以被重用。`Widget` 之间的关系是一种组合关系，而不是继承关系。但如果继承关系是必须的，那么 `Flutter` 也提供了 `InheritedWidget`，它可以让 `Widget` 之间建立继承关系。但这里的继承只是复用逻辑，而不是为了布局。

## Widget 生命周期

![Flutter-Lifecycle](Flutter-Lifecycle.png)

> *Flutter In Action*, Manning.

## 高级布局

### 更多布局组件

* `Container`
* `Padding`
* `SizedBox`

### 列表组件

* `CustomScrollView` 和 `Sliver`

## 控制组件状态

* `Controller`

## 高级状态管理

* `Provider`

## 连接前端与后端

广义上的跨进程通信

单机跨进程通信方案：

* 管道
* 消息队列
* 共享内存
* Semaphore
* 网络

> 参考：<https://xiaolincoding.com/os/4_process/process_commu.html>

跨主机跨进程通信：网络


### 网络请求

+ `pub.dev`
+ `pubspec.yaml` 导入 `http` 包
+ `HTTP` 基础（`curl -v` & `WireShark` 抓包实践）

* `Protobuf`

## 异步：承诺（Promise）与未来（Future）


## MISC

* `Dart` 的一些内置数据结构
  + `Map`
  + `Set`
  + `List`

## 项目：个人字典

* 输入框
* 网络请求
* 单词列表

## 向何方而去

* `GitHub` 优质项目
