---
title: git
date: 2019-11-06 23:08:12
categories: tools
tags: git
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
			Git提供了一个跳过使用暂存区域的方式,只要在提交的时候,给git commit加上-a选项,Git就会自动把所有**已经跟踪过的**文件暂存起来一并提交,从而跳过git add步骤:
			```bash
			$ git status
			On branch master
			Changes not staged for commit:
			    (use "git add <file>..." to update what will be committed)
			    (use "git checkout -- <file>..." to discard changes in working
			directory)

				modified:    CONTRIBUTING.md
				
			no changes added to commit (use "git add" and/or "git commit -a")
			$ git commit -a -m 'added new benchmarks'
			[master 83e38c7] added new benchmarks
			1 file changed, 5 insertions(+), 0 deletions(-)
			```
		10. ###### 移除文件
			要从Git移除某个文件,就必须要从已跟踪文件清单中移除(确切的说,是从暂存区域移除),然后提交.可以用git rm命令完成此项工作,并连带从工作目录中删除指定的文件,这样以后就不会出现在未跟踪文件清单中了.  
			如果只是手动删除文件,运行git status时就会看到:
			```bash
			$ rm PROJECTS.md
			$ git status
			On branch master
			Your branch is up-to-date with 'origin/master'.
			Changes not staged for commit:
			   (use "git add/rm <file>..." to update what will be committed)
			   (use "git checkout -- <file>..." to discard changes in working
			directory)
			
				deleted:   PROJECTS.md
	
			no changes added to commit (use "git add" and/or "git commit -a")
			```
			然后再运行git rm记录此次移除文件的操作:
			```bash
			$ git rm PROJECTS.md
			rm 'PROJECTS.md'
			$ git status
			On branch master
			Changes to be committed:
			   (use "git reset HEAD <file>..." to unstage)
		
				deleted:    PROJECTS.md
			```
			下一次提交时,该文件就不再纳入版本管理了。 如果删除之前修改过并且已经放到暂存区域的话,则必须要用强制删除选项 -f(译注:即 force 的首字母)。 这是一种安全特性,用于防止误删还没有添加到快照的数据,这样的数据不能被 Git 恢复。  
			另外一种情况是,我们想把文件从Git仓库中删除(即从暂存区域移除),但仍然希望保留在当前工作目录中.换句话说,你想让文件保留在磁盘,但是并不想让Git继续跟踪.为达到这一目的,使用 --cached 选项:  
			`$ git rm --cached README`  
			git rm命令后面可以列出文件或者目录的名字,也可以使用glob模式.比方说:  
			`$ git rm log/\*.log`  
			注意到星号*之前的反斜杠\,因为Git有它自己的文件模式扩展匹配方式,所以我们不用shell来帮忙展开.此命令删除log/目录下扩展名为.log的所有文件.类似的比如:  
			`$ git rm \*~`  
			该命令为删除以~结尾的所有文件.
		11. ###### 移动文件
			在Git中重命名某个文件可以如此操作:`$ git mv file_from file_to` 进行这项操作后可以看到以下说明
			```bash
			$ git mv README.MD README
			$ git status
			On branch master
			Changes to be committed:
			  (use "git reset HEAD <file>..." to unstage)
			  
			  renamed:	README.MD -> README
			```
			其实运行git mv就相当与运行了下面三条命令:
			```bash
			$ mv README.md README
			$ git rm README.md
			$ git add README
			```
	3. #### 查看提交历史
		可以使用git log命令来查看提交的历史:
		```bash
		git clone https://github.com/schacon/simplegit-progit
		$ git log
		commit ca82a6dff817ec66f44342007202690a93763949
		Author: Scott Chacon <schacon@gee-mail.com>
		Date:   Mon Mar 17 21:52:11 2008 -0700
	
		     changed the version number
	
		commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
		Author: Scott Chacon <schacon@gee-mail.com>
		Date:   Sat Mar 15 16:40:33 2008 -0700
	
		     removed unnecessary test
	
		commit a11bef06a3f659402fe7563abf99ad00de2209e6
		Author: Scott Chacon <schacon@gee-mail.com>
		Date:    Sat Mar 15 10:31:28 2008 -0700
	
		     first commit
		```
		如果默认不使用任何参数的话,git log 会按提交时间列出所有更新,最近的排在最上面.  
		当然git log有很多选项:
		* -p,用来显示每次提交的内容差异.
		* -2(可换),显示最近两次的提交.
		```bash
		$ git log -p -2
		commit ca82a6dff817ec66f44342007202690a93763949
		Author: Scott Chacon <schacon@gee-mail.com>
		Date:   Mon Mar 17 21:52:11 2008 -0700
	
			changed the version number
	
		diff --git a/Rakefile b/Rakefile
		index a874b73..8f94139 100644
		--- a/Rakefile
		+++ b/Rakefile
		@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
		  spec = Gem::Specification.new do |s|
			s.platform =   Gem::Platform::RUBY
			s.name =   "simplegit"
		-	s.version =   "0.1.0"
		+	s.version =   "0.1.1"
			s.author  =   "Scott Chacon"
			s.email   =   "schacon@gee-mail.com"
			s.summary =   "A simple gem for using Git in Ruby code."
	
		commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
		Author: Scott Chacon <schacon@gee-mail.com>
		Date:    Sat Mar 15 16:40:33 2008 -0700
	
			removed unnecessary test
	
		diff --git a/lib/simplegit.rb b/lib/simplegit.rb
		index a0a60ae..47c6340 100644
		--- a/lib/simplegit.rb
		+++ b/lib/simplegit.rb
		@@ -18,8 +18,3 @@ class SimpleGit
			end
	
		 end
		-
		-if $0 == __FILE__
		- git = SimpleGit.new
		- puts git.show
		-end
		\ No newline at end of file
		```


​			
