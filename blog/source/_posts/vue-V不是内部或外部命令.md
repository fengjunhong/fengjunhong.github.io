
---
title: vue -V不是内部或外部命令
date: 2019-12-02 22:35:50
tags: vue
categories:
	- 常见问题
---
vue -V 不是内部或外部命令，也不是可运行的程序或批处理文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191202223924116.png)
那么面对此问题，该如何解决呢？

全局搜索**vue.cmd**，打开文件所在位置，将**vue.cmd**所在的**路径**添加到环境变量Path中，重新打开控制台，再次执行vue -V.即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191202224024582.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)