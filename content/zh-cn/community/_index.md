---
title: 社区
menu: {main: {weight: 40}}
type: new_community

# Add blocks of content here to add more sections to the community page
---

这个文件比较奇怪，前端页面有内容，但是打开这个文件，却看不到正文内容，应该在哪里修改呢？

- 这个页面的内容在哪里修改？搜索“Goldydocs community”，没找到文件，请指出来在哪份文件中，我自己修改吧。似乎中文版是自动翻译的吧，我没有改它。
https://hugo-docsy.pages.dev/community/

A：也是i18n文件夹下zh-cn.toml中改，逻辑和搜索框那个一样

- 这个页面、首页和about页面中 ../zh-cn/about/ 的中间大块颜色背景的block 是通过以下这些代码控制的吗？
  
A：这个得自己修改主题模板了，创建html文件，示例在layouts/community下面，需要修改html文件改样式

但是这个community页面中的block在哪个文件中控制呢？

- about, index 等网页背景图片，是否可以用外链到google drive中的图片？而不是将图片也和网页文件一起存放到源码库中。

A:可以改，图片语法参考https://www.docsy.dev/docs/adding-content/shortcodes/#blockscover
google drive之类的网盘不清楚，正常没有反盗机制的图片是可以的