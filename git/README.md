# Git命令行汇总

### 1. git config --global user.name author

设置git用户名 example : `git config --global user.name 'vueto'`

### 2. git config --global user.email email
设置git用户邮箱 example : `git config --global user.email '1638566006@qq.com'`

### 3. git init

将所在目录初始化为git可以管理的仓库

### 4. git add

把文件添加到仓库, example: " `git add "README.md"` "

### 5. git commit 

把文件提交到仓库, `git commit -m` '提交的说明'

### 6. git status

查看仓库当前的状态,查看是否有文件被改动过

### 7. git diff

查看文件被改动过的内容

### 8. git log

查看git提交的历史记录
带上 `--pretty=oneline` 可以简化信息

### 9. git reset --hard

版本回退： `git reset --hard Head^` 退回上一个版本,每多一个^多回一个版本

`git reset --hard 版本号(不用写全)` 直接回到这个版本

### 10. git reflog

用于找到你的每一次提交记录，当你版本回退找不到之后的版本号可以使用此命令(重返未来)

### 11. git checkout

让文件回到最近一次`git commit` 或 `git add` 的状态,丢弃工作区的修改

example: `git checkout --readme.md`

### 12. git reset HEAD

可以回退版本,也可以把暂存区的修改回退到工作区。丢弃暂存区的修改

example: `git reset HEAD readme.txt`

### 13. git rm 

当你删除了一个文件有两种情况

> 1.确实要删除该文件

>  那就用命令`git rm`删掉，并且`git commit`

> 2.删错了

>  `git checkout --filename` 

> 用版本库中的文件替换工作区的文件

## Github

### 1. 创建ssh密钥

如果有ssh密钥,进入.ssh文件夹目录 `cd ~/.ssh` 

如果没用ssh密钥则用git bash 输入 `ssh-keygen -t rsa -C "1638566006@qq.com"` 创建密钥

id_rsa 是私钥不能泄露出去

id_rsa.pub 是公钥,将其中的内容填写在，打开“Account settings”，“SSH Keys”页面然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

### 2. 将文件推送到github上

第一次推送到github上

关联一个远程库 `git remote add origin https://github.com/vueto/note.git`

第一次推送master分支的所有内容 `git push -u origin master`

之后可以通过 `git push origin master` g推送到github上

## Git分支管理

### 1. git checkout -b

创建并切换分支 example: `git checkout -b dev`

`git branch xxx` 创建分支

`git checkout xxx` 切换分支

`git branch` 查看当前分支

### 2. 合并分支

`git merge xxx` 合并xxx分支合并到当前分支

### 3. 删除分支

`git branch -d xxx` 删除xxx分支

### 4. 解决冲突

当合并分支产生冲突时，可以用 `git status` 查看冲突的文件

### 分支管理策略

通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。

如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

强制禁用Fast forward模式，可以使用` git merge --no-ff xxx ` 合并分支

example： `git merge --no-ff -m "merge with no-ff" dev`

`-m` 参数带的描述

### BUG分支

`git stash`可以将当前的工作现场保存起来,可以创建临时分支愉快的改bug

`git stash list`查看被保存起来的工作现场

 恢复工作现场

1.`git stash apply`恢复后，stash内容并不删除，你需要用`git stash drop`来删除

2.`git stash pop`，恢复的同时把stash内容也删了


### Feature分支

软件开发中，总有无穷无尽的新的功能要不断添加进来。

添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。

1.于是准备开发：

创建新的分支 ` git checkout -b feature-vulcan`

2.开发完毕后:

放入暂存区 `git add vulcan.py`

查看状态 `git status`

提交到版本库 `git commit -m "add featrue vulcan"`

3.合并分支

切换分支 `git checkout dev` 

销毁分支 `git branch -d feature-vulcan` 

此时git会提醒feature-vulcan分支还没有被合并，如果删除，将丢失掉修改，如果要强行删除，需要使用命令`git branch -D feature-vulcan`然后使用该命令强行删除

开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。

### 多人协作

当你从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且，远程仓库的默认名称是origin

1.查看远程库的信息，用 `git remote` 或者 `git remote -v`查看更详细的信息

####推送分支

1.推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上

`git push origin master`

2.如果要推送其他分支，比如`dev`

`git push origin dev`

#### 抓取分支

当你的小伙伴从远程库`clone`时，默认情况下，你的小伙伴只能看到本地的`master`分支。不信可以用`git branch`命令看看

现在，你的小伙伴要在`dev`分支上开发，就必须创建远程`origin`的`dev`分支到本地，于是他用这个命令创建本地dev分支

在本地新建一个分支： `git branch Branch1`
切换到你的新分支: `git checkout Branch1`
将新分支发布在github上： `git push origin Branch1`
在本地删除一个分支： `git branch -d Branch1`
在github远程端删除一个分支： `git push origin :Branch1`   (分支名前的冒号代表删除)


<<<<<<< HEAD
与远程分支创建连接 `git branch --set-upstream dev origin/dev`

抓取github上的分支 `git pull`
=======

>>>>>>> dev
