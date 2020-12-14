---
layout: page
title: "Log"
description: "建站日志"
header-img: "img/post-bg-log.png"
---

# 20201213

设置百度统计

在`_config.yml`文件中设置`ba_track_id`，该值为[百度统计](https://tongji.baidu.com)中新增网站后在代码获取中的一长串ID。

<img src="https://gitee.com/wangzhebufangqi/PictureBed/raw/master/image-20201213210747622.png" width="80%"/>

可以发现，在`_includes\footer.html`文件中用到了这个ID：

```javascript
<!-- Baidu Tongji -->
{% if site.ba_track_id %}
<script>
    var _baId = '{{ site.ba_track_id }}';

    // Originial
    var _hmt = _hmt || [];
    (function() {
      var hm = document.createElement("script");
      hm.src = "//hm.baidu.com/hm.js?" + _baId;
      var s = document.getElementsByTagName("script")[0];
      s.parentNode.insertBefore(hm, s);
    })();
</script>
{% endif %}
```

用到了百度统计官方提供的代码。

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

