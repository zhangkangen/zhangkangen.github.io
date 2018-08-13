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


## 导入 jekyll 模板

* 下载模板
    
    进入[jekyll 模板网页模板](http://jekyllthemes.org/)选择自己喜欢的模板下载.<br>
    
* 配置

## 发表文章
* 在 _posts 目录下创建 .markdown 结尾的文件,文件名称以时间日期开始.例如:2018-08-13-create-github-pages.markdown <br>
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
