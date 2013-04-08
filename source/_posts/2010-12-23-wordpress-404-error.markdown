---
layout: post
title: "WordPress设置固定链接后，发生404错误解决办法"
date: 2010-12-23 19:56
comments: true
categories: tech
---
前几天在<a href="http://linfcstmr.net/" target="_blank">小红</a>童鞋的帮助下，顺利的把博客搬到他维护的服务器上面。转移数据库、安装插件好一阵忙活，然后在浏览器上输入域名，顺利打开了主页。正当我为搬家成功沾沾自喜的时候，意外发生了——点开主页上任何一个链接都是提示404错误，而且还不是我主题自定义的404页面。

于是请教Google大神，说是.htaccess的权限问题，只要在“后台→设置→固定链接”点击“保存更改”，让网站主目录的.htaccess更新一下就哦了。但是问题是，我的新服务器上的wordpress是原来就有的，我只是把原来的主题和插件复制到wordpress的目录下，和.htaccess没有关系。按照这个方法更新了.htaccess还是无济于事。

在Google上好一阵搜索后，终于找到解决办法。原来是我服务器上并没有启用重写模式（mod_rewrite），而且没有在httpd.conf中启用固定链接。<!--more-->
<blockquote>科普一下，什么是固定链接：

缺省情况下，wordpress用内部的路径参数生成URL，这样的结果就是URL看起来象是："http://www.example.com/?q=news/83."。这使得很多搜索引擎，比如google，在索引这些页面时被挡在门外。你可以告诉Drupal使用“固定链接”，以去掉内部链接中的“?q=”。注意，这只能在加载了重写模块（rewrite_module）并且在配置中启用重写模式（mod_rewrite）的apache服务器上能正常工作。</blockquote>
<span style="background-color: #f8f8f8;">解决办法分三步：</span>
<ol>
	<li>启用Apache的重写模式。
请咨询主机服务商或查询<a href="http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html">Apache 文件</a>以了解有关重写模式和如何操作。最少，要确认你的Apache安装中启动了重写模式。它应该被编译进（apache）或被做成可加载的模块。一句话，你可通过在apache的配置文件中引用下面的代码来告诉Apache加载重写模块。
也就是在httpd.conf文件中删除第116行左右如下代码前面的注释符“#”
<blockquote>#LoadModule rewrite_module modules/mod_rewrite.so</blockquote>
</li>
	<li>编辑站点的Apache配置文件httpd.conf
开启apache服务器的AllowOverride，如果httpd.config的AllowOverride设置的是None，那.htaccess将被忽略。
<blockquote>&lt;Directory /&gt;
Options FollowSymLinks
AllowOverride All
&lt;/Directory&gt;</blockquote>
</li>
	<li>在DocumentRoot打开AllowOverride
<blockquote>&lt;Directory /var/www/html&gt;
# ... other directives...
AllowOverride All
&lt;/Directory&gt;</blockquote>
</li>
</ol>
最后，也是最重要的——重启apache，让apache重新载入配置文件。

Tips: 如果您在使用Drupal过程中不能开启“简洁链接”，可以按照同样的办法解决。

大功告成，吼吼~