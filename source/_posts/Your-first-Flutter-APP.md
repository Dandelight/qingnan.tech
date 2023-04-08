---
title: Your first Flutter APP
date: 2023-04-08 14:36:21
tags:
  - Flutter
---

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
