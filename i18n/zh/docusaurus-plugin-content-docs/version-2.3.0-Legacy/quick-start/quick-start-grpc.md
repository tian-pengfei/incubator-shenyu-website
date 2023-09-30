---
title: Grpc快速开始
description: Grpc快速开始
---

本文档将演示了如何快速使用Grpc接入Soul网关。您可以直接在工程下找到本文档的[示例代码](https://github.com/dromara/soul/tree/2.3.0/soul-examples/soul-examples-grpc)。

## 环境准备

请参考[配置网关环境](../users-guide/soul-set-up)并启动`soul-admin`和`soul-bootstrap`。

注：`soul-bootstrap`需要引入grpc依赖

```xml
<dependency>
    <groupId>org.dromara</groupId>
    <artifactId>soul-spring-boot-starter-plugin-grpc</artifactId>
    <version>${project.version}</version>
</dependency>
```

## 运行soul-examples-grpc项目

下载[soul-examples-grpc](https://github.com/dromara/soul/tree/2.3.0/soul-examples/soul-examples-grpc)

在`soul-examples-grpc`下执行以下命令生成java代码

```shell
mvn protobuf:compile //编译消息对象
mvn protobuf:compile-custom //依赖消息对象,生成接口服务
```

运行`org.dromara.soul.examples.grpc.SoulTestGrpcApplication`main方法启动项目。

成功启动会有如下日志：

```shell
2021-02-10 01:57:02.154  INFO 76 --- [           main] o.d.s.e.grpc.SoulTestGrpcApplication     : Started SoulTestGrpcApplication in 2.088 seconds (JVM running for 3.232)
2021-02-10 01:57:02.380  INFO 76 --- [pool-1-thread-1] o.d.s.client.common.utils.RegisterUtils  : grpc client register success: {"appName":"127.0.0.1:8080","contextPath":"/grpc","path":"/grpc/echo","pathDesc":"","rpcType":"grpc","serviceName":"echo.EchoService","methodName":"echo","ruleName":"/grpc/echo","parameterTypes":"echo.EchoRequest,io.grpc.stub.StreamObserver","rpcExt":"{\"timeout\":-1}","enabled":true} 
```

## Grpc 插件设置

* 在 `soul-admin` 插件管理中，把`grpc` 插件设置为开启。

## 测试

`soul-examples-grpc`项目成功启动之后会自动把加 `@SoulGrpcClient` 注解的接口方法注册到网关。

打开插件管理->grpc可以看到插件规则配置列表

![](/img/soul/quick-start/grpc/rule-list.png)

下面使用postman模拟http的方式来请求你的grpc服务

![](/img/soul/quick-start/grpc/postman-test.png)

