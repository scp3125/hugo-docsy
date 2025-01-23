---
title: 社区
menu: {main: {weight: 40}}
# Add blocks of content here to add more sections to the community page
---

问题：

这个文件比较奇怪，前端页面有内容，但是打开这个文件，却看不到正文内容，应该在哪里修改呢？

- 这个页面的内容在哪里修改？搜索“Goldydocs community”，没找到文件，请指出来在哪份文件中，我自己修改吧。似乎中文版是自动翻译的吧，我没有改它。
https://hugo-docsy.pages.dev/community/


- 这个页面、首页和about页面中 ../zh-cn/about/ 的中间大块颜色背景的block 是通过以下这些代码控制的吗？
```
{.text-center}

{{% /blocks/section %}}

{{% blocks/section %}}

```
但是这个community页面中的block在哪个文件中控制呢？
