---
layout: post
title: "给博客添加humans.txt"
date: 2011-09-23 18:21
comments: true
categories: sparks
---
<a href="http://glowface.net/2011/09/add-humans-txt/"><img class="alignnone size-full wp-image-142110" title="humanstxt" src="/static/images/2011/09/humanstxt.jpg" alt="" width="550" height="220" /></a>
<h2>一、什么是humans.txt</h2>
humans.txt 就是记录这个网站相关制作人员和一些有贡献的作者的文本文档，告诉搜索引擎我们是人开发，而不是通过程序自动生成的网站，通常放在网站的根目录。humans.txt 是相对于 robots.txt 而言的，它不像robots.txt 中的针对搜索引擎的语句那么生硬，网站所有者可以在这个txt文档中加入网站简介和copyright显得更加人性化。
<h2>二、其他网站的使用</h2>
humans.txt的<a href="http://humanstxt.org/" target="_blank">官方网站</a>对humantxt给出了很好的定义和应用，大家可以猛击<a href="http://humanstxt.org/humans.txt" target="_blank">这里</a>查看官网对于humans.txt的使用。Google也在它的网站添加了humans.txt，想必google的搜索蜘蛛以后会把humans.txt作为一部分参考。google的humans如下：
<blockquote>Google is built by a large team of engineers, designers, researchers, robots, and others in many different sites across the globe. It is updated continuously, and built with more tools and technologies than we can shake a stick at. If you'd like to help us out, see google.com/jobs.</blockquote>
<h2>三、如何添加humans.txt</h2>
说了那么多，现在给大家介绍一下如何在网站上添加humans.txt。

<strong>首先</strong>，新建一个txt文本文档，格式最好改为UTF-8（我用的是notepad++，“格式→转为UTF-8无BOM编码”），编辑完此txt文档后，命名此文件为humans.txt，上传到网站的根目录。

<strong>第二步</strong>，在header.php的&lt;head&gt;&lt;/head&gt;标签中插入如下的HTML代码:
<div class="source" style="font-family: Consolas, 'Lucida Console', 'Courier New'; color: #000000; background-color: #f9f7ed;"><span style="color: #1e90ff; font-weight: bold;">&lt;link</span> <span style="color: #1e90ff;">type=</span><span style="color: #aa5500;">"text/plain"</span> <span style="color: #1e90ff;">rel=</span><span style="color: #aa5500;">"author"</span> <span style="color: #1e90ff;">href=</span><span style="color: #aa5500;">"http://yourdomain.com/humans.txt"</span> <span style="color: #1e90ff; font-weight: bold;">/&gt;</span></div>
OK，大功告成，刷新一下网页，humans.txt添加成功。

<a href="/static/images/2011/09/humanstxt1.png"><img class="alignnone size-full wp-image-142118" title="humanstxt1" src="/static/images/2011/09/humanstxt1.png" alt="" width="316" height="122" /></a>

&nbsp;
<h2>三、最后要说的话</h2>
humans.txt相对于robots.txt来说还是一个很新的概念，但是不排除它受到一些开源组织和Google的推崇，最终成为一个标准。我们可以想象一下如果humans.txt 最终成为标准的话，会有如下影响：
<ol>
	<li>该文件将被搜索引擎用来当做判断一个网站的信任程度的一个因素。</li>
	<li>html代码head部分将会进一步简化，类似于CSS的调用，可以将一些author, copyright等等元素统统放在这个文件里进行调用，缩减代码体积。</li>
	<li>主流浏览器会推出相应的插件或者内置功能用来解释Humans.txt，让访客第一时间了解该网站“关于我们”的信息，更加方便用户对网站有一个基本的了解。现在firefox已经有这样的插件了（猛击<a href="https://addons.mozilla.org/zh-CN/firefox/addon/humanstxt/" target="_blank">真相</a>）。</li>
</ol>
相关链接如下：

张鑫旭：<a href="http://www.zhangxinxu.com/wordpress/2011/01/humans-txt-%E7%BD%91%E7%AB%99%E7%9B%B8%E5%85%B3%E4%BA%BA%E5%91%98%E4%BF%A1%E6%81%AF%E8%AE%B0%E5%BD%95%E7%9A%84idea/" target="_blank">humans.txt-网站相关人员信息记录的idea</a>

<a href="http://humanstxt.org/" target="_blank">humans.txt官方网站</a>(英文)

谷奥：<a href="Google 不仅有 robots.txt，还有 humans.txt" target="_blank">Google 不仅有 robots.txt，还有 humans.txt</a>