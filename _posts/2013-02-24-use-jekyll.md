---
layout: post
title: "使用jekyll写博客"
description: "使用jekyll写博客"
category: Tools
tags: jekyll github
---
{% include JB/setup %}

很久以前就想，如果博客可以用wiki语法来编辑纯文本的话，那应该非常爽，不去纠结于各种html。
前一阵看到阮一峰的[这篇文章](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html "搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门")，觉得非常不错，今天试了一下并试用了一下发现确实不错，非常适合我们程序猿使用:

<!--more-->

    1. 可以使用vim来编辑
    2. 使用git进行版本管理
    3. 可以github pages功能进行免费托管
    4. 可以bind独立域名


有了这几点对于博客来说已经完全足够了，不需要额外维护vps，简单可靠，并且github已经被G\*F\*W认证过，说明是个好网站。

搭建jekyll的过程可以直接参考阮一峰的博文，写的比较详细，如果对自己的博客做一些装饰变得好看一些，可以参考其他人的[Site](https://github.com/mojombo/jekyll/wiki/Sites)，可以从里边选一个觉得不错的，然后直接clone到自己的repo中即可。

jekyll的搭建过程和基本的使用方法我这里就不赘述了，网上一搜一大堆。不过在搭建过程中出现的问题，以及解决办法还是说一下，肯定有人会遇到类似问题。

### 问题1 首页中如何显示文章摘要

看了一下jekyll的api，post没有摘要的属性，不过这个可以通过对liquid模板稍微做一些调整，例如我在index.md中这样处理:
    
    {% raw %}
    <div class="excerpt">{{ post.content | split:'<!--more-->'| first }}</div>
    {% endraw %}

几个有用的链接：

* [Markdown Syntax](http://en.wikipedia.org/wiki/Markdown)
