---
title: 一种可伸缩的微服务架构：DRCON
date: 2016-05-31 16:53:55
tags: 微服务
---

微服务时下正火，Docker是当红炸子鸡，稍微思考一下就能发现：两者结合为可伸缩的架构提供天然的基础，但怎么实现，却没有太多的头绪。直到发现[这篇旧文](https://www.airpair.com/scalable-architecture-with-docker-consul-and-nginx)才让我豁然开朗。【各位见谅，虽然名词很早就接触了，真正打算着手开干才是最近的事情。】

DRCON其实是下列工具的集合：

- Docker，不必过多介绍，略过
- Registrator，可简化服务的注册
- Consul，服务注册和发现
- Consul Template + Nginx，服务的负载均衡和重定向

服务的负载均衡和重定向也可以用SRV-Router来做，这一做法作者在[另一篇更老的文章](http://www.maori.geek.nz/docker_web_services_with_consul/)里有介绍。相比起来，这篇文章的做法要更简单一些，就是利用Consul Template在服务启停时自动去修改Nginx的配置文件。

若采用SRV-Router，务必注意文中提到的小细节：

> The srv-router when called will query Consul for home.simple.service.consul, then route to the address and port that is returned. This is the tags namespace in Consul, so each consul service must have the home tag.

我就是没有注意在Consul中要有个home tag，浪费了半天时间。

最后提一句，与文中用python来实现服务的例子不同，我用的是[Vert.x Web](http://vertx.io/docs/#web)，;)。
