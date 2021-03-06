---
title: 导致Web应用测试失败的罪魁祸首
date: 2016-05-30 20:34:24
tags:
- The Morning Paper
- 开发
---

但凡给Web应用写过自动化功能测试的人都会对这类测试的脆弱性印象深刻，并经常怀疑自己做这件事情的价值。相信我，若没有这样的疑问，那是你写的还不够多，;)

虽然脆弱，但它却并非一无是处，有时确实能够省掉不少人工，尤其是当UI已经定型并且在可预见的未来很长时间内不会有大的动作时。我猜[测试金字塔](http://martinfowler.com/bliki/TestPyramid.html)大概就是在这种又爱又恨的情绪下诞生的：很明显，跟UI有关的功能测试是最少的。

今天，[The Morning Paper上的一篇文章给这类测试的脆弱性提供了理论上的指导](https://blog.acolyer.org/2016/05/30/why-do-recordreplay-tests-of-web-applications-break/)，细节大家就上网站上自己看吧，结论是大家基本都很清楚的：导致Web应用功能测试失败的最大原因是测试中用到的定位符。这也难怪，人就是喜新厌旧的动物，再好看的UI看久了都会有审美疲劳。于是，改头换面自然就成了寻常事，这种背景下原来的测试用得上才怪。

我也是懒人，也不主张花很大代价去完成一个100%覆盖的功能测试。我更倾向于尽可能大面积覆盖较为稳定的非GUI测试（单元测试和集成测试），严格验证跟GUI交互的接口，最好能在无界面的前提之下就能验证功能流程的流转。至于GUI，则口子放的开一点，方便它们随时调整布局和设计。

最后又到广告时间，对于Web的功能测试，我推荐[Geb](http://www.gebish.org/)，它基于[Selenium](http://docs.seleniumhq.org/)，同时又支持[Spock](http://spockframework.org/)，而且还有[Grails](https://grails.org/)的插件，非常的方便易用。我之前在老东家SAP时还专门让人用它做了一个小的测试工具，效果还不错，;)
