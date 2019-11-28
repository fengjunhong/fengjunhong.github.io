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

![img](https://pic4.zhimg.com/50/v2-832168e58b4ac4ce7c3cca797711d2d3_hd.jpg)

什么是Git ?简单来说Git是开源的分布式版本控制系统，用于敏捷高效地处理项目。我们网站在本地搭建好了，需要使用Git同步到GitHub上。如果想要了解Git的细节，参看[廖雪峰](http://link.zhihu.com/?target=http%3A//weibo.com/liaoxuefeng)老师的Git教程：[Git教程](http://link.zhihu.com/?target=http%3A//www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 从Git官网下载：[Git - Downloading Package](http://link.zhihu.com/?target=https%3A//git-scm.com/download/win) 现在的机子基本都是64位的，选择64位的安装包，下载后安装，在命令行里输入git测试是否安装成功，若安装失败，参看其他详细的Git安装教程。安装成功后，将你的Git与GitHub帐号绑定，鼠标右击打开Git Bash

 

![img](https://pic3.zhimg.com/50/v2-8b1cbe253d6e0301bd9a68c6f98a9f52_hd.jpg)

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

![img](https://pic3.zhimg.com/50/v2-d1e47103ec1aa8675f68688c5d63bd27_hd.jpg)

 

![img](https://pic3.zhimg.com/50/v2-72a3f22c080e99343c3cc4aabce10e3c_hd.jpg)

 

![img](https://pic2.zhimg.com/50/v2-da481ffa686410becd4186c656b4ebd6_hd.jpg)

 

**安装Node.js**

Hexo基于Node.js，Node.js下载地址：[Download | Node.js](http://link.zhihu.com/?target=https%3A//nodejs.org/en/download/) 下载安装包，注意安装Node.js会包含环境变量及npm的安装，安装后，检测Node.js是否安装成功，在命令行中输入 node -v :

 

![img](https://pic3.zhimg.com/50/v2-76ea38e9545e606f975781e47933b010_hd.jpg)

 

![img](https://pic3.zhimg.com/50/v2-bede250b8456df92475b455fda8c1dd9_hd.jpg)

 

**安装Hexo**

Hexo就是我们的个人博客网站的框架， 这里需要自己在电脑常里创建一个文件夹，可以命名为MyBlog，Hexo框架与以后你自己发布的网页都在这个文件夹中。创建好后，进入文件夹中，按住shift键，右击鼠标点击命令行

![img](https://pic4.zhimg.com/50/v2-a5450a466c0927c25dff8ad6f1d2046c_hd.jpg)

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

