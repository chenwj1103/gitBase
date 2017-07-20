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

   6.

    ```
