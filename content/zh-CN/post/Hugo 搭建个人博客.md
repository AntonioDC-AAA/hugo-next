+++
title = "Hugo 搭建个人博客"
description = "Hugo搭建个人博客"
date = "2022-03-20"
author = "Antonio.DC"
tags = [
    "开源小项目",
]
categories = [
    "Hugo",
]

series=["Hugo"]

toc = true

+++



# Hugo 搭建个人博客

**【摘要】** 工作以来一直想写点东西，本来想继续用之前的博客来，未曾想到离校之后github访问一直失败，搞定了访问失败后又发生了一些事情，转而想干脆用gitee，Github就当一个学习的平台，有了这个想法后就开始搭建Hugo博客，之前在github上搭建过，基本的步骤是懂得的，但是之前的主题太简陋了，想找一个好看的主题搞一下，本文主要讲解如何搭建个人博客如何实现功能，下篇博客讲解一下主题改造及应用。

**[Hugo官方网站](https://gohugo.io/)**

## 一、准备

### 1. 软件及工具下载

Hugo是以go语言编写的静态网页框架，使用的是go语言template这个库，如果想深入研究下可阅读相关材料，在搭建个人博客前，需要下载一些软件和工具

- Git     --> [下载地址](https://git-scm.com/downloads)
- Go     --> [下载地址](https://golang.google.cn/dl/)  （版本1.11以上）
- Hugo --> [下载地址](https://github.com/gohugoio/hugo/releases)

安装完成后检查环境变量是否配置完成

```shell
git version
go  version
hugo version
```

hugo在[下载地址](https://github.com/gohugoio/hugo/releases)下载的是releases版本，切记要配置环境变量

### 2. 创建Gitee账号

​	Gitee的相关操作，请看[Gitee帮助中心](https://gitee.com/help/articles/4114#article-header0)



## 二、命令

参考资料：[Hugo快速开始](https://gohugo.io/getting-started/quick-start/)

### 1. 创建博客

```
hugo new site blogName
cd blogName
ls
```

### 2. 选择主题

在theme目录下添加要加入的主题

[主题列表](https://www.gohugo.org/theme/)

```
cd theme
git clone git@gitee.com:antonio-dc/hugo-theme-next.git
```

下载完成后，把exampleSite目录下的`config`和`content`目录复制到 `blogName`下面。

### 3. 编写文章

创建文章是hugo new post/test.md

可以发现在content\zh-CN\post目录下创建test.md，随后进行内容编写

### 4. 启动本地服务器查看效果

hugo server -D

这里-D的意思是-Draft，在文档中Draft=false的也能正常显示

## 三、部署到Gitee

在Gitee上创建仓库，这个地方跟github 有区别，在Gitee上配置 Git page的话需要手动部署，并且需要特别注意BaseUrl的配置

```
BaseUrl = "https://antonio-dc.gitee.io/"
```

​            ![image-20220322221855701](/blogMaties/image-20220322221855701.png)                                       

![image-20220322221924569](/blogMaties/image-20220322221924569.png)



在blogName目录下运行

hugo -t hugo-theme-next -D

发现在public目录下生成文档



【注意】

1. 每次上传文件时删除Public目录下的文件

2. 运行的git指令为
   ```shell
   cd public
   git init
   git remote add origin https://gitee.com/antonio-dc/antonio-dc.git
   git add .
   git commit -m "提交博客"
   git push origin "master"
   ```

3. 每次代码有更新需要在gitee上重新部署

