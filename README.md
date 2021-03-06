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
    git revert <commit> 回滚了单独一个提交，它没有一处后面的提交，然后回到项目之前的状态。
    git reset <commit> 移除了后面的提交。
    git reset 经常被用于撤销文件缓存


   10.git log
    查看日志，使用'q'退出

   11.git commit --amend
   命令是修复最新提交的便捷方式。它允许你将缓存的修改和之前的提交合并到一起，而不是提交一个全新的快照。
   它还可以用来简单地编辑上一次提交的信息而不改变快照。

   12.git rebase
        git rebase 是将上游更改合并进本地仓库的通常方法。不像merge，会产生新的merge记录

   13.git reflog
     每次当前的 HEAD 更新时（如切换分支、拉取新更改、重写历史或只是添加新的提交），引用日志都会添加一个新条目

   14. git remote
        列出你和其他仓库之间的远程连接。

   15.git pull
     = git fetch +git merge

   16.git config --global pull.rebase true
   设置之后 git pull的命令将使用rebase而不是merge

   17.git branch
    列出仓库中所有分支
    git branch -r
    列出远端所有分支
    git branch -d <branch>
    删除指定分支。这是一个安全的操作，Git 会阻止你删除包含未合并更改的分支。
    git branch -D <branch>
    强制删除指定分支
    git branch -m <branch>
    将当前分支命名为 <branch>
    git checkout -b <new-branch> <existing-branch>
    创建一个新的分支，将 <existing-branch> 作为新分支的基，而不是当前分支。

    18.解释git命令
    git add files 将工作目录的文件加入到stage缓存；commit命令把缓存中的修改生成一个commit，加入到commit历史中
    git reset 撤销所有的缓存文件，也可以git reset --files 撤销某一个；
    git checkout -- files 把文件从 stage 缓存复制到工作目录，用来丢弃本地修改

    19. git diff --cached
        git diff
        git diff HEAD
        git diff maint
        查看分支之间的不同
    23.代码合并：Merge、Rebase 的选择

       将 master 分支合并到 feature 分支最简单的办法就是用下面这些命令：
       1)merge
       git checkout feature
       git merge master

       2)rebase
       git checkout feature
       git rebase master

       同步两个 master 分支的唯一办法是把它们 merge 到一起，导致一个额外的合并提交和两堆包含同样更改的提交。不用说，这会让人非常困惑。
       所以，在你运行 git rebase 之前，一定要问问你自己「有没有别人正在这个分支上工作？」

       # 小心使用这个命令！
       git push --force

    24. 代码回滚：Reset、Checkout、Revert-的选择
        git reset 用在私有分支上
        git reset HEAD 用来撤销没有提交的更改


        git checkout HEAD^

        git revert
        Revert 撤销一个提交的同时会创建一个新的提交。这是一个安全的方法，因为它不会重写提交历史。比如，下面的命令会找出倒数第二个提交，
        然后创建一个新的提交来撤销这些更改，然后把这个提交加入项目中。

        命令	|作用域	    |常用情景
        git |reset	    |提交层面	在私有分支上舍弃一些没有提交的更改
        git |reset	    |文件层面	将文件从缓存区中移除
        git |checkout	|提交层面	切换分支或查看旧版本
        git |checkout	|文件层面	舍弃工作目录中的更改
        git |revert	    |提交层面	在公共分支上回滚更改
        git |revert	    |文件层面	（然而并没有）

    https://github.com/geeeeeeeeek/git-recipes/wiki/5.1-%E4%BB%A3%E7%A0%81%E5%90%88%E5%B9%B6%EF%BC%9AMerge%E3%80%81Rebase-%E7%9A%84%E9%80%89%E6%8B%A9





    # 图解 git命令
    https://github.com/geeeeeeeeek/git-recipes/wiki/4.1-%E5%9B%BE%E8%A7%A3-Git-%E5%91%BD%E4%BB%A4


    # 代码回滚：Reset、Checkout、Revert 的选择
    https://github.com/geeeeeeeeek/git-recipes/wiki/5.2-%E4%BB%A3%E7%A0%81%E5%9B%9E%E6%BB%9A%EF%BC%9AReset%E3%80%81Checkout%E3%80%81Revert-%E7%9A%84%E9%80%89%E6%8B%A9

    # 常见工作流比较
    https://github.com/geeeeeeeeek/git-recipes/wiki/3.5-%E5%B8%B8%E8%A7%81%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%AF%94%E8%BE%83


    ```
