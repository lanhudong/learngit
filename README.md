## 简单的Git使用教程

- [简单的Git使用教程](#简单的git使用教程)
  - [创建Git目录](#创建git目录)
  - [添加文件](#添加文件)
  - [上传文件](#上传文件)
  - [掌握工作区状态](#掌握工作区状态)
  - [查看修改内容](#查看修改内容)
  - [版本回退](#版本回退)
  - [删除文件和文件夹目录](#删除文件和文件夹目录)
  - [关联和删除远程库](#关联和删除远程库)
  - [克隆github仓库](#克隆github仓库)
  - [分支的使用](#分支的使用)
  - [标签管理](#标签管理)
  - [多人协作](#多人协作)
  - [上传远程库出错问题](#上传远程库出错问题)
  - [关联远程仓库相关问题](#关联远程仓库相关问题)
### 创建Git目录
通过`git init`命令把这个目录变成Git可以管理的仓库

### 添加文件
（把文件添加进去，实际上就是把文件修改添加到暂存区）： `git add`，批量一次性提交可以：`git --all`

### 上传文件
（提交更改，实际上就是把暂存区的所有内容提交到当前分支）：`git commit`

### 掌握工作区状态
`git status`

### 查看修改内容
`git diff`

### 版本回退

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。精简log输出内容可以加上：`--pretty=oneline`参数
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

### 删除文件和文件夹目录

- 删除文件：`rm <文件名>`，tips：*从来没有被添加到版本库就被删除的文件，是无法恢复的！*

- 删除文件夹：`rm -r <文件夹名>`

### 关联和删除远程库

 - 关联远程库：`git remote add origin git@server-name:path/repo-name.git`

   比如说我要关联我的一个github中的一个仓库：`git remote add origin git@github.com:alandiy/learngit.git`

- github远程库推送与修改：关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名。关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改

- 删除远程库与本地连接：` git remote rm origin` ，origin是一般远程库默认名称

- 查看远程库连接情况：`git remote -v`

### 克隆github仓库

`git clone <Code SSH>`

### 分支的使用

- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 切换分支：`git switch <name>`或者`git checkout <name>`
- 创建+切换分支：`git switch -c <name>`或者`git checkout -b <name>`
- 合并某分支到当前分支：`git merge <name>`
- 删除分支：`git branch -d <name>`

### 标签管理

- 添加标签：`git tag <tagname>` 例如 `git tag v1`，默认为`HEAD`，也可以指定一个commit id 添加
- 查看标签：`git tag`
- 删除标签：`git tag -d <tagname>`
- 命令`git tag -a <tagname> -m "blablabla..."`可以指定标签信息
- 同步远程库标签：`git push <远程库名> <本地库名> --tags`

### 多人协作

- 查看远程库信息，使用`git remote -v`；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用`git branch --track branch-name origin/branch-name`；
- 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突

### 上传远程库出错问题

<u>12.1</u>  当 `git push`的时候，本地分支的内容和远程库（服务器）分支的内容不一致时，会导致出错。

*解决方案：* 同步远程库（服务器）的内容，保证本地代码和服务器代码版本一致。

- `$ git pull --rebase <Code SSH>`
- 再次上传代码
- 如果提示有文件冲突，需要手动解决冲突后并重新`add`，`commit`更改完成后，输入命令`git rebase --continue`确认，确认之后重新`git push`上传到远程仓库即可（该方法加了`rebase`参数，目的可以把本地未push的分叉提交历史整理成直线，不修改分叉提交历史的也可参考下方12.2）

<u>12.2</u>  当 `git push`的时候，本地分支的内容和远程库（服务器）分支的文件内容冲突时，会导致出错。

*解决方案：* 同步远程库（服务器）的内容，保证本地代码和服务器代码版本一致。

- `$ git pull`
- 打开内容冲突文件，修改后，重新`add`，`commit`后再次上传合并到远程仓库
  

### 关联远程仓库相关问题

参考：[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600/898732864121440)

举个例子，比如说你的个人电脑需要关联远程仓库github。

- 第一步的话，你的电脑需要创建`SSH Key`，一般都是在用户目录下，记得打开隐藏文件的选项，如果没有`.ssh`的目录则需要创建。
- 创建ssh key，打开Git Bash使用命令 `$ ssh-keygen -t rsa -C "youremail@example.com"` 随后步骤回车即可。
- 接下来，你在.ssh目录下会看见两个文件，分别为：id_rsa（私钥）和id_rsa.pub（公钥），私钥打死都不要告诉别人哦。
- 把公钥里面的内容复制下来，在github个人设置那里，点击Add SSH Key，添加进去即可，title可以随便取

按照上面四个步骤做完之后，就可以关联推送内容到github啦。

> 在新版 Git 中可以用 `git remote rename` 命令修改某个远程仓库在本地的简称，比如想把 `aa` 改成`bb`，可以这么运行：
>
> ```ruby
> $ git remote rename aa bb
> ```




---

> 以上部分学习内容参考-https://www.liaoxuefeng.com/wiki/896043488029600
