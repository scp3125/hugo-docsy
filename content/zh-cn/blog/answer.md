hugo-docsy/content/zh-cn/blog/_index.md 这个导航直接链接到另外一个博客网址 https://blog.coolshell.in/

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