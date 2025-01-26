---
title: Hugo - Docsy
description: > 
    如何做主题配置，并增加内容?
date: 2025-01-24
---

本项目采纳主题[Hugo-Docsy](https://www.docsy.dev/)

[测试网页](https://scp3125.github.io/hugo-docsy/zh-cn/)

[测试库](https://github.com/scp3125/hugo-docsy)


# 安装方式
目前本主题的安装方式是怎样的？例如远程主题、gem-based，或还有其他方式。为何在本站根目录中没有发现hugo建站相关的程序文件和theme 目录？

我们寻找Hugo的配置文件的位置，为了查找静态页面所保存的文件目录```publishDir=public```的配置，可能有几个文件与该配置相关：

```sh
config/_default/config.toml
config/_default/config.yaml
config/_default/config.json
config/production/config.toml
config/production/config.yaml
config/production/config.json
```

如果不采用docker方法安装，需要删除docker相关文件吧，包括哪些文件清单？


# 整站页面配置

这个页面./community/ 的内容在哪里修改？前端页面有内容，但是打开这个文件，却看不到正文内容，搜索“Goldydocs community”，没找到文件。

A：逻辑和搜索框一样，在i18n文件夹下zh-cn.toml 配置覆盖，所有的语言配置在https://github.com/google/docsy/tree/main/i18n



##  修改主题模板
  
这个页面、首页和about页面中 ./content/zh-cn/about/ 的中间大块颜色背景的block 是通过以下这些代码控制的吗？但是这个community页面中的block在哪个文件中控制呢？
  
A：这个得自己修改主题模板了，创建html文件，示例在layouts/community下面，需要修改html文件改样式



### 背景图片外链

about, index 等网页背景图片，是否可以用外链到google drive中的图片？而不是将图片也和网页文件一起存放到源码库中。

A:可以改，图片语法参考https://www.docsy.dev/docs/adding-content/shortcodes/#blockscover, google drive之类的网盘不清楚，正常没有反盗机制的图片是可以的

# 导航网址外链
  
例如hugo-docsy/content/zh-cn/blog/_index.md 这个导航直接链接到另外一个博客网址 https://blog.coolshell.in/

不在本站中写博客。

A：删掉blog文件夹，在hugo.yaml中，各个语言下，添加合适的配置，比如：

  zh-Cn:
    languageName: 中文简体
    contentDir: content/zh-cn
    title: 酷壳众创
    params:
      description: 左耳朵耗子的酷壳下一代众创版
    menu:
      main:
        - name: 博客
          weight: 50
          url:  "https://blog.coolshell.in"


# 文件目录和内容类型

- 将原blog 目录./content/zh-cn/blog/ 改为courses 后，其中的文章消失不见了；

A：加一个type: blog 就好了，因为如果文件夹是blog, 默认就是blog类型的，如果是其他类型的，需要加上type: blog

- 参考./content/zh-cn/docs/，打开任何一个页面，左右两侧边栏的目录导航菜单和tag，catelogies都保留的。<p style="color: red;">但是，如果不给头信息中增加“type: blog”，那么./content/zh-cn/courses/ 中的文章页面的左右两侧边栏的目录都消失了，docs/如何做到没有增加内容类型，却可以保留侧边栏的目录呢？</p>

A:因为官方提供了几个默认模板，包含doc、blog、community等，如果你的文件夹名字和模板名字一样，就会默认使用这个模板，如果不一样，就需要在md文件中加上type: blog，这样就会使用blog模板

我们给这个文章./content/zh-cn/courses/releases/_index.md 的头信息中增加了
```sh 
  cascade:  
      type: "blog"
```
因此唯独这篇文章可以显示两边的侧边栏导航菜单，同样在./content/zh-cn/courses/目录下的其他任何文章没有增加“cascade”，它们每一篇文章页面都缺少了侧边栏。当然我们希望，尽量少给每篇文章都做配置，批量给某一个目录下文章都赋予相同的页面样式结构。


A1:可以使用如下格式： 
```sh 
  cascade:  
      type: "blog"
```
cascade可以让你在一个文件夹下的所有文件都使用该配置，不需要每个文件都写一遍
如果只是用
```sh
 type: "docs" 
```
那么只有这个文件会使用这个配置，其他文件不会使用.

系统默认的原 docs和blog目录中文章内容类型是什么？在哪里定义docs和blog这种保留左右侧边栏目录的页面样式呢？我们复制了 docs/ 目录，并命名为 study/, 中文命名“学习”，但是其中的文章没有类似docs/页面那样的左右侧边栏。

A:文章类型就是docs或者blog，定义如上面的A1回答，我这边是能看到左右侧边栏的。

目前每篇文章又侧边栏的文章目录仅仅显示2-3级标题，无法显示1级标题，在哪个文章中配置更改我们想要显示的标题级数呢？例如这个页面中，我们仅仅有1级标题，因此无法在右侧边栏显示目录。

A: 修改hugo.yaml中的如下配置：
markup:
  tableOfContents:
    endLevel: 3
    ordered: false
    startLevel: 1
可以更改endLevel和startLevel的值，来显示不同级别的标题，这个是全局配置，没有页面级别的配置

# 导航单页面

尝试在导航栏中创建一个单页面，要求其他语言版本中也都要有。

bug：前端页面显示，头信息和正文之间没有空格，而且第一个#标题丢失了 ？

A: 标题并未丢失，因为样式中却发空行，导致被隐藏，markdown语法加空格和空行可以使用 

```sh
<br><br><br> &nbsp;&nbsp;&nbsp;&nbsp;
```


# 导航语言切换

中文内容在目录zh中，但是导航上没有中文语言切换项。

A:修改配置文件，语言。



# 文档页面上github链接

- 如何去除页面右上方的github库相关信息？这些是多余的内容，具体如下：

- View page source
- Edit this page
- Create child page
- Create documentation issue
- Create project issue
- Print entire section

A：修改配置解决了

**如果我要把以上github連結内容在某些页面中再加回来？应该如何操作？它是批量增加到某一个类的文档中吗？例如在docs中增加，但是我可以在blog中将其去除？**

A: 可以在md中，添加配置，例如该文件上面的，cascade中的内容，可以参考这个配置，这个配置是针对单个文件的，如果要批量增加到某一个类的文档中，可以在该类的_index.md中添加配置

# 增加blog 或docs页面中的文章分类

在blog下增加一个分类 business，中文/英文版本中都有该分类。 

A：目录下需要有_index.md文件，填好里面的内容就能显示
 
源库中目录分类例如：
/blog/news/ 分类目录名为 news，/blog/releases/ 分类目录名为 releases

/docs/tutorials/ 分类目录名为 tutorials， /docs/tasks/ponycopters/ 有2-3级目录，分类目录名为 tasks/和 ponycopters/，ponycopters/目录中才是文章。

A:这个按照当前的文件夹结构就行，不需要额外的配置，如果某一层不想有文章，该文件夹下不需要有md文件就行，但是需要有_index.md文件。

