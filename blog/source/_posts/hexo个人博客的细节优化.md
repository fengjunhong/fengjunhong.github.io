---
title: hexo个人博客的细节优化
date: 2019-11-27 16:27:12
categories: hexo
tags:
---
> **1、添加分享功能**

找到主题配置文件（\themes \ next \ _config.yml）,如下修改即可
```javascript
baidushare: 
  type: button
  baidushare: true
```
<!--more-->
> **2、修改文章间距**
> 
找到 \themes \ next \ source \ css \ _custom \ _custom.styl
```javascript
.post {
   margin-top: 0px;    # 上外边距
   margin-bottom: 60px;  # 下外边距
   padding: 25px;
   -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
   -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
}
```
Next官网：[Next官网链接](http://theme-next.iissnan.com/theme-settings.html#syntax-highlight-scheme)