---
title: 采用Seek Method加速分页
date: 2016-06-13 19:41:15
tags:
- 开发
- 数据库
---

这是今天在[码天狗周刊上看到的文章](http://use-the-index-luke.com/no-offset)，加上之前曾有过切身体会（只不过不是在SQL上），故觉得有必要摘记下来广而告之。

凡事做过页面的，一般对分页不会陌生，也不会觉得它有多难：就是limit + offset的组合就可以了呀。但是，危险往往都是从最不起眼的地方开始的。在这里，我先说一下我之前在用MongoDB时遇到的问题。这类问题同样会出现在这种分页方式上。

当时，我需要对于MongoDB中的数据进行处理，每次处理一批，也相当于是按页来操作数据啦。这个没啥难度，直接使用API中的find + skip + limit就可以轻易搞定。迅速把程序写完之后就开始拿产品库开搞了。刚开始一切正常，可过了没多久，就发现整个程序的性能下降了。进入Mongo一查，发现是Table Scan。哇，那个collection中有上千万的数据啊！

此处略去3000字。

总之，问题最后解决了，程序又运行如飞。而解决之道很简单：只用find + limit，不再使用skip（原因自己想）。只不过在find中加了一个条件：上一批的最后一个document的_id。整个代码形似（groovy代码）：

~~~

if (docId) {
    batch = collection.find(['_id': ['$gt': docId]] as Document).limit(BATCH_SIZE)
} else {
    batch = collection.find().limit(BATCH_SIZE)
}
docId = batch[-1]['_id']

~~~

它的原理很简单，其实就是利用可以利用的index来加速分页。这种思想跟今天看到的文章的思路如出一辙，不再使用offset，寻找能达到同样效果的index，用它来助力搜索。因此，文中给出的方案跟上面的代码类似：

~~~

SELECT ...
  FROM ...
 WHERE ...
   AND id < ?last_seen_id
 ORDER BY id DESC
 FETCH FIRST 10 ROWS ONLY

~~~

这种分页方式被称为“seek method”，其中的id被称为“seek predicate”。典型的seek predicate还可以是日期。需要提醒的是，seek predicate上需要有index才有意义，而且它可以有多列！采用这种方式的分页可以避免上述分页的潜在危险：当页数达到一定量之后，分页速度会严重下降。

关于seek method，还可以参考下面的文章：

- https://blog.jooq.org/2013/10/26/faster-sql-paging-with-jooq-using-the-seek-method/
- http://use-the-index-luke.com/sql/partial-results/fetch-next-page
