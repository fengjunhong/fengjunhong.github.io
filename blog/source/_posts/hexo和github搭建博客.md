---
title: 使用hexo和github搭建个人博客
date: 2019-11-26 09:45:53
categories: hexo
tags:
	- hexo
	- github
---
##### 问题一：

nrm : 无法加载文件 C:\Users\TANG\AppData\Roaming\npm\nrm.ps1，因为在此系统上禁止运行脚本。

###### 处理方式：

 https://www.cnblogs.com/lingblog/p/11845011.html 



### 搭建博客步骤

**GitHub创建个人仓库**

登录到GitHub,如果没有GitHub帐号，使用你的邮箱注册GitHub帐号：[Build software better, together](http://link.zhihu.com/?target=https%3A//github.com/) 点击GitHub中的New repository创建新仓库，仓库名应该为：**用户名**.[http://github.io](http://link.zhihu.com/?target=http%3A//github.io) 这个**用户名**使用你的GitHub帐号名称代替，这是固定写法，比如我的仓库名为：
![github仓库名](https://img-blog.csdnimg.cn/20191128094057439.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)
什么是Git ?简单来说Git是开源的分布式版本控制系统，用于敏捷高效地处理项目。我们网站在本地搭建好了，需要使用Git同步到GitHub上。如果想要了解Git的细节，参看[廖雪峰](http://link.zhihu.com/?target=http%3A//weibo.com/liaoxuefeng)老师的Git教程：[Git教程](http://link.zhihu.com/?target=http%3A//www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 从Git官网下载：[Git - Downloading Package](http://link.zhihu.com/?target=https%3A//git-scm.com/download/win) 现在的机子基本都是64位的，选择64位的安装包，下载后安装，在命令行里输入git测试是否安装成功，若安装失败，参看其他详细的Git安装教程。安装成功后，将你的Git与GitHub帐号绑定，鼠标右击打开Git Bash

 

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMzLnpoaW1nLmNvbS81MC92Mi04YjFjYmUyNTNkNmUwMzAxYmQ5YTY4YzZmOThhOWY1Ml9oZC5qcGc?x-oss-process=image/format,png)

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

生成ssh密钥文件：

```bash
ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```

然后直接三个回车即可，默认不需要设置密码
然后找到生成的.ssh的文件夹中的id_rsa.pub密钥，将内容全部复制
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191128094415435.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5MzM0NQ==,size_16,color_FFFFFF,t_70)

新建SSH密钥
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMzLnpoaW1nLmNvbS81MC92Mi03MmEzZjIyYzA4MGU5OTM0M2MzY2M0YWFiY2UxMGUzY19oZC5qcGc?x-oss-process=image/format,png)


**安装Node.js**

Hexo基于Node.js，Node.js下载地址：[Download | Node.js](http://link.zhihu.com/?target=https%3A//nodejs.org/en/download/) 下载安装包，注意安装Node.js会包含环境变量及npm的安装，安装后，检测Node.js是否安装成功，在命令行中输入 node -v :


![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMzLnpoaW1nLmNvbS81MC92Mi03NmVhMzhlOTU0NWU2MDZmOTc1NzgxZTQ3OTMzYjAxMF9oZC5qcGc?x-oss-process=image/format,png)

 

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMzLnpoaW1nLmNvbS81MC92Mi1iZWRlMjUwYjg0NTZkZjkyNDc1YjQ1NWZkYThjMWRkOV9oZC5qcGc?x-oss-process=image/format,png)

 

**安装Hexo**

Hexo就是我们的个人博客网站的框架， 这里需要自己在电脑常里创建一个文件夹，可以命名为MyBlog，Hexo框架与以后你自己发布的网页都在这个文件夹中。创建好后，进入文件夹中，按住shift键，右击鼠标点击命令行

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWM0LnpoaW1nLmNvbS81MC92Mi1hNTQ1MGE0NjZjMDkyN2MyNWRmZjhhZDZmMWQyMDQ2Y19oZC5qcGc?x-oss-process=image/format,png)

```bash
npm install -g hexo-cli 
```

 这个安装时间较长耐心等待，安装完成后，初始化我们的博客，输入：

```bash
hexo init blog
```

注意，这里的命令都是切换到**blog文件夹**中。

```bash
PS D:\MyProject\MyBlog> cd blog
					  hexo new test_my_site
					  hexo g  # 生成
					  hexo s  # 启动服务
```

这些命令在后面作介绍，完成后，打开浏览器输入地址：

localhost:4000

转载