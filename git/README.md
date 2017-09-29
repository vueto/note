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

> 1. 确实要删除该文件

>  那就用命令`git rm`删掉，并且`git commit`

> 2. 删错了

>  `git checkout --filename` 

> 用版本库中的文件替换工作区的文件

## Github

### 1. 创建ssh密钥

如果有ssh密钥,进入.ssh文件夹目录 `cd ~/.ssh` 

如果没用ssh密钥则用git bash 输入 `ssh-keygen -t rsa -C "1638566006@qq.com"` 创建密钥

id_rsa 是私钥不能泄露出去

id_rsa.pub 是公钥,将其中的内容填写在，打开“Account settings”，“SSH Keys”页面然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

### 2. 将文件推送到github上

git remote add origin https://github.com/vueto/note.git

