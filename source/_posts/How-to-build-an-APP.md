---
title: 如何制作一款 APP
date: 2023-04-08 14:12:40
tags:
---

组成部分：

* 客户端
* 服务端
* 数据库

## 客户端

* Web
* 桌面
  * Windows
  * macOS
  * Linux
* 手机
  * Android
  * iOS

跨平台解决方案：

* 编译型
  * Flutter: 谷歌出品，性能高，开发快，跨平台，各平台渲染效果一致，国内以闲鱼为代表，很多厂商的 APP 里混编了 Flutter
  * React Native: Facebook 出品，采用**类似**于 Web 的技术栈，编译到原生代码性能有保证，但没出过正式版，API 变化较大，适配 Android/iOS 新版本慢
  * Weex: 阿里出品，类似于 RN
  * Taro: 京东、58同城出品，编译到 RN
  * Xamarin: 微软出品，C#，落寞了
* `WebView` + `JSBridge` 型
  * Ionic: 多种 Web 框架，但国内用得不多
  * NativeScript: 国内用得不多
  * uni-app: 国内数字天堂出品，上手快，但推出五年还是有很多 bug，只建议用来做小程序

## 服务端

### 服务器软件

| 语言 | 框架 |
| --- | --- |
| Node.js | Express |
| Java | SpringBoot |
| Python | Django |
| Go | Gin |
| Ruby | Ruby on Rails |
| C# | ASP.NET |

### 数据库

MongoDB、MySQL、Redis、ElasticSearch

## 第三方服务

* 对象存储
* 用户统计
* 消息推送
* 即时通讯
* 崩溃分析

## 上架

* Google Play
* App Store
* 国内应用市场
  * 必须是有 ICP 许可证的公司
  * 持有软件著作权

## 运营

* 内容审查
* 客户服务
