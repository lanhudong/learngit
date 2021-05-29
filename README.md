## 简单的Git使用教程

**0、创建Git目录：** 通过`git init`命令把这个目录变成Git可以管理的仓库

**1、添加文件**（把文件添加进去，实际上就是把文件修改添加到暂存区）： `git add`

**2、上传文件**（提交更改，实际上就是把暂存区的所有内容提交到当前分支）：`git commit`

**3、掌握工作区状态：**`git status`

**4、查看修改内容：**`git diff`

**5、版本回退**

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。精简log输出内容可以加上：`--pretty=oneline`参数
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

**6、删除文件和文件夹目录**

- 删除文件：`rm <文件名>`，tips：*从来没有被添加到版本库就被删除的文件，是无法恢复的！*

- 删除文件夹：`rm -r <文件夹名>`

**7、关联和删除远程库**

 - 关联远程库：`git remote add origin git@server-name:path/repo-name.git`

   比如说我要关联我的一个github中的一个仓库：`git remote add origin git@github.com:alandiy/learngit.git`

- github远程库推送与修改：关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名。关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改

- 删除远程库与本地连接：` git remote rm origin` ，origin是一般远程库默认名称

**8、克隆github仓库**：`git clone`

**9、分支的使用：**

- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 切换分支：`git switch <name>`或者`git checkout <name>`
- 创建+切换分支：`git switch -c <name>`或者`git checkout -b <name>`
- 合并某分支到当前分支：`git merge <name>`
- 删除分支：`git branch -d <name>`

**10、多人协作：**

- 查看远程库信息，使用`git remote -v`；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
- 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突

11、当 `git push`的时候，本地的内容和远程库（服务器）的内容不一致时，会导致出错。

​	*解决方案：* 同步远程库（服务器）的内容，保证本地代码和服务器代码版本一致。

	- `$ git pull --rebase <Code SSH>`
	- 再次上传代码



---

> 以上部分学习内容参考-https://www.liaoxuefeng.com/wiki/896043488029600
