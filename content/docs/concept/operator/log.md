---
title: "log操作符"
linkTitle: "log操作符"
weight: 364
date: 2021-01-23
description: >
  log 操作符记录事件
---

log 操作符将流相关的事件记录在日志中。

下面的代码添加了 log 操作符并指定了日志分类的名称：

```java
Flux.range(1, 2).log("Range").subscribe(System.out::println);
```

在实际的运行时，所产生的输出如下所示：

```java
13:07:56.735 [main] DEBUG reactor.util.Loggers$LoggerFactory - Using Slf4j logging framework
13:07:56.751 [main] INFO Range - | onSubscribe([Synchronous Fuseable] FluxRange.RangeSubscription)
13:07:56.753 [main] INFO Range - | request(unbounded)
13:07:56.754 [main] INFO Range - | onNext(1)
1
13:07:56.754 [main] INFO Range - | onNext(2)
2
13:07:56.754 [main] INFO Range - | onComplete()
```

