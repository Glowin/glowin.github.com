---
layout: post
title: "notepad++小技巧之列编辑"
date: 2011-10-26 21:57
comments: true
categories: 
---
怎样让敲代码从一个脑力劳动变成乐趣是任何一款编辑器的终极目标，在这里我不得不提到notepad++这款神器。我从使用它到现在已经有一年有余了，并且已经代替dreamweaver成为我在windows系统上的首选编辑器（为什么要用notepad++而不是dreamweaver？知乎上的相关<a href="http://www.zhihu.com/question/19885458?nr=1&amp;noti_id=8316845#428229" target="_blank">讨论链接</a>）。今天向大家介绍notepad++上的一个使用小技巧——列编辑。

在编写javascript的时候，我们经常要把某个代码块注释或者进行批量编辑时，要是一行一行的给行首添加//注释的话，应该是一件很闹心的事。但是在notepad++上用两个快捷键就可以很好的解决这个问题，提高编程效率。

步骤：

1.在notepad++中，先指定到要批量添加注释的地方，使用 Shift+Alt 快捷键不放，用鼠标点击要处理的代码后点击，notepad++会高亮选中的代码块。

<a href="/static/images/2011/10/notepad++.jpg"><img class="alignnone size-full wp-image-142143" title="notepad++" src="/static/images/2011/10/notepad++.jpg" alt="" width="682" height="377" /></a>

2.快捷键选中代码块后，在你要批量添加的地方点击，然后快捷键 Alt + C，弹出编辑框如下图，在插入文本的输入框中添加你想输入的任何字符，这里我输入的是注释的//，点击回车，notepad++就自动在你想添加的内容。

<a href="/static/images/2011/10/notepad++2.jpg"><img class="alignnone size-full wp-image-142144" title="notepad++2" src="/static/images/2011/10/notepad++2.jpg" alt="" width="475" height="421" /></a>

<strong><span style="color: #ff0000;">买一送一：</span></strong>

在 <strong>vim</strong>中相关的操作为“块操作”，相关步骤如下：
<ol>
	<li>在normal模式中，输入“ ^ ”到达行首，快捷键 ctrl + O 开始块操作。</li>
	<li>快捷键 ctrl + d 向下移动，你也可以使用hjkl来移动光标，或是使用%，或是别的。</li>
	<li>输入“I” （大写的 i），在插入模式中输入"//"，按Esc键。I是插入，插入“//”，按ESC键来为每一行生效。</li>
</ol>