---
layout: post
title: "notepad++解决多余空行"
date: 2011-08-25 9:43
comments: true
categories: sparks
---
Notepad++ 是一款免费的开源的跨平台的代码编辑器。它支持包括中文在内的多国语言，功能强大，除了可以用来制作一般的纯文字说明文件，也十分适合当作撰写电脑程序的编辑器。Notepad++不仅可以实现语法高亮显示，也有语法折叠功能，并且支持宏以及扩充基本功能的外挂模组。

&nbsp;

自从使用notepad++来代替dreamweaver编辑网页文件后，notepad++强大的代码高亮和标签选中后自动寻找闭合标签功能让敲代码变得更加方便。以前用dreamweaver的时候，代码一多的话，要想找到一个闭合的标签（比如“div”，在未加任何注释的情况下）的起始标签要花很长一段时间。但是在notepad++上面，只需点击闭合标签，notepad++就自动找到起始标签并且高亮它，非常方便了像我这样的懒人。<!--more-->

<a href="/static/images/2011/08/plug.jpg"><img class="alignnone size-full wp-image-142084" title="plug" src="/static/images/2011/08/plug.jpg" alt="" width="555" height="435" /></a>

&nbsp;

今天在使用notepad++的时候，遇到一个从外来文档中复制内容到notepad++中有多余空行的问题，现把解决方案提供给大家，希望对遇到这种问题的童鞋有帮助。

我在记事本或者在chrome的审查元素中复制代码到notepad++的时候，notepad++会很“有爱”的给每行代码加上一行空行。代码少的话，就手工删除空行。但是今天从记事本中复制了近100行的base64代码，要是还像以前手工删除空格的话，需要的时间可想而知。于是到Google上一阵狂搜，终于找到解决方法——使用notepad++自带的插件TextFX。如上图。

首先，选中需要删除空行的代码，然后依次点击TextFX→TextEdit→Delete Blank Lines，那些恼人的空行就消失了。

其实notepad++自带的TextFX插件功能非常强大，只不过我一直把它给忽略了。现在给大家简单介绍一下这个插件部分常用功能：
<ul>
	<li><strong>TextFX Characters -&gt; UPPER CASE, lower case, Proper Case, Sentence case, iNVERT cASE</strong>: 批量改变选中文字的大小写。</li>
	<li><strong>TextFX Edit -&gt; Delete Blank Lines</strong>: 这个就是我刚才说的删除空格。</li>
	<li><strong>TextFX Edit -&gt; Delete Surplus Blank Lines</strong>: 将选中文字的多个连续空格转换成一个空格。</li>
	<li><strong>TextFX Convert -&gt; Encode URI Component</strong>: 转换选中文字中的标点符号成16进制，让其对URL友好。</li>
	<li><strong>TextFX Convert -&gt; Encode HTML (&amp;&lt;&gt;”)</strong>: 将HTML文件中的尖角符号转换成16进制。</li>
	<li><strong>TextFX HTML Tidy -&gt; Tidy Reindent XML</strong>: 将未格式化的xml文件按照规格缩进。（很实用的说）</li>
	<li><strong>TextFX Tools -&gt; Sort lines case sensitive, Sort lines case insensitive</strong>: 排序。</li>
	<li><strong>TextFX Tools -&gt; Insert Line Numbers</strong>: 为选中的文字加上行号，基于此文件的第一行排序。</li>
	<li><strong>TextFX Tools -&gt; Word Count</strong>: 对选中的文字记数，包括详细的文字总数，行数等等。如下图：</li>
</ul>
<div><a href="/static/images/2011/08/notepad++-word-count.png"><img class="alignnone size-full wp-image-142085" title="notepad++-word-count" src="/static/images/2011/08/notepad++-word-count.png" alt="" width="259" height="274" /></a></div>
建议大家花几分钟的时间查看一下TextFX插件，有可能你会惊喜的发现以前需要很大工作量的修改，用这个插件的一个功能就可以实现。这也是一中探宝行动吧。

如果大家对我的这篇文章有疑问，你可以在<a href="http://www.douban.com/people/glowin/" target="_blank">豆瓣</a>、<a href="http://t.sina.com.cn/jiangbian66/" target="_blank">新浪微博</a>、<a href="http://t.qq.com/daniel_jiang" target="_blank">腾讯微博</a>或者<a href="https://twitter.com/#!/glow_chiang" target="_blank">twitter</a>上与我联系解决。