---
layout: post
title: "Flag for Chrome修复更新PageRank"
date: 2012-02-21 16:31
comments: true
categories: tech
---
Flag for Chrome 是一款 chrome 上的插件，它能显示被访问网站服务器所在国家和地区、Geo、Google PageRank,、Alexa Rank和WOT等信息。功能和 firefox 上的 flagfox 还要强大。我就经常用它来看网站的所在国家和 PageRank。<a href="https://chrome.google.com/webstore/detail/dbpojpfdiliekbbiplijcphappgcgjfn" target="_blank">插件下载地址</a>

在近段时间的使用中，以前 chrome 地址栏上 Flag for Chrome 显示的 PageRank 值显示为问号。经过一番检查，原来是 google 的 PageRank 已经停止使用，但是 PageRank 的 API 还没有撤销，只不过 google 把它更改了一下，加上插件作者好长段时间没有更新了，所以原本显示 PageRank 的地方成了问号。现在给大家介绍如何修复 PageRank 的显示问题。
<ol>
	<li><strong>找到插件的文件位置。</strong>一般来说，chrome插件的文件位置就是在它的安装目录里面。比如我的“C:\Users\<strong>用户名</strong>\AppData\Local\Google\Chrome\User Data\Default\Extensions\dbpojpfdiliekbbiplijcphappgcgjfn\0.4.1_0”，其中dbpojpfdiliekbbiplijcphappgcgjfn为 Flag for Chrome 在应用市场的 ID，“0.4.1_0”是插件的版本号。<strong>注意</strong>：AppData 文件夹为默认隐藏，需要修改文件夹选项将其显示。</li>
	<li><strong>修改 js 文件夹中的 PageRank.js 文件。</strong>替换“http://toolbarqueries.google.com/search?client=navclient-auto&amp;hl=en&amp;ch=”字段为“http://toolbarqueries.google.com/tbr?client=navclient-auto&amp;features=Rank&amp;ch=”。</li>
	<li><strong>重启 Chrome 浏览器。</strong></li>
</ol>
<div>大功告成，现在 PageRank 又回到我的地址栏了。在最后，恳请此插件的作者早日更新这个 bug。</div>