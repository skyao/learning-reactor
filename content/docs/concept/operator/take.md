---
title: "take操作符"
linkTitle: "take操作符"
weight: 357
date: 2021-01-22
description: >
  take 操作符从流中提取元素
---

take 系列操作符用来从当前流中提取元素。

提取的方式有

- take(long n)，take(Duration timespan)和 takeMillis(long timespan)：按照指定的数量或时间间隔来提取。

   ```java
   // 输出的是数字 1 到 10
   Flux.range(1, 1000).take(10).subscribe(System.out::println);
   ```

- takeLast(long n)：提取流中的最后 N 个元素。

   ```java
   // 输出的是数字 991 到 1000
   Flux.range(1, 1000).takeLast(10).subscribe(System.out::println);
   ```

- takeUntil(Predicate<? super T> predicate)：提取元素直到 Predicate 返回 true。

   ```java
   // 输出的是数字 1 到 10
   // 使得 Predicate 返回 true 的元素也是包含在内的。
   Flux.range(1, 1000).takeUntil(i -> i == 10).subscribe(System.out::println);
   ```

- takeWhile(Predicate<? super T> continuePredicate)： 当 Predicate 返回 true 时才进行提取。

   ```java
   // 输出的是数字 1 到 9
   Flux.range(1, 1000).takeWhile(i -> i < 10).subscribe(System.out::println);
   ```

- takeUntilOther(Publisher<?> other)：提取元素直到另外一个流开始产生元素。






