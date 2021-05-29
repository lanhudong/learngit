**1、添加文件**（把文件添加进去，实际上就是把文件修改添加到暂存区）： `git add`

**2、上传文件**（提交更改，实际上就是把暂存区的所有内容提交到当前分支）：`git commit`

**3、掌握工作区状态：**`git status`

**4、查看修改内容：**`git diff`

**5、版本回退**

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
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

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git switch <name>`或者`git checkout <name>`

创建+切换分支：`git switch -c <name>`或者`git checkout -b <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`