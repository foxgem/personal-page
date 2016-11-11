---
title: Hexo基础
date: 2016-11-11 11:35:18
tags: 写作
---

以下为这半年来玩Hexo的总结，希望对各位玩家有帮助，;)

---

## 入门

* npm install hexo-cli -g
* hexo init blog
* cd blog
* npm install
* hexo server

## 部署

* hexo generate
* hexo deploy

对于部署到github，配置：

~~~
deploy:
  type: git
  repo: https://github.com/foxgem/foxgem.github.io.git
~~~

## 文章

* 对于中文需更改语言，否则有问题：_config.yml
  * language: zh-CN
* 若因为墙的问题要换jquery的cdn地址：themes/landscape/layout/_partial/after-footer.ejs

~~~
    <script src="//code.jquery.com/jquery-2.0.3.min.js"></script>
~~~

* 多标签（YAML语法）

~~~
---
title: 那些恶意的相似域名（Domain Name Typosquatting）
date: 2016-05-22 17:19:17
tags:
- 安全
- The Morning Paper
---
~~~

用Atom时，Disable Markdown Formatter插件

## RSS和Sitemap

添加以下两个插件之后，重新生成就能看到atom.xml和sitemap.xml了：
* npm install hexo-generator-feed --save
* npm install hexo-generator-sitemap --save

## 目录整理

按自己意愿创建目录（_posts下），然后在_config.yml中改permalink（见下面的示例）：
* permalink: :title/

然后手动移到自己的目录中，原谅我这么懒，没有写一个工具。

## 个人域名

* 购买域名，在域名提供商那里添加解析规则
  - 记录类型：CNAME
  - 主机记录：www
  - 记录值：你的github个人主页地址
* 进入personal page的settings，修改【Custom domain】。
  - 这一步会生成在仓库中生成一个CNAME文件，将这个文件放到personal-page工程的source目录下。
* 个人域名目前不支持HTTPS

## 搜索引擎

GitHub禁止了百度搜索引擎，通常做法都是利用“虚拟空间+定时任务（git pull + FTP上传）+个人域名”方式进行。详细内容以及其他方案可参考：http://www.zhihu.com/question/30898326。

此外，放在国内空间上，个人域名需要备案。
