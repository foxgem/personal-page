---
title: 趣文三则
date: 2016-06-12 19:06:01
tags: 阅读
---

今天阅读了三篇有趣的短文，因为都不长而且易懂，所以就一起记下了。

## [漫画：is Java Dying？](https://dzone.com/articles/big-numbers-comic)

知道天堂排名第三的人造数字是什么？咳咳，那就是“宣传Java正走向死亡的文章数量”，:)

## [消灭if语句的方法总结](http://code.joejag.com/2016/anti-if-the-missing-patterns.html)

if语句的问题已经是路人皆知了，文章介绍了5种方法来消灭它：

- 若方法的参数中有布尔类型，那就写成两个方法，一个对应false，另一个对应true
- 用多态来替换switch语句
- 采用Optional或NullObject避免null判断
    - Optional在Java 8或Guava中都有
    - NullObject，典型的如空数组或空字符串，视使用情况而定。Optional本质上也是一种NullObject。
- 尽量用inline语句来表达，如布尔表达式或三目运算符
- 将反复出现的if语句往调用链的上游移动

个人认为，可以从公共方法，且调用方最常用的那部分开始，逐步向内推进，这样可以让外层逻辑清爽很多。

## [谎言的4种语言特征](http://lifehacker.com/learn-to-spot-a-liar-with-these-verbal-signs-1780047717)

这篇文章相当于文中内嵌Ted视频的文字解读，列出了谎言的四种语言特征：

- 尽可能少的自我引用，一般采用第三人称说话
- 负面的语言，由于负罪感作祟
- 简单阐述，因为大脑很难产生复杂的谎言
- 故意用冗长晦涩的表达方式来讲一件简单的事情，简而言之就是“绕着弯说话”

今天的阅读小结就到这里，谢谢！
