---
layout: post
title: "简明Vim使用命令"
date: 2014-02-19 14:16:18 +0800
comments: true
categories: linux shell 
---
<article>
一直在使用vim编辑，但是感觉玩的不溜，现记录一些常用的命令和Vim知识。
<!-- more -->
<h2>各种插入命令</h2>
i --> 进入插入模式<br>
o --> 在当前光标的下一行插入<br>
O --> 在当前光标的上一行插入<br>
cw --> 替换从当前光标开始到单词结尾
<h2>移动光标命令</h2>
0 --> 到行头<br>
$ --> 到行尾<br>
gg --> 到文档头<br>
G --> 到文档尾 <br>
Ng -->到文档第N行<br>
<h2>其他命令</h2>
<ctrl+r> --> redo <br>
u --> undo<br>
N<command> --> 重复N次命令<br>
. --> 重复上次命令<br>
<h2>visual模式</h2>
v --> 单字符选取<br>
V --> 每次选取一行<br>
<ctrl+v> --> 矩形块方式选取<br>
</article>
