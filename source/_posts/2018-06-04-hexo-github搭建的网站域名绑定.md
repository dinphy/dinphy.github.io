title: hexo + github搭建的网站域名绑定
author: Dinphy - 简乐
abbrlink: 1eb48005
tags:
  - web技术
  - hexo
  - 域名绑定
  - ''
categories:
  - 学习参考
date: 2018-06-04 10:35:00
---
每个网站都有属于自己独特的域名，有些很容易记住，有些具有特别意义，根据自己定位吧。本文简单介绍一下把已经搭建好的网站与域名绑定。

使用hexo + github搭建web网上教程很多，千篇一律的就是那几个步骤。

1. 新建一个github仓库：`username.github.io`
2. 在本地新建一个空文件夹用于初始化 hexo 站点：`npm install hexo-cli -g` 和 `hexo init`。
3. git clone 自己喜欢的主题，然后配置根目录和主题目录下的 `_config.yml` 文件。
4. 安装主题相应的依赖和插件 `npm install`。
5. 生成静态页面：`hexo g`。
6. 本地测试：`localhost:4000`。
7. 配置本地与 github 仓库的 keygen ，配置 `git config --global user.name` 账号和 `git config --global user.email` 邮箱，deploy 中也要配置 repo 。
8. 上传 github 仓库：`hexo d`。

本文重要的不要上面这些，下面的才是重点。

对于域名绑定难易程度看个人。

** 具体如下：**

- 申请域名

> 阿里云，西部数据，新网，万网，国外的，随便找一个提供商申请即可。

- 域名解析
```js
主机名   域名类型       对应值
@        CNAME     dinphy.github.io
www      CNAME     dinphy.github.io
```
(主机名默认是@)

- github 仓库添加 CNAME（用来解析域名）

在CNAME中添加如下内容：

> www.dinphy.wang

添加的内容其实就是注册的域名。

到此本文结束。