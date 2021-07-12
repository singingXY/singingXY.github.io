---
title: 一个next主题版本产生的错误
date: 2021-07-12 17:28:50
tags:
  - hexo
  - next
---

github 报了安全警报，又到了升级的时候。
于是升级 hexo，升级完运行`hexo server`的时候，出来的不是我的博客界面，而是未生成的模板

```html
{% extends '_layout.swig' %} {% import '_macro/post.swig' as post_template %} {% import '_macro/sidebar.swig' as
sidebar_template %} {% block title %}{{ config.title }}{% if theme.index_with_subtitle and config.subtitle %} -
{{config.subtitle }}{% endif %}{% endblock %} {% block page_class %} {% if is_home() %}page-home{% endif -%} {% endblock
%} {% block content %}
<section id="posts" class="posts-expand">
  {% for post in page.posts %} {{ post_template.render(post, true) }} {% endfor %}
</section>

{% include '_partials/pagination.swig' %} {% endblock %} {% block sidebar %} {{ sidebar_template.render(false) }} {%
endblock %}
```

这不就废了嘛，以为是 guthub 访问不畅文件下载不全，又重新下了两次，依然是这样。
经过搜索后得到答案，需要下载更高版本的 next 主题
下载最新版的方法可以参考https://theme-next.js.org/docs/getting-started/installation.html
直接下了个最新版的 next 主题，运行`hexo server`，漂亮的主题回来了。

关于 next 主题还有一些事没有完成
个性化定制的 next 文件还是应该同步到 github 上面存放，不然换个电脑就没了，得找时间完善这个事。
