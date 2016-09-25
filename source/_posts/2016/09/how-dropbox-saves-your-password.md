---
title: Dropbox保存用户口令的安全之法
date: 2016-09-25 21:10:13
tags: 安全
---

近日，[Dropbox公布了它的用户口令保存安全之道](https://blogs.dropbox.com/tech/2016/09/how-dropbox-securely-stores-your-passwords)，以应对日益猖獗的网络安全形势。这不，就在前几天，[Yahoo就承认至少丢失了5亿用户数据](https://yahoo.tumblr.com/post/150781911849/an-important-message-about-yahoo-user-security)。

Dropbox的方法可以归结成两点：多重Hash并加密和关键数据单独保存。Dropbox用下图进行了展示：

<img src="https://dropboxtechblog.files.wordpress.com/2016/09/layers.png" width="650" height="443" />

从下到上可以视为Password的处理过程，最外层加密用的全局密钥（Dropbox称之为pepper）单独存放，这样即使存放口令存放点被破，黑客依旧无法拿到pepper，无法就口令破解实施攻击。

针对每一层的算法选择，Dropbox分别给出了理由：
- SHA512，将口令规范化成512 bit值，克服bcrypt的缺点。
- bcrypt，高强度hash，防止暴力破解。
- AES256，采用加密而非Hash是为了方便轮换（rotate，注：猜测是定期重新计算一次，故能解密就能方便的实现这一点。而单向加密，则无法做到）。按照文中的说法，Dropbox还有计划将这个全局密钥植入硬件。

就这个方案来讲，应该是我目前所见为止最强的方案了！
