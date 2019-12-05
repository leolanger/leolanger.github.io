---
title: git
date: 2019-11-06 23:08:12
categories:  programming
tags:  git
---

#                                                                            git

<!--more-->

1. ## git 基础
	在开始先认识Git的三种状态:已提交(committed)、已修改(modified)和已暂存(staged）。已提交表示数据已经安全的保存在本地数据库中；已修改表示修改了文件，但还没保存到数据库中；已暂存表示对一个已修改文件的当前版本做了标记（即被add过了），是指包含在下次提交的快照中。

	1. ### 获取git仓库

 		创建仓库:`$ git init`  

 		克隆现有仓库:`$ git clone url`  
		1. `$ git clone https://github.com/libgit2/libgit2`,这会在当前目录下创建一个名为"ligbit2"的目录,并在该目录下初始一个.git文件夹,将远程仓库中取下的所有文件放入其中.
		2. `$ git clone https://github.com/libgit2/libgit2 mylibgit`,此操作把本地创建的仓库名字变为mylibgit.

	2. ### 记录每次更新到仓库

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
			 只要在Changes to be committed这行下面的,就说明是已暂存状态.
		4. ###### 暂存以修改文件
			如果我们修改了一个名为CONTRIBUTING.md的已被跟踪文件，然后运行git status会看到：
			```bash
			$ git status
			On branch master
			Changes to be committed
			   (use "git reset HEAD <file>..." to unstage)
			      new file:	README
			Changes not staged for commit:
			   (use "git add <file>..." to update what will be committed)
			   (use "git checkout -- <file>..." to discard changes in working directory)
			       modified: CONTRIBUTING.md
			  ```
			文件CONTRIBUTING.md出现在Changes not staged for commit这行下面，说明已跟踪文件的内容发生了变化，但还没有放到暂存区。要暂存这次跟新需要git add命令。
		5. ###### 状态简览
			对`git status` 命令可以使用`git status -s`或`git status --short`,是输出更为紧凑。此时的输出如下：
			```bash
			$ git status -s
			 M README
			MM Rakefile
			A  lib/gie.rb
			M  lib/simplegit.rb
			?? LICENSE.txt
			```
			？？标记为新添加的未跟踪文件；A标记为新添加到暂存区中的文件；出现在靠左边的M表示该文件被修改了并放入了暂存区，而靠右边的M表示该文件被修改了但是还没放入暂存区；而Rakefile则是在工作区被修改并提交到暂存区后又在工作区被修改了（滑稽）。
		6. ###### 忽略文件
			一般我们会有一些文件，无需纳入Git的管理，也并不希望他们出现在未跟踪文件列表。在这种情况下，我们可以创建一个名为.gitignore的文件，列出要忽略的文件模式。
			```bash
			$ cat .gitignore
			*.[oa]
			*~
			```
			第一行告诉Git忽略所有以.o或.a结尾的文件。第二行告诉Git忽略所有以波浪符结尾的文件。  
			文件.gitignore的格式规范如下：
			* 所有空行或者以#开头的行都会被Git忽略。
			* 可以使用标准的glob模式匹配。
			* 匹配模式可以以（/）开头防止递归
			* 匹配模式可以以（/）结尾指定目录。
			* 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（！）取反。
			
			所谓glob模式是指shell所使用的简化了的正则表达式。星号（*）匹配零个或多个任意字符；[abc]匹配任何一个列在放括号中的字符；问号（？）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示可以匹配到所有在这两个字符范围内的字符；使用两个星号表示匹配任意中间目录。
			Github有一个针对数十种项目即语言的.gitignore文件列表，可以在[这儿](https://github.com/github/gitignore)找到它。
		7. ###### 查看已暂存和为暂存的修改
			如果你觉得git status命令的输出过于模糊，你想知道具体修改了什么地方，可以用git diff命令。在git diff后还可以添加参数。使用git difftool --tool-help来看你的系统支持哪些插件。
		8. ###### 提交更新
			在完成git add后，先用git status检查以下，然后用`$ git commit`命令提交。这种方式会启动文本编辑器以便输入本次提交说明（因为我用的是Vim，所以只后以vim方式显示。当然也可以用git config --global core.editor命令来设定你喜欢的编辑软件）  
			编辑器会显示类似下面的文本信息：
			```vim
			# Please enter the commit message for your changes. Lines starting
			# with '#' will be ignored, and an empty message aborts the commit.
			# On branch master
			# Changes to be committed:
			#
			   new file:	 README
			#
 			   modified:     CONTRIBUTING.md
			#
			~
			~
			~
			".git/COMMIT_EDITMSG" 9L, 283C
			```
			另外,你也可以在 commit 命令后添加 -m 选项,将提交信息与命令放在同一行,如下所示:
			```vim
			$ git commit -m "Story 182: Fix benchmarks for speed"
			[master 463dc4f] Story 182: Fix benchmarks for speed
			2 files changed, 2 insertions(+)
			create mode 100644 README
			```
			可以看到,提交后它会告诉你,当前是在哪个分支(master)提交的,本次提交的完整 SHA-1 校验和是什么(463dc4f),以及在本次提交中,有多少文件修订过,多少行添加和删改过。
		9. ###### 跳过使用暂存区域
			
