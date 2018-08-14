---
layout: post
title: springboot 开发项目中集成文件上传,Excel导入导出,oss对象存储
date: 2018-08-14 17:46:32
categories:
- springboot
tags:
- java
- springboot
description: springboot 项目中文件上传, 使用 Apache poi 和 Apache poi-ooxml 实现 Excel 文档的导入与导出,同样会介绍两种对象存储的使用:1)使用阿里云的对象存储.2)使用七牛云的对象存储.
---
# springboot 开发项目中文件相关操作

## 文件上传
## 文件下载
## Excel 导入与导出

### 引言
Java 中使用 POI 是常用的一种操作 excel 的工具库. 在 office 中, excel 分为 2003 和 2007 两种不同的格式, 通常情况下通过 xls/xlsx 不同的后缀来区分(不是绝对的)
<br> 为了支持 2007 之后的 excel 的操作, 需要使用 poi-ooxml 包.
```
HSSF － 提供读写Microsoft Excel格式档案的功能。
XSSF － 提供读写Microsoft Excel OOXML格式档案的功能。
```
### Excel 导入
读取 excel 可以使用 WorkbookFactory 来创建.

> Workbook workbook = WorkbookFactory.create(file.getInputStream());

### Excel 导出


## 使用阿里云的对象存储功能

## 使用七牛云的对象存储功能


**示例与源码: []()**
**未完待续...**