---
layout: post
title: "解压.gz文件"
description: "解压.gz文件"
category: Tools
tags: linux tips
---
{% include JB/setup %}

linux系统日志会自动将以往的日志打包成gz进行压缩，查看日志时需要解压：

    gzip -d syslog.2.gz
