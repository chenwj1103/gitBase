# 基本命令
    ```
   1.git clone url
    克隆代码

   2.git init
    创建新文件

   3.git status
    查看git仓库的状态

   4.git的工作流
   git维护三棵树 工作目录（实际持有文件）、缓存区（临时存储你的改动）、HEAD（只想你最近一次提交后的结果）

   5.添加与提交
   git add .或者 git add <fileName> >> 添加到缓存区
   git commit -m "代码提交信息" >>代码已经提交到HEAD 但是没有提交到远端仓库
   git push origin master  >>提交到远端仓库
   git remote add origin <server>  >>如果你还没有克隆远端仓库，或者想要添加你的仓库到远程服务器

   这里 origin 是 < server > 的别名，取什么名字都可以，你也可以在 push 时将 < server > 替换为 origin。但为了以后 push 方便，我们第一次一般都会先 remote add

   6.不追踪的文件
   .gitignore文件

   # 忽略的文件
   *.class

   #忽略的目录
    /src/

   7.git checkout <branch>
    切换分支

    git checkout <commit>
    检出之前的提交是一个只读操作。在查看旧版本的时候绝不会损坏你的仓库
    切换到某次提交的版本的地方，如果你想在当前位置上开发，可以在当前位置创建一个新的分支

   8. git checkout <commit> <file>
    和检出提交不同，这里 确实 会影响你项目的当前状态。旧的文件版本会显示为「需要提交的更改」，
    允许你回滚到文件之前的版本。如果你不想保留旧的版本，你可以用下面的命令检出到最近的版本
    git checkout HEAD <file>

   9.git revert <commit>
    git revert 命令用来撤销一个已经提交的快照。但是，它是通过搞清楚如何撤销这个提交引入的更改，然后在最后加上一个撤销了更改的 新 提交，
    而不是从项目历史中移除这个提交。这避免了Git丢失项目历史，这一点对于你的版本历史和协作的可靠性来说是很重要的

    撤销（revert）和重设（reset）对比
    git revert 回滚了单独一个提交，它没有一处后面的提交，然后回到项目之前的状态。
    git reset 移除了后面的提交。







    ```
