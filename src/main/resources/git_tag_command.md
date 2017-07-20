#查看标签
	git tag
#打标签
	git tag v0.0.1
#上传标签到master上
	git push origin master --tag
#删除本地的某个标签
	git tag -d v0.0.1
#删除远程的某个标签
	git push origin --delete tag <tagname>
    //或者以下方法
	git tag -d <tagname>
	git push origin :refs/tags/<tagname>