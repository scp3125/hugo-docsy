---
title: 课程
menu: {main: {weight: 30}}
type: blog
---


<br><br><br>
&nbsp;&nbsp;&nbsp;&nbsp;


这是 **课程** 部分。它有两个类别：新闻和发布。

这些目录中的文件将按时间倒序列出。

問題：

- hugo-docsy/content/zh-cn/courses/_index.md 将原blog 目录改为courses 后，其中的文章消失不见了；

加一个type: blog 就好了，因为如果文件夹是blog,默认就是blog类型的，如果是其他类型的，需要加上type: blog
