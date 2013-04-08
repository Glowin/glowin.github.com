---
layout: post
title: "tcexam在线考试系统csv文件转换为xml文件"
date: 2011-11-19 21:09
comments: true
categories: tech
---
<span class="Apple-style-span" style="color: #333333; font-weight: 300;">tcexam是一个非常优秀的在线考试系统，将纸笔考试转化为在计算机上在线完成，只要有计算机和网络就可以考试，大大简化了整个考试流程，将出题、考试、管理阅卷登常规过程一并纳入一个系统中，不仅减少了人力，而且极大的提高了整个效率和考试结果的可信度。Glow认为最大的收益方为组织考试的老师，它让老师免去了试卷排版和编排的工作，将更多的时间放在了出题的质量上，而且只需要提交 csv 格式或者 xml 格式的考试试题设置相关考试要求，其他的工作比如判卷就可以交与服务器完成，特别是当题目大多数为选择题时效果最明显。（TCExam的主页和下载页面为</span><a style="font-weight: 300;" href="http://www.tcexam.org/" target="_blank">这个</a><span class="Apple-style-span" style="color: #333333; font-weight: 300;">）</span>
<h1> 为什么要把 csv 转换成 xml</h1>
TCExam 考试系统默认只能导入xml格式的考试试题，但是我们老师给的考试试题确实从Excel 转换后的 csv 格式。只有通过修改考试系统的源代码来让TCExam考试系统支持csv 格式的试题导入。这里 Glow 采用曲线救国的方法，将 csv 格式的试题先转换成xml，然后由老师手动导入到考试系统。下面是老师提供的 csv 格式的部分试题。<!--more-->
<pre>CSVInsert,标题(1),类型(2),解答(3),答案(4),分值(5),答错扣分(可选项)(6),分级level(7),Tag(8),留空列(9),留空列(10),选项A(11),选项B(12),选项C(13)…,选项D(14),选项E(15)
1,车床的种类很多，其中应用最广的是(  )。,1,,12,,,1,,,,立式车床,卧式车床,仪表车床,转塔车床,
2,目前最常用的车刀材料是为（  ）。,1,,12,,,2,,,,硬质合金和碳素钢,硬质合金和高速钢,碳素钢和高速钢,硬质合金和45号钢,

60,车削加工的切削用量三要素有（  ）。,2,,11，12，13,,,2,,,,切削速度,切削深度     ,进给量,切削宽度,切削厚度
61,在金属切削加工过程中，工件上存在三个不断变化的表面有（  ）。,2,,11，12，14,,,2,,,,已加工表面 ,待加工表面　,端面,过渡表面,内孔

103,车工是使用车床进行切削的工种。,3,,11,,,1,,,,是,,,,
104,车工是使用车床的技术工人。,3,,11,,,1,,,,是,,,,</pre>

csv格式的文件主要是用逗号来分隔文件内容的格式。

