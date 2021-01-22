---
title: "buffer操作符"
linkTitle: "buffer操作符"
weight: 352
date: 2021-01-22
description: >
  buffer 操作符缓冲流中的元素
---


### buffer

buffer 操作符的作用是把当前流中的元素收集到集合中，并把集合对象作为流中的新元素。

在进行收集时可以指定不同的条件：所包含的元素的**最大数量**或收集的**时间间隔**。

方法 buffer()仅使用一个条件，而 bufferTimeout()可以同时指定两个条件。

```java
// 输出的是 5 个包含 20 个元素的数组
Flux.range(1, 100).buffer(20).subscribe(System.out::println);
```

### bufferTimeout

指定时间间隔时可以使用 Duration 对象或毫秒数，即使用 bufferMillis()或 bufferTimeoutMillis()两个方法。

```java
// 输出的是 2 个包含了 10 个元素的数组
Flux.intervalMillis(100).bufferMillis(1001).take(2).toStream().forEach(System.out::println);
```

需要注意的是，这里的代码首先通过 toStream()方法把 Flux 序列转换成 Java 8 中的 Stream 对象，再通过 forEach()方法来进行输出。这是因为序列的生成是异步的，而转换成 Stream 对象可以保证主线程在序列生成完成之前不会退出，从而可以正确地输出序列中的所有元素。

### bufferUntil 和 bufferWhile

除了元素数量和时间间隔之外，还可以通过 bufferUntil 和 bufferWhile 操作符来进行收集。

这两个操作符的参数是表示每个集合中的元素所要满足的条件的 Predicate 对象：

- bufferUntil 会一直收集直到 Predicate 返回为 true。使得 Predicate 返回 true 的那个元素可以选择添加到当前集合或下一个集合中；

   ```java
   // 输出的是 5 个包含 2 个元素的数组
   // 每当遇到一个偶数就会结束当前的收集
	Flux.range(1, 10).bufferUntil(i -> i % 2 == 0).subscribe(System.out::println);
   ```

- bufferWhile 则只有当 Predicate 返回 true 时才会收集。一旦值为 false，会立即开始下一次收集。

   ```java
   // 第四行语句输出的是 5 个包含 1 个元素的数组
   // 数组里面包含的只有偶数。
	Flux.range(1, 10).bufferWhile(i -> i % 2 == 0).subscribe(System.out::println);
   ```





