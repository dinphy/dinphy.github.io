title: hexo-admin 插件使用
author: Dinphy - 简乐
abbrlink: 96d8dc65
tags:
  - web技术
  - hexo
categories:
  - 学习参考
date: 2018-05-25 15:07:00
---
>用了几天hexo搭建的网站，感觉主题挺好的，就是发布文章时有点麻烦，于是搜索了一下有没有什么新的办法，快速发布文章的。
>网上有很多方法，这里我用了hexo-admin这个插件。用起来比较简单，界面也可以。
>使用方法如下：
- 在已经搭建好的环境中，也就是hexo 的根目录进行操作。
- 先使用官方的方法安装hexo-admin插件`npm install --save hexo-admin`
- 然后使用我FORK过来的[hexo-admin](https://github.com/dinphy/hexo-admin)
- 将我FORK过来的hexo-admin克隆下来到hexo根目录

<!--more-->
>git clone https://github.com/dinphy/hexo-admin.git
- 进入克隆下来的hexo-admin目录，执行`npm link`;
- 在 hexo 根目录下执行 `npm link hexo-admin`;
- 配置 hexo 根目录下的_config.yml文件，以下代码可以在Settings里面设置了获取，在文件中加入：

```js
# hexo-admin authentification
admin:
  username: dinphy
  password_hash: $2a$10$Cjsi8jHIzInUtkSBaK9tnOyv3oqqcJPS2MF3Mz6FlGj2JNQYlwVhm
  secret: Life is not easy, happiness is good
  deployCommand: 'hexo-deploy.sh'
```
(注意：username是管理员名称，password_hash是密码，secret是cookies缓存短语，据说越长越好，deployCommand是执行的命令，也就是Deploy页面的deploy按钮要调用的东西。我这里是在 hexo 根目录新建了一个hexo-deploy.sh文件，里面只有两条命令`hexo clean`和`hexo g -d`意思简单明了)。

这些都配置好了，就可以开始测试了本地执行`hexo s`，浏览器输入`http://localhost:4000/admin`就能进入管理后台了，输入用户名密码，就可以看到你发的文章了。

hexo-admin支持添加标签和分类，间隔几秒就可以保存草稿到本地，完了之后右上角的Pubilc点一下，Deploy页面点一下deploy按钮，就可以直接发布到站点上了。