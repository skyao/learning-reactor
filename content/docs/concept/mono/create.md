---
title: "创建Mono"
linkTitle: "创建Mono"
weight: 332
date: 2021-01-22
description: >
  创建Mono
---



### 静态方法

Mono 的创建方式与 Flux 比较相似。Mono 类中也包含了一些与 Flux 类中相同的静态方法。这些方法包括 just()，empty()，error()和 never()等。

除了这些方法之外，Mono 还有一些独有的静态方法：

- fromCallable()、fromCompletionStage()、fromFuture()、fromRunnable()和 fromSupplier()：分别从 Callable、CompletionStage、CompletableFuture、Runnable 和 Supplier 中创建 Mono。

- delay(Duration duration)和 delayMillis(long duration)：创建一个 Mono 序列，在指定的延迟时间之后，产生数字 0 作为唯一值。

- ignoreElements(Publisher source)：创建一个 Mono 序列，忽略作为源的 Publisher 中的所有元素，只产生结束消息。

- justOrEmpty(Optional<? extends T> data)和 justOrEmpty(T data)：从一个 Optional 对象或可能为 null 的对象中创建 Mono。只有 Optional 对象中包含值或对象不为 null 时，Mono 序列才产生对应的元素。

代码示例：

```java
Mono.fromSupplier(() -> "Hello").subscribe(System.out::println);
Mono.justOrEmpty(Optional.of("Hello")).subscribe(System.out::println);
```

###  create()

可以通过 create()方法来使用 MonoSink 来创建 Mono:

```java
Mono.create(sink -> sink.success("Hello")).subscribe(System.out::println);
```



