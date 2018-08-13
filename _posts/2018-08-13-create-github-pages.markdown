---
layout: post
title: 创建github pages
date: 2018-08-13 13:40:22
categories: Other
tags: Other
description: github + jekyll + markdown 搭建自己的博客页面
---

# 在 github 上搭建自己的博客

## 创建项目
首先注册一个 github 账号,这是肯定的嘛, 因为我们就是要在 github 中搭建静态博客,
然后我们创建一个项目,名称就是账号+github.io (zhangkangen.github.io).

## 导入 jekyll 模板

* 下载模板
    
    进入[jekyll 模板网页模板](http://jekyllthemes.org/)选择自己喜欢的模板下载.<br>
    我使用的模板: [jekyll-jacman](https://github.com/Simpleyyt/jekyll-jacman), 详细的配置可以点击链接查看.<br>
    将下载的模板解压后的文件放到项目库中.
    
* 配置<br>
在 _config.yml 中为博客的主要配置, 包括博客名称,logo,显示样式,个人信息的配置..eg.

## 发表文章
* 在 _posts 目录下创建 .md 结尾的文件,文件名称以时间日期开始.例如:2018-08-13-create-github-pages.md <br>
   打开文件,开头加入如下内容. 
```
    ---
    layout: post
    title: 创建github pages
    date: 2018-08-13 14:07:13
    categories: Other
    tags: Other
    author: zhangkangen
    description: 创建自己的github pages.
    ---
``` 
title:文章的标题 <br>
date: 创建时间<br>
categories:文章的分类<br>
tags:文章的标签<br>
author:作者<br>
description:文章简要描述<br>

* push 更改到 github

## 访问
博客的地址是 github.io 前加上个人账号这样的一个二级域名<br>
我的博客地址是: [https://zhangkangen.github.io](https://zhangkangen.github.io)
