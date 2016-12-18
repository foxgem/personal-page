---
title: GraphQL简说
date: 2016-12-18 17:03:47
tags: 开发
---

之前看到Facebook开源GraphQL的新闻时还以为它是为图数据库提供的查询语言，但[这篇文章](https://medium.com/chute-engineering/graphql-in-the-age-of-rest-apis-b10f2bf09bba#.1nzvweus8)及时纠正了我的错误认识。

简单的说：GraphQL是一种API，它的出现是为了改进使用REST时面临的缺陷。

> GraphQL’s power comes from a simple idea — instead of defining the structure of responses on the server, the flexibility is given to the client. Each request specifies what fields and relationships it wants to get back, and GraphQL will construct a response tailored for this particular request. The benefit: only one round-trip is needed to fetch all the complex data that might otherwise span multiple REST endpoints, and at the same time only return the data that are actually needed and nothing more.

文中提到了另一个REST不具备的优势：

> Another advantage that I see in GraphQL is that it has a built-in type introspection. That means you can describe the entire API programmatically, and we can build tools that drastically improve development. 

由此看来，GraphQL是作为REST的一个替代品出现的，那么这是否意味着REST的好日子到头了呢？作者并非这么想：
- 业界在REST上已投入不少资源
- GraphQL目前只有Facebook一家在产品环境下使用 【注：文章的写作时间是是去年7月份】
- 转变需要至少10年时间

因此，最有可能的结果是：两者并存。

文后，作者给出了若干GraphQL的例子，读者可自行查阅。除此之外，有兴趣的读者还可以看看[这篇介绍PostGraphQL的短文](https://compose.com/articles/postgraphql-postgresql-meets-graphql)，通过它，你可以用GraphQL来查询后端的PostgreSQL数据库。