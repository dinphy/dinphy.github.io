title: CKEditor 编辑内容时，回车生成段落P，首行缩进两字
author: Dinphy - 简乐
abbrlink: b09dbdd3
tags:
  - ckeditor
  - 换行
  - 段落
categories:
  - 学习参考
date: 2018-10-20 13:04:00
---
使用 ckeditor 编辑器时，按回车会自动添加 `<br />` 标签强制换行，而且行距之间距离不好控制，若用 CSS 给它 `display:none;` 属性的话，之前处理好的文章就会合并到一起，所以为了能更好的掌控，决定将 `<br />` 标签换成 `<p>&nbsp;</p>` 标签，对于 `<p>&nbsp;</p>` 标签处理起来就方便的多。

查看 ckeditor 编辑器源码时会看到，点击回车显示的 `<p>&nbsp;</p>` 。

解决这个问题说简单也不简单，说难也不难，不过终究还是解决了。

##### 1、替换 br 标签为 p 标签

首先，修改 ckeditor/config.js 配置文件里面的 `CKEDITOR.editorConfig = function( config )` 函数下的代码。

将原始代码

```js
  config.enterMode = CKEDITOR.ENTER_BR;
  config.shiftEnterMode = CKEDITOR.ENTER_P;
```

修改为

```js
  config.enterMode = CKEDITOR.ENTER_P;
  config.shiftEnterMode = CKEDITOR.ENTER_BR;
```

最后，清理一下浏览器的缓存就可以看到效果了。

##### 2、段落首行缩进两字

首先，修改 `ckeditor/skin/kama/editor.js` 文件中的 `.cke_panel_listItem p` 属性,在p后面添加：`{text-indent:2em;}` ；完成后如下： `.cke_panel_listItem p{text-indent:2em;}` 。

最后，清理一下浏览器的缓存就可以看到效果了。