---
layout: post
title: "Dreamweaver CS5中ICERegions.htm翻译加载错误解决办法"
date: 2010-11-25 13:21
comments: true
categories: 
---
今天打开dreamweaver准备修改下网页的html文档时，dreamweaver频繁的弹出错误窗口，关闭后又弹出来了，很是恼人，如下：（我用的是英文版的DW，中文版的应该内容相似吧）
<blockquote>The following translators were not loaded due to errors:
ICERegions.htm:has configuration information that is invalid.</blockquote>
本人之前并未修改dreamweaver的配置，在感觉莫名其妙的同时google一下了解决办法，方法如下：<!--more-->

1、关闭dreamweaver。

2、打开我的电脑，连接到一下路径：

<strong><span style="color: #ff0000;"> win7</span></strong> : C:\Users\你的用户名\AppData\Roaming\Adobe\Dreamweaver CS5\【你使用的语言】\Configuration
<strong><span style="color: #ff0000;">XP</span></strong> ：C:\Documents and Settings\你的用户名\Application Data\Adobe\Dreamweaver CS4\【你使用的语言】\Configuration

找到如下文件：
WinFileCache-【一串数字】.dat

然后修改为：
WinFileCache-【一串数字】<span style="color: #ff0000;">-old</span>.dat

3、重启dreamweaver，那恼人的警告窗口终于不见了。

本文参考了<a href="http://www.wretch.cc/blog/sayopium/26257176">小卷＆虹的心情隨筆</a>的文章，希望对像我一样碰到这样问题的童鞋有帮助。

<ins datetime="2010-11-25T04:30:40+00:00">2010-11-25</ins>