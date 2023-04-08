---
title: Your first Flutter APP
date: 2023-04-08 14:36:21
tags:
  - Flutter
---

## Flutter 将是下一代全平台开发框架

Google 的下一代操作系统 Fuchsia 将会基于 Flutter 来开发，但为了布局，Flutter 支持了现有的六大平台。

## 在线运行

* <https://dartpad.dev> 在线 Dart 环境
* <https://flutlab.io> 在线 Flutter（免费版只能创建两个项目，来不及安装 Flutter 可以体验下）

## 安装 Flutter

* 官网：<https://flutter.dev>
* 中文社区：<https://flutter.cn>

通过镜像安装：https://mirrors.tuna.tsinghua.edu.cn/help/flutter/

```shell
export FLUTTER_STORAGE_BASE_URL="https://mirrors.tuna.tsinghua.edu.cn/flutter"
export PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub"
export FLUTTER_GIT_URL="https://mirrors.tuna.tsinghua.edu.cn/git/flutter-sdk.git"
```

```shell
git clone https://mirrors.tuna.tsinghua.edu.cn/git/flutter-sdk.git -b stable
```

然后去设置 `PATH` 环境变量。

```shell
flutter doctor
```

按照提示配置 Web 等环境。我们推荐的是，在 Windows 上配置 Android 环境，在 macOS 上配置 macOS 环境（因为 iOS 环境很难配置，需要开发者账号）

## 创建第一个 Flutter APP

```shell
flutter create $应用名 --org $组织名
```

## 在 IDE 中安装 Flutter 插件

> 有一说一，Flutter 插件是我用过的最好用的插件

## 运行 APP

```shell
flutter run
```

## `DevTools`

```shell
dart devtools
# 另一个终端里
flutter run
```


## 打包 APP

```shell
flutter build apk --release
```

## Flutter Basics

### `Widget`

Widget 是 Flutter 中的基本元素，开发者接触到的主要有 `StatelessWidget` 和 `StatefulWidget`，另外还有 `ProxyWidget`，`RenderObjectWidget`，`InheritedWidget` 等。

* `StatelessWidget` 是不可变的，本身没有状态，一经构建不会改变，除非丢掉重新构建（顺带提一句，Dart 是 GC 语言）
* `StatefulWidget` 是可变的吗？不是，它的状态是可变的，但是本身是不可变的，它的状态是由 `State` 来管理的。
  * 官方文档说，这么设计是为了方便继承 `StatefulWidget`，否则，`StatefulWidget` 可能要接收一个 `State` 类型的参数，多层继承会变得很复杂。

Flutter 的设计中，处处体现着“组合优于继承”的思想，能用组合就用组合。

示例 `Widget`

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}
```

### Material Design

Material Design 是 Google 推出的一套设计标准。大多数 Flutter APP 都是基于 Material Design 来设计的。当然，Flutter 也支持 `Cupertino`、`Foundation` 等设计标准。
使用 `Flutter` 时并不需要过分关注 `Material Design`，知道 `import 'package:flutter/material.dart';` ，会使用 `Material Icon` 即可。

首先来看下 `MaterialApp` 的文档。

### `Scaffold`

### `Material` 库中的 `Widget`

`pub.dev` 包管理
`Navigator` 路由管理

项目：做一个简单的翻译软件（调用彩云 API）

## 深入理解

* `Key`：一般情况下不需要考虑，但如果有**大量同类 `Widget` 的排序、删除、插入**的需求时，就需要考虑 `Key` 了。
