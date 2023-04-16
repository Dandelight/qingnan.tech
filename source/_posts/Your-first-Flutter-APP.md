---
title: Your first Flutter APP
date: 2023-04-08 14:36:21
tags:
  - Flutter
---

## 优质学习资料

* Flutter 官方文档：<https://flutter.dev/docs>
* *Flutter in Action*, Manning：<https://www.manning.com/books/flutter-in-action>
* Flutter 实战指南：<https://book.flutterchina.club/>

## Flutter 将是下一代全平台开发框架

Google 的下一代操作系统 Fuchsia 将会基于 Flutter 来开发，但为了布局，Flutter 支持了现有的六大平台。

## 在线运行

* <https://dartpad.dev> 在线 Dart 环境
* <https://flutlab.io> 在线 Flutter（免费版只能创建两个项目，来不及安装 Flutter 可以体验下）

## 安装 Flutter

* 官网：<https://flutter.dev>
* 中文社区：<https://flutter.cn>

通过镜像安装：https://mirrors.tuna.tsinghua.edu.cn/help/flutter/

`macOS` 贴到 `~/.zshrc`里；

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

## `pubspec.yaml`

类似 `packages.json`，项目名称、推送到中心仓库、版本管理、依赖管理、项目配置

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

### 基础 `Widget`

`Flutter` 中提供了一些基础组件，比如

#### 界面展示类

* 文本类
  * `Text`：文本
  * `TextSpan`：文本片段
* 按钮类
  * `ElevatedButton`：突出按钮
  * `TextButton`：文本按钮
  * `OutlineButton`：边框按钮
  * 前三种都有 `icon` 属性，可以加一个图标
  * `IconButton`：单图标按钮
* 图片
  * `ImageProvider`: 抽象类，有 `loadBuffer` 等方法，用于加载图片，常用的实现有
    * `AssetImage`：加载**资源**图片（资源是什么以后会讲）
    * `NetworkImage`：加载网络图片
    * `CachedNetworkImage`：由第三方库[cached_network_image](https://pub.dev/packages/cached_network_image)提供，加载网络图片并缓存
  * `Image`：图片组件
    * `image`
    * `width`
    * `color`
    * `colorBlendMode`
    * `fit`
    * `alignment`
    * `repeat`
* Icon
  * Flutter 提供了 `Material Design` 的图标，所有图标可以在其官网查看：<https://material.io/tools/icons/>
  * 可以用 `Icons` 来获取，实际上每个图标对应一个 Unicode 字符，，在 `Text` 组件中输入 `\u` 可以查看。
  * 也可以通过加载自定义字体的方式来使用自定义图标
* 进度指示器
  * `LinearProgressIndicator`：线性进度条
  * `CircularProgressIndicator`：圆形进度条


#### 用户输入类

* 开关与复选框
  * `Switch`
  * `Checkbox`
* 输入框及表单
  * `TextField` 用于简单的文本输入
  * `Form` 用于复杂的表单输入，可以包括多个输入框，支持输入校验。
    * `Form` 的直接 `children` 必须继承 `FormField` 抽象类

#### 容器类

你做一个 APP 总不能只放一列文字图片输入框吧，但不同于 `CSS`，你无法用类似选择器的东西直接给一个 `Widget` 设置 `margin`、`padding`、`border` 等属性，这就需要容器类组件。

容器类组件中，`Container` 是一个 holistic 全能型的组件，可以设置 `margin`、`padding`、`border`、`decoration`、`transform` 等位置偏移，也可以设置 `width`、`height`、`color` 等属性。但它的属性太多了，有时候会让人感到迷惑，让人好奇它怎么实现的。如果去看它的源码，你会发现它的属性实际上是由 `Decoration`、`ConstrainedBox`、`Transform`、`Padding`、`Align`、`FittedBox` 等组件组合而成的。所以，如果只需要设置某个单个属性，可以直接使用这些组件。

```dart
Container(
  constraints: BoxConstraints.expand(
    height: Theme.of(context).textTheme.headlineMedium!.fontSize! * 1.1 + 200.0,
  ),
  padding: const EdgeInsets.all(8.0),
  color: Colors.blue[600],
  alignment: Alignment.center,
  transform: Matrix4.rotationZ(0.1),
  child: Text('Hello World',
    style: Theme.of(context)
        .textTheme
        .headlineMedium!
        .copyWith(color: Colors.white)),
)
```

它的源码是这样的：

```dart
  @override
  Widget build(BuildContext context) {
    Widget? current = child;

    if (child == null && (constraints == null || !constraints!.isTight)) {
      current = LimitedBox(
        maxWidth: 0.0,
        maxHeight: 0.0,
        child: ConstrainedBox(constraints: const BoxConstraints.expand()),
      );
    } else if (alignment != null) {
      current = Align(alignment: alignment!, child: current);
    }

    final EdgeInsetsGeometry? effectivePadding = _paddingIncludingDecoration;
    if (effectivePadding != null) {
      current = Padding(padding: effectivePadding, child: current);
    }

    if (color != null) {
      current = ColoredBox(color: color!, child: current);
    }

    if (clipBehavior != Clip.none) {
      assert(decoration != null);
      current = ClipPath(
        clipper: _DecorationClipper(
          textDirection: Directionality.maybeOf(context),
          decoration: decoration!,
        ),
        clipBehavior: clipBehavior,
        child: current,
      );
    }

    if (decoration != null) {
      current = DecoratedBox(decoration: decoration!, child: current);
    }

    if (foregroundDecoration != null) {
      current = DecoratedBox(
        decoration: foregroundDecoration!,
        position: DecorationPosition.foreground,
        child: current,
      );
    }

    if (constraints != null) {
      current = ConstrainedBox(constraints: constraints!, child: current);
    }

    if (margin != null) {
      current = Padding(padding: margin!, child: current);
    }

    if (transform != null) {
      current = Transform(transform: transform!, alignment: transformAlignment, child: current);
    }

    return current!;
  }
```

可以看见它是把

* `LimitedBox`
* `Align`
* `Padding`
* `ColoredBox`
* `ClipPath`
* `DecoratedBox`
* `ConstrainedBox`
* `Transform`

组合起来的。下面我们介绍单个组件。

* 限制类
  * `LimitedBox`：限制最大宽高的组件
  * `ConstraintsBox`：限制最大最小宽高的组件
  * `SizedBox`：限制宽高的组件
  * `FittedBox`：拉伸子组件到填满自己
* 对齐类
  * `Align`
  * `Center`
* 边界类
  * `Padding`
  * ~~`Margin`~~：`Flutter` 中设置边界的方式只有 `Padding`，`Container` 的 `margin` 属性也是通过 `Padding` 实现的。
* 装饰类
  * `DecoratedBox`
  * `ColoredBox`
* 变换类
  * `Transform`
  * `RotatedBox`
* 裁剪类
  * `ClipOval`: 裁剪为椭圆
  * `ClipRRect`: 裁剪为圆角矩形
  * `ClipRect`: 裁剪为矩形
  * `ClipPath`: 裁剪为自定义路径
  * `CustomClipper`: 自定义裁剪方法
