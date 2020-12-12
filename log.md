---
layout: page
title: "Log"
description: "建站日志"
header-img: "img/post-bg-log.png"
---

# 20201212

修改博客内容侧边栏目录样式。

在`css/hux-blog.min.css`文件（**打开后是压缩后的一行，可利用[在线工具](https://c.runoob.com/front-end/52)解压缩**）中的`.side-catalog .catalog-body`字段进行修改：

```css
.side-catalog .catalog-body .h1_nav{
	margin-left:0;
	font-size:18px;
	font-weight:700
}
.side-catalog .catalog-body .h2_nav{
	margin-left:5px;
	font-size:16px;
	font-weight:500
}
.side-catalog .catalog-body .h3_nav {
	margin-left:10px;
	font-size:14px;
	font-weight:300
}
```

这样就将1、2、3级标题区分开来了，其他同理。

另外，原模板会用...代替溢出的内容，可修改为visible

```css
.side-catalog {
	display:block;
	overflow:visible;	/* 由hidden修改为visible */
	height:100%;
	padding-bottom:40px;
	width:195px
}
```

# 20201211

开始学习jekyll，尝试在模板的基础上进行DIY

# 20201115

fork他人[模板](https://github.com/qiubaiying/qiubaiying.github.io)，jekyll+Github Pages