TCExam格式的xml文件如下
``` xml
<?xml version=”1.0” encoding=”UTF-8” ?>
<tcexamquestions version=“11.2.004”>
	<header lang=“cn” date=“2011-11-18 08:49:14”></header>
	<body>
		<module>
			<name>车工机考试题</name>
			<enabled>true</enabled>
			<subject>
				<name>单选题</name>
				<description>单选题</description>
				<enabled>true</enabled>
				<question>
				<enabled>true</enabled>
				<type>single</type>
				<difficulty>1</difficulty>
				<position></position>
				<timer>0</timer>
				<fullscreen>false</fullscreen>
				<inline_answers>false</inline_answers>
				<auto_next>false</auto_next>
				<description>车床的种类很多，其中应用最广的是(  )。</description>
				<explanation></explanation>
				<answer>
					<enabled>true</enabled>
					<isright>false</isright>
					<position></position>
					<keyboard_key></keyboard_key>
					<description>立式车床</description>
					<explanation></explanation>
				</answer>
				</question>
		</subject>
	</module>
	</body>
</tcexamquestions>
```
在分析 csv 和 TCExam考试系统的代码后，转换的 php 代码的思路也越来越明晰。首先我们先读取 csv 文件，然后逐行读取它，使用 php 的 explode 函数，将每行文字用英文逗号分隔，输出为数组方便后面的调用。最后输出 TCExam 标准的 xml 文件提供下载。
<h1> 如何给 TCExam 添加 csv 转换成 xml 的功能</h1>
1、在 admin/code/tce_import_xml_questions.php 文件的 97 行左右添加如下的代码，主要是给考试系统添加上传 csv 格式的文件，以及添加考试试题的名称。（复制代码时请把下面中出现的中文引号全部改为英文引号，否则就会报语法错误；另外把tce_import_xml_question.php的编码改成UTF-8无BOM编码）
<div class="source" style="font-family: Consolas, 'Lucida Console', 'Courier New'; color: #000000; background-color: #f9f7ed;"><span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;div class="tceformbox"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;h1&gt;csv转换为xml&lt;/h1&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;form action="transf.php" method="post" enctype="multipart/form-data" id="form_ratingeditor"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;div class="row"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;span class="label"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;label for="file"&gt;csv文件:&lt;/label&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/span&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;span class="formw"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;input type="file" name="file" id="file" /&gt;&lt;br /&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/span&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/div&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;div class="row"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;span class="label"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;label for="module_name"&gt;试题名称:&lt;/label&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/span&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;span class="formw"&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;input type="text" name="module_name" id="module_name" /&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000000;">F_submit_button</span>(<span style="color: #0000ff;">"update"</span><span style="color: #000000;">,</span> <span style="color: #a61717; background-color: #e3d2d2;">上传</span><span style="color: #000000;">,</span> <span style="color: #a61717; background-color: #e3d2d2;">上传</span>);
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/span&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/div&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;br /&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;br /&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/form&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;
<span style="color: #000080; font-weight: bold;">echo</span> <span style="color: #0000ff;">'&lt;/div&gt;&lt;!-- svc转换为xml结束 --&gt;'</span><span style="color: #000000;">.</span><span style="color: #000000;">K_NEWLINE</span>;</div>
<div class="mceTemp" style="text-align: left;"><dl id="attachment_142150" class="wp-caption alignnone" style="width: 474px;"><dt class="wp-caption-dt"><a href="http://glowface.net/2011/11/tcexam-transform-csv-to-xml/tcexam-csv-xml/" rel="attachment wp-att-142150"><img class="size-full wp-image-142150" title="TCExam-csv-xml" src="/static/images/2011/11/TCExam-csv-xml.jpg" alt="" width="464" height="290" /></a></dt><dd class="wp-caption-dd">修改后的页面效果</dd></dl></div>
2、在 TCExam 考试系统的 admin/code 文件夹中添加 transf.php 文件，点击<a href="https://gist.github.com/1378794" target="_blank">这里</a>下载

源代码如下：

<script src="https://gist.github.com/1378794.js?file=transf.php"></script>

3、修改上面的要求后，老师在后台的“模块”→“导入”中上传 csv 格式的试题，填写相关的考试试题名称后，点击提交后系统就会弹出下载的 xml 文件，老师可以直接把此 xml 文件导入到考试系统中。
<h1>题外话</h1>
如果您的 csv 格式的文件内容结构和我的不同的话，可以参考一下我的代码。主要思路就是逐行读取 csv 文件后，输出为TCExam考试系统能够读取的 xml 试题文件。如果你在实际操作中遇到问题，可以在 <a href="http://weibo.com/jiangbian66" target="_blank">新浪微博</a> 、 <a href="https://twitter.com/#!/glow1n" target="_blank">twitter</a> 、 <a href="https://plus.google.com/u/0/117778352719386861792/posts" target="_blank">Google+</a> 上联系我。