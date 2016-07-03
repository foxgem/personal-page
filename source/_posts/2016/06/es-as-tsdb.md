---
title: 作为TSDB的Elasticsearch
date: 2016-06-30 16:06:28
tags: 数据库
---

Elasticsearch可作为TSDB已经早有耳闻，而且自从v2版本之后，更是加了很多特性，使其更加适合作为TSDB使用。而[这一篇文章](https://www.elastic.co/blog/elasticsearch-as-a-time-series-data-store)给出了一个详细的例子，个人认为其最有价值的地方在于给出了一个参考的[schema mapping](https://github.com/stagemonitor/stagemonitor/blob/influxdb/stagemonitor-core/src/main/resources/stagemonitor-elasticsearch-metrics-index-template.json)。尤其是其中将"_all"和"_source"设为关闭，余心有戚戚焉。

同时，对于长期存储的优化建议也不错，但终究赶不上上面提到的mapping更直接，:)

附带说一句，文中提到的[stagemonitor](http://www.stagemonitor.org/)很让人惊艳，打算抽时间看看。
