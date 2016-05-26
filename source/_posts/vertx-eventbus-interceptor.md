---
title: Vert.x技巧：使用EventBus Interceptor拦截消息
date: 2016-05-26 18:58:38
tags: 开发
---

[Vert.x](http://vertx.io/)用久了肯定有这样的想法：拦截EventBus上发送的所有消息。这个需求用Vertx EventBus Interceptor可以非常简单的实现，可惜的是，[Vert.x文档](http://vertx.io/docs/)却并没有明确的指出来。

其实它的使用很简单，直接看代码吧（Groovy代码）：

~~~
vertx.eventBus().addInterceptor { sendContext ->
    Message message = sendContext.message()
    // 自由发挥……

    sendContext.next()
}
~~~

最后的那句 **sendContext.next()** 非常关键：如果没写，后续的consumer将无法收到刚刚被你拦截的消息！所以，一定要确保你是**有意**不写的。

其他的就没什么可说得了，基本跟其他工具提供的拦截器的功能类似，查查API文档，看看代码，都能搞清楚。
