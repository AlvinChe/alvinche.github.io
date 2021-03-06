---
title: 搭建hexo博客
date: 2019-03-13 13:52:00
tags: 
- hexo
- 搭建环境
categories: 博客
toc: true
---
---
```
动机：看到别人有，羡慕，觉得好玩，实践了一下，前后大概两小时
```
---


<!--more-->

####  相关软件安装

> Git
>
> Node.js
>
> Hexo

 

#### Hexo 环境配置

 ###### 1.Hexo主题

  选一个自己喜欢的主题，我这里直接用了教程里的nexT，后面遇到喜欢的再改吧
  [Github 主页](https://github.com/theme-next/hexo-theme-next)

  ```shell
$ cd hexo
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
  ```


###### 2.初始化博客

 选一个空白的不需要管理员权限的文件夹，打开git bash，在终端输入下面的代码，初始化博客

  ```shell
  #建立一个博客文件夹，并初始化博客，<folder>为文件夹的名称，可以随便起名字
  $ hexo init <folder>
  #进入博客文件夹，<folder>为文件夹的名称
  $ cd <folder>
  # node.js的命令，根据博客既定的dependencies配置安装所有的依赖包
  $ npm install
  ```

  

###### 3.基本配置

  比如博客名，个人介绍呀，参考了这篇文章[简书:Hexo的Next主题详细配置](https://www.jianshu.com/p/3a05351a37dc)

  1.站点计数

   可以直接在配置里将busuanzi的false改成true，参考[文档](https://www.jianshu.com/p/c311d31265e0)


2.配置在线后台管理

  hexo 有个插件可以在网页上对博客进行管理，但是我觉得使用起来并不流流畅，还不如使用本地markdown工具[Typora](https://typora.io/)，不过配不配和用不用又没什么直接关系。

3.Hexo-admin

    `$ nmp i hexo-admin --save`

  这个时候，登录 <http://localhost:4000/admin> 即可查看所有文章内容，并可视化进行修改。

  还可以添加配置后台账号密码，我没设置，哈哈。

4.通过域名访问博客

绑到了GitHub.io，具体教程可以看这里[GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)
不绑域名是因为买过，然后没怎么用就忘掉了。
有机会再绑自己的域名吧

5.添加评论(2019年3月14添加)

也是超级方便几行代码，详细参考这个[为你的Hexo加上评论系统-Valine](https://blog.csdn.net/blue_zy/article/details/79071414)

有个小bug就是，在添加appid和appkey的时候，记得删除leancloud占位符



6.给博客添加豆瓣插件

参考[这里](https://github.com/mythsman/hexo-douban)

看到人家博客还有豆瓣读书什么的，给自己也加了一个，但是好像得时长更新一下。

###### 4.小问题
	busuanzi计数问题（未解决,本地依旧不太对,添加leancloud试试）
	主题语言设定问题，中文要使用 zh-CN
	无需列表换行问题（未解决，可能是不同平台的问题）
	数学公式无法渲染（未解决，19.3.25号了，还是解决不了，以后用图片吧 3月27号，改好了，原来是我没有找对开关，[捂脸]）