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
  * Qt Mobile: C++，落寞了
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
* 用户统计（友盟）
* 消息推送（极光）
* 即时通讯
* 崩溃分析（Bugly）

## 项目管理

树状结构+Code Review，由 CTO 把握整体技术方向与技术选型，各开发方向设技术负责人，技术负责人负责完成需求。

一些重要的概念

* milestone
* timeline
* version

## 本软件的 milestone

> 按照校历，国际周在 6 月 26 日开始，暑假也在这个时候。这个时间点到 9 月 1 日的暑假内，应该将绝大部分任务完成。

* 四月：经验分享系列活动
* 五月：经验分享中积极参与者加入项目组，熟悉代码和框架
* 六月：完成 A 类任务中的数据格式设计，完成界面编码
* 七月：完成大部分 A 类任务，尤其是完成即时通讯的对接。开始第二轮内测。
* 八月：完成所有 A 类任务及大部分 B 类任务，同时添加足够的测试用例，完成 D 类任务；持续接收内测反馈，及时修复。
* 九月：上架（此处可以有团建），完成所有 B 类任务，研发 C 类任务。运维。评估工作量。
* 十月：整理开发资料，成果可转化为大创、竞赛、专利等。
* 十一月：探索：自主实现实时消息系统；服务扩容。

## 上架

* Google Play
* App Store
* 国内应用市场
  * 必须是有 ICP 许可证的公司
  * 持有软件著作权

## 运营

* 内容审查
* 客户服务
