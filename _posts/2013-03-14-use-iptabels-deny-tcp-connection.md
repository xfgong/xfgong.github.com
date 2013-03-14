---
layout: post
title: "使用iptabels拒绝tcp连接"
description: ""
category: Tools
tags: iptables
---
{% include JB/setup %}

在对写的程序进行功能测试时，需要模拟一些极端的网络环境，需要在程序过程中断开与某个IP的网络连接，这个可以使用iptables轻松实现。

拒绝接收某个IP的请求：

    iptables -A INPUT -d 1.1.1.1 -p tcp -j DROP

拒绝主动连接某个IP：

    iptables -A OUTPUT -d 1.1.1.1 -p tcp -j DROP

删除相关的规则，只要将上面命令的 -A 修改为 -D 即可。
