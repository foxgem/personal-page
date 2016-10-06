---
title: Vert.x Circuit Breaker须知
date: 2016-07-11 17:30:03
tags: 微服务
---

Vert.x 3.3新增的[Circuit Breaker](http://vertx.io/docs/vertx-circuit-breaker/java/)深得我心，使用简单，而且文档齐全。今天照着文档写了[一个探索性的例子](https://github.com/shifudao/how-to/tree/master/circuitbreaker)，为接下来的项目做技术性预研。

整个过程非常顺利，但有几点有必要说明一下：

- future.complete()必须被调用，无论有无返回值，否则这次执行不会被认为是结束，进而导致超时。
- 为了让CircuitBreaker检查到超时，在CircuitBreaker.execute()外部套了一层vertx.executeBlocking()，否则即便CircuitBreaker.execute()内的操作的执行时间超过了外部设置的时间长度，CircuitBreaker也不会检查到。

总得来说，还是不错。只不过需要注意该版本还只是技术预览版，不排除以后有接口变动的可能。
