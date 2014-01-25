---
layout: post
title: "在 Mac OS中使用 beyond compare"
date: 2014-01-26 00:58
comments: true
categories: 
---

[Beyond Compare](http://www.scootersoftware.com/) 是一款强大的文件比较(diff)软件，通过它我们可以比较两个目录、两个文件、两个文本之间的差别。但是在 Beyond Compare 的官网只提供 windows 和 Linux 版本下载，一度让我以为它不支持 Mac 平台，以至于在 Mac 上通过 wine 来间接使用它。前段时间 Scooter 公司在千呼万唤中发布了 Beyond Compare 的 Mac beta 版，完成了 Windows、Linux和Mac平台的全覆盖。如果你是 Mac 用户，而且又是 git 的重度使用者，为何不尝试一下呢？

下载 Mac 版的 Beyond Compare
============================

由上文得知，Beyond Compare在下载页面是没有显示的，只有通过其官网的支持页面下载。下载地址：<http://www.scootersoftware.com/support.php?zz=kb_mac>。将解压后的 Beyond Compare 拖动到“程序”文件夹中安装。

安装 Beyond Compare 后，下一步就是安装它的命令行工具。打开 Beyond Compare 后，在"Beyond Compare"的下拉菜单中选择"Install Command Line Tools"，在弹出框中输入系统密码后，会自动将它的命令行工具安装到系统中。安装完命令行工具后，就可以在终端中输入 `bcomp a.txt b.txt` 来比较文件了。下面的步骤都是基于它的命令行工具进行的。

在 Git CLI 中使用
============================

安装完 Beyond Compare 的下一步就是设置其为 Git 的 diff tool 和 merge tool。在终端中输入如下几条命令：

``` bash
git config --global diff.tool bc3
git config --global difftool.prompt false
git config --global merge.tool bc3
```

这几条语句的作用是，当你在 Git 中使用 `git diff` 和 `git merge` 命令时，Git 会自动调用刚才的命令行工具来打开 Bycompare 来比较文件。

在 Tower 中使用
============================

1. 退出 Tower 工具
2. 在终端中 ` cd ~/Library/Application\ Support/Tower`
3. 如果不存在 CompareScripts 文件夹，就使用 `mkdir CompareScripts` 来生成一个文件夹
4. 下载 [bcomp.sh](http://jdon.at/3tWV) 并放在上面的 CompareScripts 文件夹中
5. 使用 `chmod +x bcomp.sh` 命令赋予其可执行权限
6. 下载 [CompareToools.plist](http://jdon.at/J4cR) 到 ~/Library/Application\ Support/Tower 文件夹下
7. 启动 Tower

在 SourceTree 中使用
===========================

1. 打开 SourceTree
2. 在 SourceTree 的菜单中选择 "Performance"
3. 在顶部的菜单栏中选择 "diff" 选项卡
4. 在 "External Diff / Merge" 里
    - 如果是 "Visual Diff Tool"，选择 "Other"，在 "diff commend" 中输入 "/usr/local/bin/bcomp"，在 "arguments" 中输入 "$LOCAL $REMOTE"
    - 如果是 "Merge Tool"，选择 "Other"，在 "Merge Commend" 中输入 "/usr/local/bin/bcomp"，在 "arguments" 中输入 "$LOCAL $REMOTE $BASE $MERGED"


