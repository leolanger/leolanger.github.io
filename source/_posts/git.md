---
title: git
date: 2019-11-06 23:08:12
categories:  programming
tags:  git
---

#                                                                            git

<!--more-->

## git 基础

### 获取git仓库

 创建仓库:`$ git init`  

 克隆现有仓库:`$ git clone url`

​    1 .`$ git clone https://github.com/libgit2/libgit2`,这会在当前目录下创建一个名为"ligbit2"的目录,并在该目录下初始一个.git文件夹,将远程仓库中取下的所有文件放入其中.

​    2 .`$ git clone https://github.com/libgit2/libgit2 mylibgit`,此操作把本地创建的仓库名字变为mylibgit.

### 记录每次更新到仓库



1. 首先通过`$ cd /home/leolanger/文档/project/C/`定位到.git文件夹所在的目录

2. ###### 检查当前文件状态

     `$ git status`这会显示未跟踪状态的新文件,更改过的文件,当前的分支(会在之后详细讨论)

3. ###### 跟踪新文件

    `$ git add 文件名`

   此时在运行在运行 git status 命令,会看到该文件已被跟踪,并处与暂存状态:

   ```bash
   $ git status
   On branch master
   Change to be committed:
     (use "git reset HEAD <file>..." to unstage)
     
       new file :             文件名
   ```

   

   ​    (未完待续)
