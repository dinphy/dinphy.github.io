hexo-theme-indigo
================
一个 Material Design 风格的 Hexo 主题。

Material Design 风格的 Hexo 主题，基于 Hexo 3.0+ 制作。 [Preview](http://me.lizhooh.com/)

## Feature

1. 仅支持 IE11+ 等现代浏览器。
2. 使用 Less 作为 css 预处理器，需要安装 `hexo-renderer-less`。
3. 添加了英文字体支持 Roboto。
4. 添加了一些波纹效果。By [Waves](https://github.com/fians/Waves)
5. 无前端依赖的分享实现。
6. 基于静态数据的站内搜索，无第三方侵入。
7. 支持文章打赏。

#### 以下是dinphy修改部分：[效果预览](https://dinphy.github.io)

8. 更改文章页结束语样式，页脚样式。

9. 更改左侧菜单栏样式，添加分类二级下拉伸缩，添加两个socail-icon。

10. TOC翻译为中文。

11. 添加Valine评论插件。

12. 调整文章页面标题显示样式。

13. 更新wave.less版本。

14. 调整文章、字数统计显示。

15. 全局采用链接加密，随机数生成，需要安装`hexo-abbrlink`。

>具体参考：[优化hexo文章网址链接URL唯一且永久化](https://dinphy.github.io/posts/31143271/)

## more
需要额外安装字数统计插件：

```bash
npm install --save hexo-wordcount
```

## all dependence
> npm install --save cheerio condense-whitespace hexo hexo-autoprefixer hexo-deployer-git hexo-generator-archive hexo-generator-category hexo-generator-feed hexo-generator-index hexo-generator-json-content hexo-generator-tag hexo-helper-qrcode hexo-renderer-ejs hexo-renderer-less hexo-renderer-marked hexo-renderer-stylus hexo-server hexo-symbols-count-time hexo-wordcount hexo-abbrlink