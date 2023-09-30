---
title: Register Center Instance Config
keywords: ["register center"]
description: Register Instance
---

This document will introduce how to register the gateway instance to the registry. The `Apache ShenYu` gateway currently supports registration to `zookeeper` and `etcd`.

### Add Maven dependency

First, introduce the following dependencies in the gateway's `pom.xml` file.

```xml
<!--shenyu instance start-->
<dependency>
    <groupId>org.apache.shenyu</groupId>
    <artifactId>shenyu-spring-boot-starter-instance</artifactId>
    <version>${project.version}</version>
</dependency>
<!--shenyu instance end-->
```

### Use zookeeper

Add the following configuration to the gateway's `yml` file:

```yaml
instance:
    enabled: true
    registerType: zookeeper
    serverLists: localhost:2181 #config with your zk address, used by the cluster environment, separated with (,).
    props:
      sessionTimeout: 3000 #Optional, default 3000
      connectionTimeout: 3000 #Optional, default 3000
```
 
### Use etcd

Add the following configuration to the gateway's `yml` file:

```yaml
instance:
    enabled: true
    registerType: etcd
    serverLists: http://localhost:2379 #config with your etcd address, used by the cluster environment, separated with (,).
    props:
      etcdTimeout: 3000 #Optional, default 3000
      etcdTTL: 5 #Optional, default 5
```

> After the configuration is complete, start the gateway and it will successfully register to the corresponding registration center.
