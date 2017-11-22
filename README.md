# test 测试仓库
>用于在任何时候想起/灵机一动/美好事物的记录
##git命令的学习(最基本)
-git init (初始化)
-git add  fileName/-A/* (将文件放入暂存区)
-git commit -m 'describe' (将文件推送至本地仓库)
-git clone address file (address是远程仓库地址；file是要clone到本地的文件夹名)
-git push origin master (将本地仓库 推送 远程仓库)
1.origin:当我们从远程仓库clone 一个仓库到本地后，经过修改后推送到远程仓库时
2.Git会自动执行以下操作：git remote add origin address
3.即：origin==address
##git分支
-git branch (查看分支)
-git branch branchName (创建分支)
-git checkout branchName (切换分支)
***git checkout -b branchName (创建并切换)***
-git merge branchName (合并某分支到当前分支)
1.例：当前为:git checkout master 执行:git merge cart
2.表示将cart分支合并到master
-git branch -d/D branchName (删除分支，-D:强制删除)