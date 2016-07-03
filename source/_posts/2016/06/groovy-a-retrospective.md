---
title: Groovy老鸟的回顾
date: 2016-06-06 20:05:48
tags: 开发
---

今天在DZone上读到[一名Groovy老鸟在即将转战其他语言之前写的自己对于Groovy的回顾总结](https://dzone.com/articles/groovy-a-retrospective)。文章盛赞了Groovy的稳定和简洁，同时也提及了Java程序员转Groovy时需要注意的思维转变。余心有戚戚焉。

关于类型这部分，我不能同意得更多：

> Again, in my opinion, typing is better - I still don't buy that typing def rather than the actual type is actually that much of a saving, and often ends up being a code-smell (even if it didn't start out as one). The official Groovy recommendation is to type things, with the exception of local method scoped variables - but even in that case I cannot see the benefit: there is no real gain to the developer in typing those precious fewer characters and the future readability suffers as other developers have to track through the code more to be sure as to what a variable is doing.

我记得在Burt寄给我的[“Programming Grails”](https://www.amazon.cn/Programming-Grails-Beckwith-Burt/dp/1449323936/ref=sr_1_1?ie=UTF8&qid=1465215356&sr=8-1&keywords=Programming+grails)一书中也提到了类似关于在变量声明时是否明确声明变量类型的内容。我个人觉得宗旨就是：不要影响阅读性。而且，在使用@CompileStatic时，声明类型有助于减少修改编译错误的麻烦。此外，声明类型可以带来额外的好处：在像Idea这样的IDE中可以方便的查看对应类型的源代码（按住Ctrl，在相应类型上鼠标点击即可）。
