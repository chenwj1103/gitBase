

# 创建分支
````
git checkout -b chen
````
# 开发
````
git add .
git commit -m  // 在本地的chen分支
git push origin chen:chenwj  // 本地名字：远程名字, 会在远端创建一个名字叫 chenwj的分支
git branch -r -d origin/dev2(另一种方式)
````

# 合并到 master
````
git checkout master
git pull
git merge chen
````
# 解决冲突

````
git add .
git commit 
git push origin master // 推到分支
````

#删除分支
````
git branch -D 分支名字(删除 本地分支)
git push origin  :chen(删除 远端分支)
````


#查看分支
````
 git branch -a (查看远程分支)
 git branch  (查看本地分支)
`````






#master上取下最新代码 创建分支
````
git checkout -b issue 
````
#开发
````
git add.
git commit -m "issue #5"
git push origin issue:chenwj3/issue   (本地和远程分支)
````
#请求合并issue到master（注意选择分支）

#合并到里程碑分支
````
git checkout 里程碑分支
git pull origin 里程碑分支
git checkout issue
````
#创建合并issue-n的分支
````
git checkout -b issue-m
git merge 里程碑分支  
git commit -m "合并里程碑"
git push origin issue-m:chenwj3/issue-m

````
#请求issue-m合并到里程碑（注意选择分支）


# 清除本地的分支
````
git remote prune origin
````



#合并分支出错 撤销到上一个
````
git reset HEAD^ --hard
````

# 修改已经提交的日志
````
 git commit -amend 
````
#修改。。。
````
 git push origin chenwj --force
````

# 撤销并保留已push的代码
````
从开发分支上check出一个分支
merge被从dev-chen的分支
撤销提交 git reset --soft commitid(dev最后一个commitId)
得到了在dev上开发的代码 已经commit的
得到add之前的代码 git reset HEAD  -filename

````


# 以下例子是开发中合并dev分支的最新支代码
  
1. 在master分支上拉去最新的代码
````
git checkout master
git pull
````
2. 在dev的远程分支下创建一个分支
````
git checkout -b issue1 origin/dev

 开发...
  git add .
  git commit -m "issue #2"
````
3. 此时合并dev分支的最新的代码  
````
git pull --rebase 

````
4. 有冲突解决冲突（此时rebase命令会中断，解决冲突后执行此命令）
````
  git rebase --continue 
````
