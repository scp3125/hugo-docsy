---
title: Github action workflow 错误报告
description: >
  我们将源库中带有.github/目录的文件传到测试库中，发现部署错误。
date: 2017-01-05
weight: 4
---

测试库 https://coolshell-in.github.io/hugo-docsy/


在github pages页面中，设置“Build and deployment Source” 为“Github Actions”，然后运行workflow，发现失败，详细报告如下：

A:1、进入仓库中settings中的Actions下的General,将Workflow permissions修改为Read and write permissions
2、进入settings中的Pages下，将Source修改为gh-pages分支，目录为/(root)
然后再次部署

Annotations
1 error

deploy

Action failed with "The process '/usr/bin/git' failed with exit code 128"


# Deploy

##[debug]Evaluating condition for step: 'Deploy'
2
##[debug]Evaluating: (success() && (github.ref == 'refs/heads/main'))
3
##[debug]Evaluating And:
4
##[debug]..Evaluating success:
5
##[debug]..=> true
6
##[debug]..Evaluating Equal:
7
##[debug]....Evaluating Index:
8
##[debug]......Evaluating github:
9
##[debug]......=> Object
10
##[debug]......Evaluating String:
11
##[debug]......=> 'ref'
12
##[debug]....=> 'refs/heads/main'
13
##[debug]....Evaluating String:
14
##[debug]....=> 'refs/heads/main'
15
##[debug]..=> true
16
##[debug]=> true
17
##[debug]Expanded: (true && ('refs/heads/main' == 'refs/heads/main'))
18
##[debug]Result: true
19
##[debug]Starting: Deploy
20
##[debug]Loading inputs
21
##[debug]Evaluating: secrets.GITHUB_TOKEN
22
##[debug]Evaluating Index:
23
##[debug]..Evaluating secrets:
24
##[debug]..=> Object
25
##[debug]..Evaluating String:
26
##[debug]..=> 'GITHUB_TOKEN'
27
##[debug]=> '***'
28
##[debug]Result: '***'
29
##[debug]Loading env
30
Run peaceiris/actions-gh-pages@v4
44
[INFO] Usage https://github.com/peaceiris/actions-gh-pages#readme
45
::group::Dump inputs
46
Dump inputs
66
::group::Debug: dump context
67
Debug: dump context
230
::group::Setup auth token
231
Setup auth token
237
::group::Prepare publishing assets
238
Prepare publishing assets
280
::group::Setup Git config
281
Setup Git config
290
::group::Create a commit
291
Create a commit
584
::group::Push the commit or tag
585
Push the commit or tag