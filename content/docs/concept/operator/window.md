---
title: "window操作符"
linkTitle: "window操作符"
weight: 354
date: 2021-01-22
description: >
  window 操作符把流中的元素收集到另外的 Flux 序列中
---

window 操作符的作用类似于 buffer，所不同的是 window 操作符是把当前流中的元素收集到另外的 Flux 序列中，因此返回值类型是 `Flux<flux>`。

下面的示例代码，输出结果 5 个字符。这是因为 window 操作符所产生的流中包含的是 UnicastProcessor 类的对象，

```java
Flux.range(1, 100).window(20).subscribe(System.out::println);
```

而下面的代码的输出结果则是 2 个 UnicastProcessor 字符：

```java
Flux.intervalMillis(100).windowMillis(1001).take(2).toStream().forEach(System.out::println);
```

