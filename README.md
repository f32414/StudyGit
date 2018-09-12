# 从0开始学Git

1. 版本控制系统
   1. 概念
   2. 进化史
      1. 本地式版本控制
      2. 集中式版本控制
      3. 分布式版本控制
2. Git学习
   1. 安装
   2. 配置
   3. 基本操作
      1. 常用命令
      2. .git
   4. 代码托管平台
      1. 介绍
      2. 配置GitServer


3. 拓展

##

## 版本控制系统

### 概念

> 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。

### 进化史

[完整进化史介绍](https://blog.csdn.net/augusdi/article/details/29846253)

[版本控制软件介绍](https://www.cnblogs.com/yanghongliang/p/5750306.html)

#### 本地式版本控制

> 采用简单的数据库记录文件的历次更新差异。

RCS

...

#### 集中式版本控制

> 通过一台集中管理的服务器保存所有的修订版本，协同工作的人们通过客户端连接到这台服务器，取出最新的文件或提交更新。

SVN

CVS

VSS

ClearCase

StarTeam

...

#### 分布式版本控制

> 指定与若干不同的远端代码仓促进行交互，每一次克隆操作，都是一次对代码仓库的完整备份。

Git

Mercurial

Monotone

...

## Git

### 安装

Linux

Windows

Mac

[各平台安装](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)

Windows平台三种使用方式：

1. Git Bash
2. Git CMD
3. Git Gui

[区别](https://blog.csdn.net/lee18254290736/article/details/53965577)

### 配置

    --global				使用全局配置文件
    --system				使用系统级配置文件
    --local				使用仓库级配置文件
    -f, --file <文件>		使用指定的配置文件
    --blob <数据对象 ID>	从给定的数据对象读取配置

> user.name
>
> user.email

[详细配置信息](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)

name & email



[Git基本原理](http://www.open-open.com/lib/view/open1416359472008.html)

### 基础操作

操作命令：

init			初始化

add			追加追踪文件，放到暂存区

commit		提交（无参数，默认开启vim编辑器输入信息

	-m		提交信息
	
	-a		跳过暂存区
	
	--amend	【漏文件，提交信息错误

status		缓存区状态

mdiff			缓存区状态详细

rm			取消追踪文件

	-f		强制删除已存入缓存区文件
	
	--cached	从Git仓库删除

mv			改名

log			提交历史

		-p			显示提交差异
	
		-数字		查看条数
	
		--stat		显示简略信息
	
		--pretty		格式

[log所有参数](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2)

reset

checkout

远程仓：

remote		查看远程仓【默认名origin

	-add <shortname><url>	添加远程仓
	
	-rename		重命名
	
	rm				移除

clone		克隆远程仓

	-v		显示URL

fetch		抓取新数据

pull			抓取数据并合并到当前分支

push		推送到远程仓

[远程仓使用](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84%E4%BD%BF%E7%94%A8)

tag			列出已有标签

	-l<查询前缀>	条件筛选标签
	
	-a				创建一个附注标签
	
		<标签名><hash>	补标签
	
	-m				存储信息
	
	<标签名>		创建轻量标签

show<标签名>		显示标签及对应的提交信息

[打标签](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE)

Git别名

```git
$ git config --global alias.co checkout
```

不仅是命令，后面也可以跟参数

达到 last 替代【log -1 HEAD】的效果

也可以是替换外部命令

```git
$ git config --global alias.visual '!gitk'
```

分支

待整理...

### 代码托管平台

国内
​	码云
​	Coding
​	阿里云code
国外
​	Github		->		Github Desktop
​	Gitlab

### 配置GitServer

> SSH

```git
# 创建一个专门的用户
useradd git
# 设置密码
passwd 密码
# 初始化空仓库
git init --bare --shared
# 克隆远程仓
git clone user@git.example.com:/opt/git/my_project.git
# 生成ssh密钥
ssh-keygen
# 给git文件夹权限
sudo chown -R git:git sample.git
# 试一下吧！
```

忽略文件



# 错误集锦

> 另一个git进程似乎在这个仓库中运行

rm -f ./.git/index.lock