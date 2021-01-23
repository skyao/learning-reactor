---
title: "retry操作符"
linkTitle: "retry操作符"
weight: 363
date: 2021-01-23
description: >
  retry 操作符进行重试
---

当出现错误时，可以通过 retry 操作符来进行重试。

重试的动作是通过重新订阅序列来实现的。在使用 retry 操作符时可以指定重试的次数。

下面的代码指定了重试次数为 1，所输出的结果是 1，2，1，2 和错误信息。

```java
Flux.just(1, 2)
        .concatWith(Mono.error(new IllegalStateException()))
        .retry(1)
        .subscribe(System.out::println);
```


