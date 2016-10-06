---
title: 用NetflixOSS和Spring Cloud构建微服务
date: 2016-10-04 19:57:48
tags: 微服务
---

微服务虽好，但其中的坑可不少。所幸，借助开源软件，可以大大降低实现的风险。

对于Java开发团队来讲，实现微服务怎么也不可能无视NetflixOSS，它提供了从服务发现到部署的一整套解决方案，堪称业界良心：
- Eureka，服务注册表，并充当负载均衡中间件
- Archaius，配置管理
- Ribbon，客户端服务发现，在客户端实现负载均衡。可与Eureka配合使用。
- Hystrix，断路器
- Zuul，Api Gateway
- Atlas，系统健康
- Spinnaker，持续交付

长期以来，Spring一直以改善Java开发者的生活为己任，在当下这个微服务横行的时代，自然不会袖手旁观。Spring Cloud系列就是在这个背景下产生的：
- Spring Cloud Netflix，含Eureka、Archaius、Ribbon、Hystrix、Zuul
- Spring Cloud Config，基于Git的配置服务器
- Spring Cloud Consul，基于Consul的服务发现
- Spring Cloud Security，实现服务间OAuth2流程
- Spring Cloud Sleuth，与Zipkin集成
- Spring Cloud Stream，基于消息（ZeroMQ和Kafka）的解决方案
- Spring Cloud Dataflow，数据处理pipeline
- Spring Cloud Task，短期存活的单任务服务
- Spring Cloud Zookeeper，与Zookeeper集成
- Spring Cloud for AWS，与AWS集成
- Spring Cloud Spinnaker，与Spinnaker集成
- Spring Cloud Contract，服务契约

以上每个工具都有很详尽的文档，在此就不再赘述。本笔记的目的主要是给出涉及微服务开发不同方面的一个完整工具列表，这在其他地方甚少看到。

注：以上内容来自[Pivotal的这个链接](https://pivotal.io/supercharging-your-microservices-with-netflixoss-and-spring-cloud)。
