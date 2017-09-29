# Git命令行汇总

1. git config --global user.name author

设置git用户名 example : git config --global user.name 'vueto'

2. git config --global user.email email
设置git用户邮箱 example : git config --global user.email '1638566006@qq.com'

3. git init

将所在目录初始化为git可以管理的仓库

4. git add

把文件添加到仓库, example: " git add 'README.md' "

5. git commit 

把文件提交到仓库, git commit -m '提交的说明'

6. git status

查看仓库当前的状态,查看是否有文件被改动过

7. git diff
查看文件被改动过的内容

8. git log
查看git提交的历史记录
带上 --pretty=oneline 可以简化信息