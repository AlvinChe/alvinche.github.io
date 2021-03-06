---
title: hexo使用过中遇到的一个小问题
date: 2019-03-14 14:59:34
tags: hexo
categories: 博客
---

##### 问题描述

新博客搭建不久，突然`hexo g`报错，

<!--more-->

```
$ hexo g
(node:14620) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  [hexo-math] Using engine 'mathjax'
INFO  Start processing
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Template render error: (unknown path) [Line 12, Column 47]
  expected variable end
    at Object._prettifyError (D:\hexo\node_modules\nunjucks\src\lib.js:36:11)
    at Template.render (D:\hexo\node_modules\nunjucks\src\environment.js:542:21)
    at Environment.renderString (D:\hexo\node_modules\nunjucks\src\environment.js:380:17)
    at Promise.fromCallback.cb (D:\hexo\node_modules\hexo\lib\extend\tag.js:62:48)
    at tryCatcher (D:\hexo\node_modules\bluebird\js\release\util.js:16:23)
    at Function.Promise.fromNode.Promise.fromCallback (D:\hexo\node_modules\bluebird\js\release\promise.js:180:30)

```



删除新写的文章之后，问题消失了，

仔细检查发现文章中公式里出现了两个连续的中括号“{   {”，导致了异常

##### 解决方案

用空格给隔开就好了

