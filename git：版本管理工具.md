git：版本管理工具

作用：管理源代码

git安装

​	初始化Git仓库==》保存临时文件

​			右键==》git bash

​			命令：git	 init

自报家门：每一次备份都会记录备份者信息

​		git 	config 	--global 	user.name    "" 	配置用户名

​		git 	config	 --global 	user.emil       "" 	 配置邮箱

将文件备份到仓库

​		git	add 	代码路径    不带引号	暂存区

​		git	add	./	目录下所有文件放进暂存区

​		git	 commit	-m	"这次修改的说明"	版本库

​		git	commit	--all   --m	" " 	跳过暂存区将所有文件放入版本库

查看当前状态，查看当前代码有没有方进仓库中去

​		git 	status        

查看提交次数

​		git	log			最新提交的在最上面，索引为0

​		git	log	--oneline	简介显示

提取之前的备份

​		git	reset	--hard	Head~0	head~索引从0开始

​		git	reset	--hard	版本号	精确回退

查看操作记录

​		git	reflog



创建分支

​		git 	branch	分支名（dev）

查询分支

​		git	branch

切换分支

​		git	checkout	分支名

合并分支：将当前分支与dev合并（要先切换到master主分支）

​		git	merge	分支名（dev）



上传到github

​		git	push	github网址	master

下载到本地

​		git	pull	github网址	master			需要在本地git init初始化

​		git	clone	github网址	master 		不需要初始化

创建github密匙

​		$ ssh-keygen -t rsa -C ["邮箱"]		邮箱可以随便写

​		将生成的公钥给别人，设置到github，就可以修改别人GitHub上的文件



指定远程链接，用来简写push 和pull

​		remote：远程		origin：起源（这里相当于一个变量）

​		远程指定【网址】为变量origin

```
	git remote add origin git@github.com:licyy/hhh.git
```

​		下次push或者pull时

​		git	push|pull	origin	master

​		简写

​		git	push|pull	-u	origin	master

