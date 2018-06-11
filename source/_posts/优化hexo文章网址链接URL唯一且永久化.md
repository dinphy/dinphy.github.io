title: hexo-abbrlink 插件使用
categories:
  - 学习参考
  - ''
tags:
  - web技术
  - github
  - hexo
abbrlink: '31143271'
date: 2018-05-19 12:16:00
---
### 网址链接URL唯一且永久化

- 使用插件hexo-abbrlink可以做到，安装：
>npm install hexo-abbrlink --save

我们可以发现hexo默认生成的文章地址路径是 【网站名称／年／月／日／文章名称】。

- 然后hexo的根目录配置文件_config.yml中修改：

```js
#permalink: :year/:month/:day/:title/
permalink: posts/:abbrlink/
#permalink_defaults:
abbrlink:
	alg: crc32
	rep: hex
```
<!--more-->
这样就确保了文章链接的唯一化，只要不修改md文件的abbrlink的值，url就永久不会改变。如此md文件名和文件内容也可以随便改了。

### 添加robots.txt

- hexo的source文件下新建robots.txt，内容如下:

```js
# hexo robots.txt
User-agent: baidspider
Disallow: /
Disallow: /*
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-Agent: 360Spider
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-Agent: Sogouspider
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-Agent: Yahoo! Slurp
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-Agent: Yisouspider
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-agent: Bingbot
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*

User-agent: *
Disallow: /*
Disallow: /admin
Disallow: /categories/*
Disallow: /tags/*
Disallow: /archives/*
Sitemap: https://dinphy.github.io/sitemap.xml
```
robots.txt是搜索引擎蜘蛛协议，告诉引擎哪些要收录，哪些禁止收录。

到此完成了。