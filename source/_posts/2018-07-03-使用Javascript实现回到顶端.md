title: 使用Javascript实现回到顶端
author: Dinphy - 简乐
abbrlink: cec1b3cd
tags:
  - 返回顶端
  - JS实现
categories:
  - 学习参考
date: 2018-07-03 14:10:00
---
经常看到网页中有回到顶部的效果，今天也研究一下回到顶部有哪些方法。众所周知，用锚链接是实现回到最简单的方法，但是从用户体验效果来说，并不是最好的。（锚链接回到顶部时太快了，而且用户可能在看到某个感兴趣的东西想停下来，却停不下来），针对上面的缺点，我们试着用Javascript的方法来得到实现。思路是这个样子的：

#### 1、首先用html和css构建基本的例子

- **html部分：**

```js
        <div class="box">
            <img src="1.jpg"/>
        </div>
        <a href="javascript:;" id="btn" title="回到顶部"></a>
```

- **css部分：**

```js
        .box { width: 1190px; margin: 0 auto; }
        #btn{ width: 40px; height: 40px; background-color: red; position: fixed; right: 0px; bottom: 60px; background: url(2.jpg) no-repeat left top; }
        #btn:hover{ background: url(2.jpg) no-repeat left -40px; }
```

在这里应该注意的是：href="javascript:;"的目的是为了阻止浏览器默认行为。

#### 2、下面我们就可以用Javascript来控制我们的例子

##### a、首先模仿锚链接回到顶部的效果

- **代码如下：**

```js
window.onload  = function(){
    var obtn = document.getElementById('btn');
    obtn.onclick = function(){             
        var osTop = document.documentElement.scrollTop || document.body.scrollTop;
        document.documentElement.scrollTop = document.body.scrollTop = -200;                       
    };
}
```

这里的效果为，鼠标每点击一次，向上移动200像素（200像素是可以变化的），然后我们发现每次都要点击觉得很麻烦，这里我们不妨为它添加一个定时器函数

##### b、添加定时器函数

- **代码如下：**

```js
var timer = null;//在前面声明
timer = setInterval(function(){},30);//里面接的是移动200px效果
```

在这里，我们觉得还不是那么的好，比如说“别人家”的效果距离顶部越近的时候，速度越慢；并且我们中间还有一个问题就是回到顶部之后，在想继续往下看时不会继续往下了。

##### c、清除定时器效果并控制回到顶部的速率

- **代码如下：**

```js
//改变回到顶部的速度
var isSpeed = Math.floor(-osTop/6)
document.documentElement.scrollTop = document.body.scrollTop = osTop + isSpeed;
//清除定时器效果
if(osTop == 0){
    clearInterval(timer);
}
```

到这里，我们的效果差不多完成了，但是还是不能在滚动条滚动的时候，看到感兴趣的内容停下来。

##### d、滚动条滚动即停

- **代码如下：**

```js
var isTop = true;//先声明
 
//滚动条滚动时触发             
window.onscroll = function(){
                     
    if(!isTop){
        clearInterval(timer);
    }
    isTop = false;
};
 
isTop = true;//添加在obtn.onclick事件的timer中
```

到这里，我们还有一点小小的地方可以改动，就是当在可视窗口中，回到顶部是不出现的，到达一定值后才出现

##### e、回到顶部的显示与隐藏

- **代码如下：**

```js
/*在css中添加如下代码：*/
#btn{display: none;}
 
//获取页面的可视窗口高度
var clientHeight = document.documentElement.clientHeight || document.body.clientHeight;
 
/*在window.onscroll中添加如下代码，控制显示与隐藏*/
//在滚动的时候增加判断
var osTop = document.documentElement.scrollTop || document.body.scrollTop;//特别注意这句，忘了的话很容易出错
if (osTop >= clientHeight) {
    obtn.style.display = 'block';
}else{
    obtn.style.display = 'none';
}
```

这样，回到顶部的效果就实现了。

- **我们在看下完整的代码：**

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Javascript 回到顶部效果</title>
        <style type="text/css">
            #btn {
                width: 40px;
                height: 40px;
                position: fixed;
                display: none;
                right: 0px;
                bottom: 30px;
                background: url(2.jpg) no-repeat left top;
            }
             
            #btn:hover {
                background: url(2.jpg) no-repeat 0 -40px;
            }
             
            .box {
                width: 1190px;
                margin: 0 auto;
            }
        </style>
    </head>
 
    <body>
        <div class="box">
            <img src="1.jpg" />
        </div>
        <a href="javascript:;" id="btn" title="回到顶部"></a>
                 
        <script type="text/javascript">
            window.onload = function() {
                var obtn = document.getElementById('btn');
                var timer = null;
                var isTop = true;
                //获取页面的可视窗口高度
                var clientHeight = document.documentElement.clientHeight || document.body.clientHeight;
 
                //滚动条滚动时触发
                window.onscroll = function(){
                    //在滚动的时候增加判断
                    var osTop = document.documentElement.scrollTop || document.body.scrollTop;//特别注意这句，忘了的话很容易出错
                    if (osTop >= clientHeight) {
                        obtn.style.display = 'block';
                    }else{
                        obtn.style.display = 'none';
                    }
 
                    if (!isTop) {
                        clearInterval(timer);
                    }
                    isTop = false;
                };
 
 
                btn.onclick = function(){
 
                    //设置定时器
                    timer = setInterval(function(){
                        //获取滚动条距离顶部的高度
                        var osTop = document.documentElement.scrollTop || document.body.scrollTop;  //同时兼容了ie和Chrome浏览器
                         
                        //减小的速度
                        var isSpeed = Math.floor(-osTop / 6);
                        document.documentElement.scrollTop = document.body.scrollTop = osTop + isSpeed;
                        //console.log( osTop + isSpeed);
 
                        isTop = true;
 
                        //判断，然后清除定时器
                        if (osTop == 0) {
                            clearInterval(timer);
                        }
                    },30);
                     
                     
                     
                };
            }
        </script>
    </body>
 
</html>
```

到这里，还要小结一下，在中间我们运用的知识点：

#### 3、知识点回顾

- **DOM：**

```js
    1、document.getElementById()
    2、document.documentElement.scrollTop
    3、document.body.scrollTop

```

- **事件：**

```js
    1、window.onload
    2、window.onscroll
    3、obtn.onclick
```

- **定时器的使用：**

```js
    1、setInterval(function(){},30)
    2、clearInterval(timer)
```