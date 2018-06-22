title: win7 开机启动 hexo server
author: Dinphy - 简乐
abbrlink: f3fd11c6
tags:
  - 开机启动
  - vbs
  - bat
categories:
  - 学习参考
date: 2018-06-22 10:14:00
---
为了更方便的使用 hexo 写文章，这里有一种通过脚本实现，可以开机启动hexo server的方法。需要创建2个脚本，一个为vbs脚本，一个为bat脚本。
> Hexo安装 hexo-admin 组件以后，所有的操作都可以在浏览器中轻松完成了，但是有一个问题就是每次开机都需要运行一次 `hexo s`

**vbs脚本放到启动文件夹，用于运行bat脚本，而bat脚本用于启动 `hexo server`**

##### 创建vbs脚本
```js
set ws=WScript.CreateObject("WScript.Shell")
ws.Run "D:\\webProject\\Hexo-blog\\hexo-server.bat /start",0
```
##### 将vbs脚本放到启动文件夹
将创建的vbs脚本保存到 win7 或 win10 的启动文件夹目录：
> C:\Users\你的用户名\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\hexo-server.vbs
##### 创建bat脚本
```js
D:
cd D:/webProject/Hexo-Blog
hexo s
```
bat脚本保存文件名和上面要对应，例如上面是 `hexo-server.bat`,保存一样即可。

这样就能实现开机启动 `hexo server` 了，剩下的一切都可以交给浏览器和hexo-admin了。

> 原文地址：[https://segmentfault.com/a/1190000008078142](https://segmentfault.com/a/1190000008078142)