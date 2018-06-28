title: 将 hexo 个人网站托管于coding.net
author: Dinphy - 简乐
abbrlink: 5cd9f4a5
tags:
  - coding
  - 托管
  - 个人网站
categories:
  - 学习参考
date: 2018-06-28 19:42:00
---
##### coding 与 github 的区别
- coding 是国内的，访问速度快，金牌会员以下的首页有 5 秒广告跳转（下文有去除的方法）。
- github 是国外的，访问速度慢，但用户多，可靠，安全性高，免费无广告。
![](https://dn-coding-net-production-pp.qbox.me/dbb26a62-68d3-4ed5-b0ef-d883b8aba999.png)
##### coding 与 github 仓库托管原理
- 同：二者托管的原理一样，使用 git 工具完成。
- 异：coding 是中文界面且支持静态和动态网站托管（例如：PHP），github 是英文界面，仅支持静态页面托管。

##### 将 hexo 托管于 coding 上
1. 账号注册与登录
  - coding 主页：[https://coding.net/](https://coding.net/)
  - 可以使用 github 账号登录，然后设置一个用户名也行。
2. 新建项目
  - **项目名必须与用户名称一致**，否则会出现托管的页面不加载 css 与 js 的问题。
  > 例如：用户名为 `dinphy` ，那么新建的项目名也要是 `dinphy` 。完成后的访问地址是： `dinphy.coding.me/dinphy`
  
  - 使用 github 上传源码的方法把网站的源码传到你新建的项目中。
  - 展开左侧**代码**菜单，找到下面的 **Pages 服务**，静态与动态自己选择，部署分值为 master 。
  - 域名绑定：如果要绑定自己购买的域名，必须在项目根目录添加 CNAME 文件，并在此文件中添加购买的域名，如我的是：`www.dinphy.wang`，我就在 CNAME 中添加这个；不绑定域名可以忽略。
  - 强制 HTTPS 访问：视情况而定，想开就开吧。
  - Hosted by Coding Pages (去除首页 5 秒跳转的广告)
  > 银牌会员的 Coding Pages 在访问时默认会先加载 Pages 跳转页，您可选择在网站首页任意位置放置**「Hosted by Coding Pages」**的文字版或图片版，然后勾选下方的**「已放置 Hosted by Coding Pages」**选项，通过审核后您的 Pages 将不会显示跳转页。请务必将**「Hosted by Coding Pages」**持续保留在网站首页，撤掉后跳转页会再次出现。
  
  等一两个工作日就可以了。
![](http://upload-images.jianshu.io/upload_images/782269-f21be3393bf0caa1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  这里我放到了页脚下，我的页脚每一页都会显示，所以也包括了首页。
  ```js
  <p>Hosted by <a href="https://pages.coding.me" style="font-weight: bold">Coding Pages</a></p>
  ```
  显示效果：
  > <p>Hosted by <a href="https://pages.coding.me" style="font-weight: bold">Coding Pages</a></p>
  
##### _config.yml配置
配置和 github 相似
- 只托管在 coding 的情况

```js
deploy:
  type: git
  repository: https://git.coding.net/dinphy/dinphy.git
  branch: master
  message: '站点更新:{{now("YYYY-MM-DD HH:mm:ss")}}'  
```
- 同时托管在 coding 和 github 的情况

```js
deploy:
- type: git
  repository: git@github.com:dinphy/dinphy.github.io.git
  branch: master
  message: '站点更新:{{now("YYYY-MM-DD HH:mm:ss")}}'
- type: git
  repository: https://git.coding.net/dinphy/dinphy.git
  branch: master
  message: '站点更新:{{now("YYYY-MM-DD HH:mm:ss")}}'  
```
  
最后就是 `hexo d` 部署到仓库了。

如果不想每次都输入用户名和密码，那么可以添加 ssh 到 coding 上面的公钥上。

添加方法参考：[Hexo 主题 teal 使用](http://localhost:4000/posts/8e1e451e/)

本文到此结束。