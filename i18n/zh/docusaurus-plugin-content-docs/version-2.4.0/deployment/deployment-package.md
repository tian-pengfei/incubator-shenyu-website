---
sidebar_position: 2
title: 二进制包部署
keywords: ["二进制", "部署"]
description: 二进制包部署
---

本文介绍使用二进制包部署 `Apache ShenYu` 网关。


### 启动 Apache ShenYu Admin

* 下载 [apache-shenyu-incubating-2.4.0-admin-bin.tar.gz](https://archive.apache.org/dist/incubator/shenyu/2.4.0/apache-shenyu-incubating-2.4.0-admin-bin.tar.gz)

* 解压缩 `apache-shenyu-incubating-2.4.0-admin-bin.tar.gz`。 进入 `bin` 目录。

* 使用 `h2` 来存储后台数据：

```
> windows: start.bat --spring.profiles.active = h2

> linux: ./start.sh --spring.profiles.active = h2
```

* 使用 `MySQL` 来存储后台数据，将 [mysql-connector.jar](https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.18/mysql-connector-java-8.0.18.jar) 拷贝到 `/${your_work_dir}/ext-lib`， 进入 `/conf` 目录，修改 `application.yaml` 中 `mysql` 的配置。

```
> windows: start.bat 

> linux: ./start.sh 
```

### 启动 Apache ShenYu Bootstrap

* 下载 [apache-shenyu-incubating-2.4.0-bootstrap-bin.tar.gz](https://archive.apache.org/dist/incubator/shenyu/2.4.0/apache-shenyu-incubating-2.4.0-bootstrap-bin.tar.gz)

* 解压缩 `apache-shenyu-incubating-2.4.0-bootstrap-bin.tar.gz`。 进入 bin 目录。

```
> windwos : start.bat 

> linux : ./start.sh 
```









