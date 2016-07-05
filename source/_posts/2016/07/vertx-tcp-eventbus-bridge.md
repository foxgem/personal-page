---
title: Vert.x TCP EventBus Bridge补遗
date: 2016-07-05 20:27:19
tags: 开发
---

如果没有记错的话，Vert.x从3.2就开始支持[TCP Eventbus Bridge](http://vertx.io/docs/vertx-tcp-eventbus-bridge/java/)了，它使得Client可以直接通过socket跟Vert.x EventBus进行通信。可遗憾的是，整个文档就像半成品，并没有把很多事情说清楚。

为了搞清楚这个特性，今天抽空完成了一个TCP Eventbus Bridge的例子，源码见[这里](https://github.com/shifudao/how-to/tree/master/vertx-tcp-eventbridge)。

按理，都已经用TCP了，Client和Server之间干嘛还需要多此一举地采用所谓的Eventbus Bridge？我认为：
- Server和Client之间采用这种方式进行通信可以让Server端的代码更加清晰明了
- Client和Server之间的交互模式也更简单一些：
  - 对于request-response，server简单地message.reply即可
  - 对于某些广播消息，client向多个server实例广播，或者是server向多个client广播，又或某些client也想接收另外的client向server的广播都非常简单和直观。
  - 通过注册地址，client也可以收到感兴趣的消息，不论是server发的，还是client发的

这两点可参考例子源码详细了解。整个例子很简单，实现了：
- client向多个bridge send，则只有一个bridge可以收到
- client向多个bridge publish，则都能收到
- server和client之间的request-response
- client注册要接受某地址的消息

关于API的使用，有以下几点需要注意：
- bridge在server端建立，client只需要使用普通socket去连接即可
- client要接收某地址的消息，仍然是使用socket来接收。因为client并不一定是Vert.x应用，并没有eventbus可用！这一点是引起我误解，同时文档没有讲清楚的地方。
- 对于Java语言，使用io.vertx.ext.eventbus.bridge.tcp.impl.protocol.FrameHelper和io.vertx.ext.eventbus.bridge.tcp.impl.protocol.FrameParser可以简化数据帧的发送和解析。可遗憾的是，没有提供其他语言，如Groovy的对应工具类，弄得我只好采用一种变通的方式去用【还是看代码去了解】。因此，对于Vert.x开发，建议还是首选Java语言来做，可以省掉一些不必要的麻烦。
