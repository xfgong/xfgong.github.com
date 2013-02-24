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


    1. 可以使用vim来编辑
    2. 使用git进行版本管理
    3. 可以github pages功能进行免费托管
    4. 可以bind独立域名

<!--more-->

有了这几点对于博客来说已经完全足够了，不需要额外维护vps，简单可靠，并且github已经被G\*F\*W认证过，说明是个好网站。

搭建jekyll的过程可以直接参考阮一峰的博文，写的比较详细，如果对自己的博客做一些装饰变得好看一些，可以参考其他人的[Site](https://github.com/mojombo/jekyll/wiki/Sites)，可以从里边选一个觉得不错的，然后直接clone到自己的repo中即可。

jekyll的搭建过程和基本的使用方法我这里就不赘述了，网上一搜一大堆。不过在搭建过程中出现的问题，以及解决办法还是说一下，肯定有人会遇到类似问题。

### 问题1 首页中如何显示文章摘要

看了一下jekyll的api，post没有摘要的属性，不过这个可以通过对liquid模板稍微做一些调整，例如我在index.md中这样处理:
    
    {% raw %}
    <div class="excerpt">{{ post.content | split:'<!--more-->'| first }}</div>
    {% endraw %}

这样在主页的文章列表中可以只显示`<!--more-->`前面的内容。

### 问题2 Page build failure

在本地进行调试时是OK的，但是push到github后，新的post并没有出现，查看repo的settings页面显示：
> Your page is having problems building: page build failed

同时也会收到github发来的page build failure的邮件，但是邮件中和settings页面上未有任何错误提示。
之所以出现在本地调试没问题，但是github build failed，大部分是因为各种版本不对，所以为了避免出现这个问题，根据github的[help页面](https://help.github.com/articles/using-jekyll-with-pages#troubleshooting)，使用与github版本一致的库：

    gem 'jekyll',     '=0.12.0'
    gem 'liquid',     '=2.4.1'
    gem 'redcarpet',  '=2.1.1'
    gem 'maruku',     '=0.6.0'
    gem 'rdiscount',  '=1.6.8'
    gem 'RedCloth',   '=4.2.9'

可以使用

    $gem list

命令查看已经安装库的版本，如果与上面的版本不一致，可以使用

    $sudo gem ins jekyll --version '=0.12.0'

进行安装对应版本的库，版本与github使用的一致后，就可以根据错误信息进行调试了。

最后给出几个有用的链接：
* [Markdown Syntax](http://en.wikipedia.org/wiki/Markdown) Markdown语法格式
* [Jekyll Plugins](https://github.com/mojombo/jekyll/wiki/Plugins) Jekyll各种插件
* [Jekyll-Bootstrap](https://github.com/plusjade/jekyll-bootstrap) 适合快速上手，里面有几套不错的theme
