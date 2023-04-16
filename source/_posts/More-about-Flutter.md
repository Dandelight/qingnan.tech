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

在 Flutter 的 Material 库中，我们可以看到 `ConstrainedBox`、`Padding`、`SizedBox` 等组件，它们的功能是相互独立的，不会相互影响，代码容易编写、容易维护、容易复用、容易重构。

### 组合大于继承

在 `Flutter` `Widget` 是页面布局的基本组件，它可以被组合、被继承，也可以被重用。`Widget` 之间的关系是一种组合关系，而不是继承关系。但如果继承关系是必须的，那么 `Flutter` 也提供了 `InheritedWidget`，它可以让 `Widget` 之间建立继承关系。但这里的继承只是复用逻辑，而不是为了布局。

## Widget 生命周期

![Flutter-Lifecycle](Flutter-Lifecycle.png)

> *Flutter In Action*, Manning.

## 多 `children` 布局组件

* Flex 布局
  * `Row`
  * `Column`
  * `Flex`
* 流式布局
  * `Wrap`
  * `Flow`
* 层叠布局
  * `Stack`
    * `Positioned`

## Flutter 布局过程

如果学过编译原理，对编译器如何遍历抽象语法树（Abstract Syntax Tree, AST）应该不陌生。`Flutter` 的布局过程也是类似的，不过它会生成三棵树：
1. `Widget` 树
2. `Element` 树
3. `RenderObject` 树

我们先不去讲复杂的原理，但对于编程，以下辅助组件是重要的：

* `LayoutBuilder`：拿到父组件传递的约束

## 列表组件

相信很多软件不会是单个页面，比如新闻列表，Todo List 需要滚动，这时候需要用到列表组件。

### 基础列表

* `ListView`
* `GridView`
* `TabbarView`
* `PageView`

### `CustomScrollView` 和 `Sliver`

### 功能型组件

* `ValueListenableBuilder`
* `FutureBuilder`
* `StreamBuilder`

### 事件处理

* `GestureDetector`

## 控制组件状态

控制自己的状态比较简单，但是控制子组件的状态就比较复杂了，比如 `TextField` 的内容等。

在 `Flutter` 中，子组件控制父组件状态，是通过回调实现的。比如，给子组件传进一个包含 `setState` 的回调函数，子组件在合适的时机调用这个回调函数，父组件就会更新状态。

`Controller` 是 `Flutter` 中的一个重要概念，它可以让父组件控制子组件的状态，比如 `TextEditingController` 可以控制 `TextField` 的内容。

## 路由

你的 APP 一定不会只有一个页面，这时候就需要用到路由了。可以把路由理解为一个页面栈，当你打开一个新页面时，就会把新页面压入栈顶，当你关闭一个页面时，就会把栈顶的页面弹出。

管理路由的类是 `Navigator`，它提供了一些方法，比如 `push`、`pop`、`pushNamed`、`popUntil` 等等。

## 主题

`Flutter` 中的主题是通过 `ThemeData` 来管理的，它是一个 `Map`，`Map` 的键是 `Material` 组件的 `Type`，值是一个 `Map`，这个 `Map` 的键是 `Material` 组件的属性，值是属性的值。

## `MediaQuery`

`MediaQuery` 是 `Flutter` 中一个重要的组件，它可以让我们获取设备的一些信息，比如屏幕的宽高、设备的像素密度、系统的语言等等。

## 导航栏

导航栏是 APP 中最常见的组件，它可以让用户在不同的页面之间切换。

对 `Flutter` 本身的介绍暂时就到这里，但 `Flutter` 能提供的远不止于此，它还提供了

* 动画
* 文件/网络 IO
* 自绘组件
* 原生插件扩展

等高级功能，能让你的 APP 更加丰富。

* `Key`：一般情况下不需要考虑，但如果有**大量同类 `Widget` 的排序、删除、插入**的需求时，就需要考虑 `Key` 了。

可以去 GitHub 上搜索 `flutter`，你会发现有很多开源的 `Flutter` 组件，比如 `fluttertoast`、`flutter_swiper`、`flutter_staggered_grid_view` 等。

## 包管理

* `pub.dev`
* `pubspec.yaml`
* 使用包（以 `fluttertoast` 为例）
* 包冲突与解决

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

`JavaScript` 中的 `Promise` 是一种异步编程的解决方案，它可以让我们在异步操作完成后，以同步的方式处理结果。但考虑到我们要建立“学 Dart 不需要先会 JS”的概念，我们直接讲 `Future`。

## MISC

* `Dart` 的一些内置数据结构
  + `Map`
  + `Set`
  + `List`

## 项目：个人字典

* 输入框
* 网络请求
* 单词列表

`pub.dev` 包管理
`Navigator` 路由管理

项目：做一个简单的翻译软件（调用彩云 API）
