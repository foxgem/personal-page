---
title: 管理JWT的生命周期
date: 2016-11-22 21:47:43
tags: 安全
---

在使用JWT时，一个让人纠结的问题就是“Token的时限多长才合适？”。对此，[Stormpath](https://stormpath.com/)的[这篇文章](https://stormpath.com/blog/manage-authentication-lifecycle-mobile)给出了一个可供参考的建议：
- 面对极度敏感的信息，如钱或银行数据，那就根本不要在本地存放Token，只存放在内存中。这样，随着App关闭，Token也就没有了。
- 此外，将Token的时限设置成较短的时间（如1小时）。
- 对于那些虽然敏感但跟钱没关系，如健身App的进度，这个时间可以设置得长一点，如1个月。
- 对于像游戏或社交类App，时间可以更长些，半年或1年。

并且，文章还建议增加一个“Token吊销”过程来应对Token被盗的情形，类似于当发现银行卡或电话卡丢失，用户主动挂失的过程。

关于“Token吊销”的实现，文章建议个方式如下：
- 在DB中记录用户对应的Token
- 实现一个Api Endpoint，负责将指定用户的Token从DB中删除

原文值得一读，并且在读之前，建议先读它的[前篇](https://stormpath.com/blog/the-ultimate-guide-to-mobile-api-security)。
