+++
title = "Git instructions"
date = 2020-02-18T18:02:14+08:00
draft = false
tags = [
   "Git",
]
toc = true
+++

# Git Instructions


## 一、集中式版本控制系统与分布式版本控制系统

### 集中式版本控制系统

有一个包含文件所有修订版本的单一服务器，多个客户端可以从这个中心位置检索出文件

优点：所有人都可以在一定程度上掌握其他人在项目中做了什么，管理员可以精细的掌控每个人的权限，

缺点：集中式服务器带来的单点故障



### 分布式版本控制系统

客户端并非仅仅是检出文件的最新快照，而是对代码仓库进行完整的镜像，不管是那个服务器出现故障，任何一个客户端都可以使用自己的本地镜像来恢复服务器，每一次检出操作实际上都是对数据的一次完整备份。

Git与其他本本控制系统最大的不同在于其对待数据的方式，从概念上来说，其他大多数版本控制系统以文件变化列表的方式存储信息，这类系统将存储的信息视为一组文件以及对这些文件随实践所作出的变更。

Git将数据视为一个微型文件系统的一组快照，每次提交状态时，Git会抓取当前状态的快照，然后存储一个指向该快照的应用。Git将数据视为一个快照流



## 二、Git基础

### Git指令

1. 在现有目录中初始化Git仓库

```shell
git init
```



2. 克隆现有的仓库

   git clone 会对服务器仓库的几乎所有数据进行性完整复制，而不只是复制当前工作目录

```shell
git clone https://github.com/
git clone https://github.com/    myProject
```



工作目录下的每一个文件都有两种状态之一：已跟踪（tracked）或未跟踪(untracked) 已跟踪的文件是指上一次快照中包含的文件。这些文件又分为未修改，已修改，已暂存三种状态。未跟踪的文件则是工作目录中除去已跟踪文件之外的所有文件



3. 查看当前文件状态

```shell
git status
```



4. 跟踪新文件

```shell
git add filename
#filename如果是目录，则该命令会递地添加该目录下所有的文件
```



5. 暂存已修改的文件

```shell
git add filename
#git add 是一个多功能的命令，既可以用来跟踪新文件，又可以用来暂存文件，还可以用来做一些其他的事。比如把存在合并冲突的文件标记为已解决。
```



6. 显示更简洁的状态信息

```shell
git status -s

 M Readme
MM rakefile
A  lib
M  simple
?? License

#未跟踪的新文件旁边会有一个??标记，已暂存的新文件会有A标记，已修改的文件会有一个M标记。 
#文件了列表旁边分两列，左侧表明了文件是否已暂存，右侧表明了文件是否已修改
```



7. 忽略文件

创建 .gitignore文件，在文件里写入忽略的文件



8. 查看已缓存和未暂存的变更

```shell
git diff
```



9. 提交变更

```shell
git commit

git commit -v	#提交的具体变更
git commit -m	#输入提交信息
git commit -a	#跳过暂存区
```



10. 移除文件

```shell
git rm #从git中移除某个文件，先从已跟踪的文件列表中移除，然后在提交，该命令还会把文件从工作目录中移除

git rm -f #强制移除，文件已暂存的情况下
git rm --cached filename   #功能与.gitignore类似
```



11. 移动文件

```shell
git mv filename1 filename2  #重命名文件相当于
##mv filename1 filename2
##git rm filename1
##git add filename2
```



12. 查看提交历史

```shell
git log
git log -p #显示每次提交所引入的差异
git log -p -2  #只输出最近的两次提交
git log --state #查看每个提交的简要统计信息
git log --pretty=<???> #更改日志输出的默认格式
				online
				short
				full
				fuller
				format  !!!
				
```



13. 限制提交历史的输出范围

```shell
git log -n   #显示最新的额n次提交
！！！
```



14. 撤销已暂存的文件

````shel
git reset HEAD filename
````



15. 撤销对文件的修改

```
git checkout --filename #很危险，执行该命令后，热恩和对filename做出的修改都会丢失
```



16. 显示远程仓库

```shell
git remote			#显示仓库
git remote -v		#显示Git仓库所存储的每个远程仓库对应的URL
```



17. 添加远程仓库

```shell
git remote add [shortname] [url]
```



18. 从远程仓库获取和拉取数据

```
git fetch [remote-name]
#这条命令会从远程仓库中获取所有本地仓库没有的数据

git pull
#如果有一个跟踪着某个远程分支的本地分支，可以使用git pull命令来自动获取远程数据，并将远程分支合并入当前本地分支

git clone 
#自动设置你的本地master分支，使其跟踪被克隆的服务器端的master分支。
```



19. 将数据推送到远程仓库

```
git push [remote-name] [branch-name]
```



20. 检查远程仓库

```
git remote show [remote-name]
```



21. 删除和重命名远程仓库

```
git remote rename [old-name] [new-name]

git remote rm [remote-name]
```



22. 标记

```
git tag  列举标签
git tag -a tagname -m "tag description"	添加标签
git tag tagname -lw			轻量标签
git push origin tagname       共享标签
git checkout -b  branchname tagname 检出标签
```





