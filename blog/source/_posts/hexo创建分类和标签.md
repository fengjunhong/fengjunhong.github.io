---
layout: hexo
title: hexo创建分类和标签
date: 2019-11-27 09:42:29
categories: hexo
tags:
---

> **1、修改主题配置文件**
> 路径：blog \ themes \ next \ _config.yml
```javascript
menu:
  home: /
  #about: /about/ || user
  #tags: /tags/ || tags
  categories: /categories/
  archives: /archives/ || archive
  tags: /tags/
```
<!--more-->
> **2、创建文件categories和tags文件**
> 

```js
hexo new page categories   # 创建分类文件
hexo new page tags         # 创建标签文件
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191127100210425.png)
> **3、修改categories/index.md和tags/index.md文件**

categories/index.md的文件内容如下：
```javascript
---
title: 分类
date: 2019-11-26 17:14:17
type: "categories"
---
```
tags/index.md的文件内容如下：
```javascript
---
title: 标签
date: 2019-11-26 17:14:17
type: "tags"
---
```

>  **4、修改source / _posts / musci.md 文章内容**

```javascript
title: 薛之谦-演员
top: 
    true
categories: 娱乐
tags:
    - 歌曲
```

> **5、实现效果**
> 
![文章分类](https://img-blog.csdnimg.cn/20191127102146585.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
![标签](https://img-blog.csdnimg.cn/20191127102454976.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)