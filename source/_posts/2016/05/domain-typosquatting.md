---
title: 那些恶意的相似域名（Domain Name Typosquatting）
date: 2016-05-22 17:19:17
tags:
- 安全
- The Morning Paper
---

原文：[The landscape of domain name typosquatting: techniques and countermeasures](https://blog.acolyer.org/2016/05/20/the-landscape-of-domain-name-typosquatting-techniques-and-countermeasures/)

人不是机器，总会犯错，这就给恶意相似域名提供了生存空间。文中提到的实验和数据充分证明了这些域名的“价值”。原本觉得这里面其实也就是钓鱼网站用得比较多，可看了这篇文章之后才知道还有那么多的道道：

- 广告点击
- 勒索
- 将用户导向竞争对手
- ……

文中提到的 typosquatting cross-site scripting(TXSS) 更是让人心有余悸，算是给code review又提供了一个很好的理由，;)
