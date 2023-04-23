---
title: Spring Boot and Protobuf
typora-root-url: Spring Boot and Protobuf
date: 2023-04-23 19:02:48
tags:
---

前两周简单介绍了Flutter

* 基础组件
* `Dart` 编程语言
* 包管理
* 路由

这周在前几周的基础上，讲一下 Flutter 如何与后端对接。

* Serverless ( Functional Computing )
* 比如：小程序云开发、LeanCloud、Google Firebase
* 弊端
  * 数据被服务提供商把控
  * 自建对整个框架的理解会更加深入，更有利于维护

## Spirng Initializr

* Project 项目管理工具：一般来说 `maven` 即可
* Language Java

2 -> 3：`javax` -> `jakarta`；最低支持 `Java 17`

## 简单的例子

```java
// WelcomeController.java

package studio.qingnan.springdemo;

import lombok.Data;
import org.springframework.web.bind.annotation.*;

@RestController
public class WelcomeController {
    @RequestMapping(value = "/")
    public Message index() {
        Message message = new Message();
        message.setId("1");
        message.setSender("qingnan");
        message.setContent("Hello World!");
        return message;
    }

    @PostMapping("/post")
    public Message post(@RequestBody Message message) {
        message.setSender("springboot");
        return message;
    }

    @GetMapping("/detail/{id}")
    public Message detail(@PathVariable String id) {
        Message message = new Message();
        message.setId(id);
        message.setSender("qingnan");
        message.setContent("Hello World!");
        return message;
    }
}

@Data
class Message {
    private String id;
    private String sender;
    private String content;
}
```

三个接口代表了两种请求方式和两种获取参数的方式

```http
GET localhost:8080/
```

```http
POST localhost:8080/post
Content-Type: application/json

{
  "id": "1",
  "title": "Hello World",
  "content": "This is my first post"
}
```

```http
GET localhost:8080/detail/333333
```

## 多层路由

`/api/v2/user/info` 可以通过 `@RequestMapping("welcome")` 来实现。


Flutter 不支持反射式创建对象，只能先得到 `Map<String, dynamic>` 对象，再通过 map 得到内容，涉及到很多强制类型转换；虽然 `json_serializable` 可以生成 Flutter 代码，但已经这么麻烦了，为何不用 Protubuf？


`MessageConverter`

* `String`
* `JSON`
