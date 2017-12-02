# Notes仓库(用于在任何时候想起/灵机一动/美好事物的记录)
## git命令的学习(最基本)
- git init (初始化)
- git add  fileName/-A/* (将文件放入暂存区)
- git commit -m 'describe' (将文件推送至本地仓库)
- git clone address file (address是远程仓库地址；file是要clone到本地的文件夹名)
- git push origin master (将本地仓库 推送 远程仓库)
	>	1. origin:当我们从远程仓库clone 一个仓库到本地后，经过修改后推送到远程仓库时
	>	2. Git会自动执行以下操作：git remote add origin address
	>	3. 即：origin==address
## git分支
- git branch (查看分支)
- git branch branchName (创建分支)
- git checkout branchName (切换分支)
***git checkout -b branchName (创建并切换)***
	> 	分支创建规范化  
	>	1.一个“稳定分支”，即master分支不要轻意被修改  
	>	2.一个开发分支（developer），保证master分支的稳定性  
	>	3.所有的功能分支（feature）从developer分支创建(功能完成后，merge(合并)到developer分子后，可删除该分支)  
	>	4.所有功能开发完成后新建发布分支(release),,最后merge(合并)到master分支
- git merge branchName (合并某分支到当前分支)  
	>	1. 例：当前为:git checkout master 执行:git merge cart
	>	2. 表示将cart分支合并到master
- git branch -d/D branchName (删除分支，-D:强制删除)

## git命令汇总
- git config配置本地仓库
	> 常用git config --global user.name、git config --global user.email
- git config --list查看配置详情
- git init 初始一个仓库，添加--bare可以初始化一个共享（裸）仓库
- git status 可以查看当前仓库的状态
- git add“文件” 将工作区中的文件添加到暂存区中，其中file可是一个单独的文件，也可以是一个目录、“*”、-A
- git commit -m '备注信息' 将暂存区的文件，提交到本地仓库
- git log 可以查看本地仓库的提交历史
- git branch查看分支
- git branch“分支名称” 创建一个新的分支
- git checkout“分支名称” 切换分支
- git checkout -b deeveloper 他健并切到developer分支
- git merge“分支名称” 合并分支
- git branch -d “分支名称” 删除分支
- git clone “仓库地址”获取已有仓库的副本
- git push origin “本地分支名称:远程分支名称”将本地分支推送至远程仓库，
- git push origin hotfix（通常的写法）相当于
- git push origin hotfix:hotfix
- git push origin hotfix:newfeature
	> 本地仓库分支名称和远程仓库分支名称一样的情况下可以简写成一个，即git push “仓库地址” “分支名称”，如果远程仓库没有对应分支，将会自动创建
- git remote add “主机名称” “远程仓库地址”添加远程主机，即给远程主机起个别名，方便使用
- git remote 可以查看已添加的远程主机
- git remote show “主机名称”可以查看远程主机的信息




## 遇到的问题:php中file_get_contents无法请求https连接
- 错误提示:
	> warning: fopen() [function.fopen]: Unable to find the wrapper "https" - did you forget to enable it when you configured PHP?
- windows解决方案(用的是wamp):
	> windows下的PHP，只需要到php.ini中把extension=php_openssl.dll前面的;删掉，重启服务即可。



## gulp项目构建工具的学习
*	npm init 创建package.json文件，用来记录依赖
* 	安装:

	1.cnpm install gulp --save-dev(--sava-dev:是将此依赖记录到package.json文件的devdependences.)   
	2.cnpm install gulp-cssmin --save-dev(安装gulp插件，例如执行此程序安装压缩css文件的插件)  
	3.more:  
		> gulp-less(编译less为CSS)   
		> gulp-uglify(丑化(压缩)JavaScript)   
		> gulp-autoprefixer(自动添加私有前缀)  
		> gulp-imagemin(压缩图片)   
		> gulp-rename(重命名)   
		> gulp-rev(添加版本号)   
		> gulp-rev-collector(替换内容)  
		> gulp-useref()  
		> gulp-if()  

* 	使用:
 	```javascript
 	gulp.task('useref', function () {  
		return gulp.src('./index.html')
			.pipe(useref()) 		//在'./index.html'进行了类似判断操作  
			.pipe(gulpif('*.js', uglify()))		//对'./index.html'中的'*.js'压缩  
			.pipe(gulpif('*.js', rev()))		//对'./index.html'中的'*.js'添加版本号  
			.pipe(gulp.dest('./release'))		//保存到'./release'下  
			.pipe(rev.manifest()) 		//生成一个json文件存 rev的js 与 原js 对应的关系 
			.pipe(rename('js-manifest.json'))	//给此json重命名  
			.pipe(gulp.dest('./release/rev'));	//将这个json存到'./release/rev'下  
	});  
	```