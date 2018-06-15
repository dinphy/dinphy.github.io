title: 使用JQuery中的attr()获取和设置元素属性
author: Dinphy - 简乐
abbrlink: 8b51e2ad
tags:
  - JQuery
  - attr
  - 设置属性
categories:
  - 学习参考
date: 2018-06-15 08:34:00
---
##### attr() 函数简介
jquery 中用 attr() 方法来获取和设置元素属性,attr 是 attribute（属性）的缩写，在jQuery DOM操作中会经常用到attr()，attr()有4个表达式。
##### 语法定义
> $(selector).attr(attribute)
> $(selector).attr(attribute,value)
> $(selector).attr(attribute,function(index,oldvalue))
> $(selector).attr({attribute:value, attribute:value ...})

| 参数 | 描述 |
| - |: - |
| selector | 获取将要设置属性的元素。 |
| attribute | 规定要获取其值的属性或名称。 |
| value | 规定属性的值。 |
| function(index,oldvalue) | 该函数可接收并使用选择器的 index 值和当前属性值。 |
| attribute:value | 规定一个或多个属性/值对。 |
##### 实例运用
- HTML结构
```js
<a href="javascript:;" id="theme-toggle" title="黑白切换">
	<i class="icon icon-lg icon-sun-o" style="font-weight: bold"></i>
</a>
```
这是本站黑夜白天模式切换的一个案例，此行的木碧是获取 a 元素中的 title 属性，然后将其值修改，为了避免 a 元素和页面上的其他元素混淆，这里定义了一个 id ，通过 id 来获取比较唯一。
- script脚本
```js
if (theme !== 'night') {
	body.classList.add('night-mode');
	S.setItem('theme', 'night');
	$('#theme-toggle').attr('title','当前是夜间模式');
}
else {
	body.classList.remove('night-mode');
	S.setItem('theme', 'not-night');
	$('#theme-toggle').attr('title','当前是日间模式');
}
```
这里用到的是 attr() 中的第二种语法：
> $(selector).attr(attribute,value)

##### 更多参考
- [jQuery 属性操作 - attr() 方法](http://www.w3school.com.cn/jquery/attributes_attr.asp)
- [JQuery中attr()获取和设置元素属性](https://blog.csdn.net/IT_beast/article/details/52203305)