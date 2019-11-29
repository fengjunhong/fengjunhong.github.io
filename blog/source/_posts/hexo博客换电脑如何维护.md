---
title: hexo博客换电脑如何维护
date: 2019-11-29 11:16:19
tags:
categories: hexo
---
**前言**：我们使用hexo+github搭建的博客，源代码文件都在本地，如果我们电脑出现问题或者其他情况，需要换电脑维护博客，该怎么办？

## 方式一 拷贝文件
把你本地的源代码，拷贝到其他电脑，安装必须的环境，即可。

## 方式二 借助github实现多终端维护博客

### 在github上创建分支

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129112553846.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
### 上传源代码
把新建的分支克隆至本地，只保留.git，其他全部删除，将hexo源代码拷贝至此，我直接将整个文件夹放到这里了,然后重新上传代码，设置分支为hexo_blog
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129114412442.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129114819425.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)

### 查看源代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129114032148.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)

### 本地启动
现在你可以在当前文件夹下，打开power shell
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129113459883.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
本地启动成功，然后修改你的博客，即可
### 同步至github
```javascript
hexo clean  # 清理缓存
hexo g -d   # 生成并发布
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129115346713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
此时可以看到我们前面修改的代码已经提交至master分支了，使用你自己的github来访问就可以了，[我的博客](https://fengjunhong.github.io/)
### 提交源代码
前面我们只是更新了master分支的数据
更新源代码：借助GitHub Desktop上传源代码至hexo_blog分支即可。
### 总结
其实就是master分支存储显示文件，hexo_blog分支存储源代码文件