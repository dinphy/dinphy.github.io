title: Hexo 主题 indigo 使用
author: Dinphy - 简乐
abbrlink: f52ea714
tags:
  - web技术
  - github
  - 主题
categories:
  - 学习参考
date: 2018-06-04 10:43:00
---
##### 安装前提
安装 Hexo 相当简单。然而在安装前，您必须检查电脑中是否已安装下列应用程序：

- [Node.js](http://nodejs.org/)
- [Git](http://git-scm.com/)

如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。

> npm install -g hexo-cli
> hexo init
> npm install

indigo 主题的所有依赖文件列表 package.json :
```js
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": "3.7.1"
  },
  "dependencies": {
    "cheerio": "^1.0.0-rc.2",
    "condense-whitespace": "^1.0.0",
    "hexo": "^3.7.1",
    "hexo-abbrlink": "^2.0.5",
    "hexo-admin": "^2.3.0",
    "hexo-autoprefixer": "^1.0.0",
    "hexo-deployer-git": "^0.3.1",
    "hexo-generator-archive": "^0.1.5",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-feed": "^1.2.2",
    "hexo-generator-index": "^0.2.1",
    "hexo-generator-json-content": "^3.0.1",
    "hexo-generator-search": "^2.2.5",
    "hexo-generator-tag": "^0.2.0",
    "hexo-helper-qrcode": "^1.0.2",
    "hexo-renderer-ejs": "^0.3.1",
    "hexo-renderer-less": "^0.2.0",
    "hexo-renderer-marked": "^0.3.2",
    "hexo-renderer-stylus": "^0.3.3",
    "hexo-server": "^0.2.2",
    "hexo-symbols-count-time": "^0.4.2",
    "hexo-wordcount": "^3.0.2",
    "less": "^3.0.4",
    "style-loader": "^0.21.0"
  },
  "devDependencies": {
    "stylus": "^0.54.5",
    "stylus-loader": "^3.0.2"
  }
}
```
##### 主题安装

安装需确认你的 Hexo 版本在 3.0 以上，以及 Node 版本为 6.x 以上，在 Hexo 根目录，执行以下命令。

> git clone git@github.com:dinphy/hexo-theme-indigo.git themes/indigo

##### 依赖安装

还是在 Hexo 根目录，如果以下插件已安装过，无需再次安装。

- Less

用于主题默认使用 less 作为 css 预处理工具。

> npm install hexo-renderer-less –save

- Feed

用于生成 rss。

> npm install hexo-generator-feed –save

- Json-content

用于生成静态站点数据，用作站内搜索的数据源。

> npm install hexo-generator-json-content –save

- QRCode

用于生成微信分享二维码。可选，不安装时会请求 jiathis Api 生成二维码。

> npm install hexo-helper-qrcode –save

- wordcount

用于统计文章字数。

> npm install hexo-wordcount –save

- condense-whitespace

用于从字符串中移除前导、尾随和重复的空白。

> npm install condense-whitespace –save

- cheerio

用于快速、灵活和精益实现核心 jQuery 专为服务器设计。

> npm install cheerio –save

- hexo-autoprefixer

用于 Hexo 自动预修插件。

> npm install hexo-autoprefixer –save

- hexo-symbols-count-time

用于符号计数和时间阅读的文章插件。

> npm install hexo-symbols-count-time –save

- hexo-deployer-git

用于 Git 部署上传。

> npm install hexo-deployer-git –save

- hexo-generator-search

用于 Hexo 生成搜索数据的插件。

> npm install hexo-generator-search –save

- hexo-abbrlink

用于帖子创建一个和唯一的链接。

> npm install hexo-abbrlink –save

- hexo-admin

用于 Hexo 后台管理界面。

> npm install hexo-admin –save

- stylus-loader stylus

用于 webpack 的手写笔加载程序。

> npm install stylus-loader stylus –save-dev

- stylus

用于提供一种高效、动态和表达方式来生成 CSS。支持缩进语法和常规 CSS 样式。

> npm install stylus -g

- other

这些是初始化就有的。

```js
npm install hexo –save
npm install hexo-generator-index –save
npm install hexo-generator-archive –save
npm install hexo-renderer-ejs –save
npm install hexo-renderer-marked –save
npm install hexo-renderer-stylus –save
npm install hexo-server –save
```
- 遇到了几个棘手的问题

问题描述如下:
```js
 ERROR D:\MyWeb\hexoTest\themes\indigo\layout\archive.ejs:58
    57|                 </a>
 >> 58|                 <a class="catagories" href="/categories/<%- post.categories.data[0].name %>" target="_blank">
    59|                     <%- post.categories.data[0].name %>
    60|                 </a>
    61|             </div>

Cannot read property 'name' of undefined
TypeError: D:\MyWeb\hexoTest\themes\indigo\layout\archive.ejs:58
    56|                     <%- /(？|。|！)$/.test(post.title) ? post.title : post.title + '。' %>
    57|                 </a>
 >> 58|                 <a class="catagories" href="/categories/<%- post.categories.data[0].name %>" target="_blank">
    59|                     <%- post.categories.data[0].name %>
    60|                 </a>
    61|             </div>

Cannot read property 'name' of undefined
```
- 问题1：`Cannot read property 'name' of undefined`

原因是新建的帖子里面没有分类。

> 解决办法是：在新建的帖子里添加分类。

```js
ERROR D:\testHexo\themes\indigo\layout\layout.ejs:3
    1| <!DOCTYPE html>
    2| <html>
 >> 3|     <%- partial('_partial/head') %>
    4|
    5| <body>
    6|     <script>

D:\testHexo\themes\indigo\layout\_partial\head.ejs:37
    35|         }
    36|     %>
 >> 37|     <title><% if (title){ %><%= title %> | <% } %><%= config.title %> | <%= config.subtitle.replace(/<[^>]*>/g, '') %></title>
    38|     <%
    39|         var keyWords = config.keywords;
    40|         if(page.tags){

Cannot read property 'replace' of null
TypeError: D:\testHexo\themes\indigo\layout\layout.ejs:3
    1| <!DOCTYPE html>
    2| <html>
 >> 3|     <%- partial('_partial/head') %>
    4|
    5| <body>
    6|     <script>

D:\testHexo\themes\indigo\layout\_partial\head.ejs:37
    35|         }
    36|     %>
 >> 37|     <title><% if (title){ %><%= title %> | <% } %><%= config.title %> | <%= config.subtitle.replace(/<[^>]*>/g, '') %></title>
    38|     <%
    39|         var keyWords = config.keywords;
    40|         if(page.tags){

Cannot read property 'replace' of null
```

- 问题2：`Cannot read property 'replace' of null`

原因是根目录下的 `_config.yml` 没有定义 `subtitle` 。

> 解决办法是：删除根目录下的 `node_modules` 文件夹，重新执行 `npm install`，然后在根目录下 `_config.yml` 中定义 `subtitle`。

**例如：**

> subtitle: 生活不易,快乐就好

本文到此结束。