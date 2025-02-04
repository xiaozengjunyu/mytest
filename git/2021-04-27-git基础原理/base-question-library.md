﻿## 2021-04-27 学习内容

>参考
> * [《廖雪峰 Git 教程》](https://www.liaoxuefeng.com/wiki/896043488029600)  
 
* [一、Git 版本回退]()
  * [1.版本回退](#1版本回退)
  * [2.已提交与未提交版本](#2已提交与未提交版本)
* [二、工作区和暂存区](#二git工作区与暂存区)
  *  [1.什么是工作区](#1什么是工作区)
  *  [2.什么是暂存区](#2什么是暂存区)
  *  [3.文件如何存入版本库](#3文件如何存进版本库)
* [三、管理修改](#三管理修改)
  * [1.修改文件存放区域](#1修改文件存放区域)
  * [2.撤销修改](#2撤销修改)
  * [3.删除及还原文件](#3删除及还原)
* [四、远程仓库](#远程仓库github)
  * [1.什么是远程仓库](#1什么是远程仓库)
  * [2.使用 Git 连接 GitHub ](#2使用git连接github)
* [五、注意点](#注意点)
  
## 一、Git的版本回退
主要用于回退到以前的版本、回退到将来的版本  
### 1.（版本回退）:  
#### 示例:


###  2.（已提交与未提交版本）:  
 #### 示例:
* git reset --hard HEAD^（^表示上一个版本，n个的话 HEAD~N ）
* git reset --hard 版本号（回退到指定版本号，git log 查看版本库，git reflog 用于查看命令历史，方便穿越）
 
## 二、Git 工作区与暂存区
 整个文件夹相当于一个工作区,Git 和其他版本控制系统不同之处就是有暂存区的概念。
 ### 1.（什么是工作区）:  
整个项目文件夹相当于一个工作区。
 ### 2.（什么是暂存区）:  
工作区下面一个 .git 文件夹就是git的版本库，版本库中最重要的就是 index暂存区。
 ### 3.（文件如何存进版本库）:  
  将文件存入到 Git 的版本库中，然后更新文件的值，存储在暂存区，之后将暂存区的文件进行效验之后保存到一个树对象，然后将顶层对象指针和要提交的信息合并成 commit 对象。
##### 示例
    $ git add readme.txt  #将 readme 文件存入暂存区
    $ git status          #查看当前工作区的状态 
 
## 三、管理修改
git add 命令后文件被放在暂存区，没有提交使用 git restore --staged 撤出暂存区域，然后在用 git restore修改内容。
### 1.（修改文件存放区域）:
  
##### 示例
    $ git add readme.txt  #将 readme 文件存入暂存区
    $ git status          #查看当前工作区的状态 
### 2.（撤销修改）:
##### 示例  
    $ git commit -m "git tracks changes" #提交缓存区文件，m后面代表注释
    $ git restore --staged readme.txt #将暂存区的文件从暂存区撤出，但不会更改文件内容
    $ git restore readme.txt #撤销修改，返回到之前未更改状态    
### 3.（删除及还原）:  
   * RM删除之后 git status查看状态，git restore 还原  
   * RM删除之后版本库还有，使用 git checkout 还原最新版本的文件。
#### 示例
    $ git rm test.txt #删除test文件
    $ git checkout -- test.txt #用版本库的版本替换工作区的版本

## 远程仓库（GitHub）
 ### 1.（什么是远程仓库）
 放在服务器上的，大家公用的仓库。
 ### 2.使用 Git 连接 GitHub
 首先远程仓库要先创建，之后配置 Github 的邮箱用户名和 SSH，通过 SSH 使本地仓库和远程仓库连接。  
#### 示例
    $ git config --global user.name '自己的用户名'
    $ git config --global user.email '自己的邮箱'
运行完可以在C:\Users\用户名 下.gitconfig查看公用SSH秘钥内容
### 常用Git指令
 * git status 查看当前工作区状态
 * git add    将文件存入到暂存区
 * git commit 将暂存区所有文件提交
 * git restore 将工作区还未存入暂存区的修改撤销，返回到还未更改之前
 * git restore --staged 将暂存区的文件从暂存区撤出，但不会更改文件内容
 
## 注意点：
* 1.确认 SSH 密钥无误。（权限问题无法提交）
* 2.连接的远程库如果不是空白的需要克隆。（git clone克隆）
* 3.确认本地仓库 git 目录下是否为空。