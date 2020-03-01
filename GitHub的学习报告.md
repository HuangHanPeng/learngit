# GitHub的学习报告

## GitHub的简介

>### GitHub是什么？
>
>GitHub是分布式版本控制系统
>
>## 安装GitHub
>
>> 官网下载
>>
>> 安装完成后，登录
>>
>> git config --global user.name “Your Name”
>>
>> git config --global user.email “email@example.com”
>
>-----
>
>### 仓库
>
>> #### 本地仓库
>>
>> > 1.创建本地仓库
>>
>> ​	a.GitHub Bush上 创建文件夹
>>
>> ​	mkdir [folder name]
>>
>> ​	b.到指定文件夹
>>
>> ​	cd /路径/
>>
>> ​	c.将空仓库变成可管理仓库.git
>>
>> ​	git init
>>
>> > #### 基本命令：
>> >
>> > 
>> >
>> > ​	git add [filename] - - 将工作区的文件添加到暂存区
>> >
>> > ​	git add file1name  file2name - - 将多个文件添加到暂存区
>> >
>> > ​    git commit -m“注释” --提交到版本库中
>> >
>> > ​	git diff [filename] 或 git status -- 查询修改
>> >
>> > ​	git log -- 查询修改历史内容
>> >
>> > ​	git reflog - - 查看历史命令
>> >
>> > > 当使用git log - - pretty=oneline 时可以得到文件的十六进制
>> > >
>> > > cat filename  - - 查看文件内容
>> > >
>> > > vi filename - - 进入文件可以执行修改操作
>> > >
>> > > 

#### 远程仓库

1.创建远程仓库

a.在github页面上创建远程仓库

b.在本地仓库上创建远程仓库

> git remot add origin 仓库地址（http://github.com/xxx）

2.推送

> 1.第一次推送本地分支
>
> ​	git push -u origin master
>
> 2.再次提交
>
> ​	git push origin master 或者  git push
>
> 3.仓库的clone
>
> ​	git clone+远程仓库地址

### 版本操作

> 一次次修改产生了不同版本的工作区和版本库，对版本的操作指令使得版本变成任意时间的修改操作。
>
> 版本回退

​	git reset  –hard +commit id前五位

> 版本回退至指定版本（或者最新版本）

​	版本回退原理：

> ​	git 内部有指向当前版本的HEAD指针，当版本回退时，HEAD指针仅仅指向上个版本

​	git reset --hard HEAD^

>回到上一版本

### 工作区管理

git checkout - - file 

> 丢弃修改：对工作区的修改全部撤销

 git rm file

>删除文件

使用git rm file 之后可以使用git checkout -  -file 恢复修改前的模样

git stash 

> 将当前任务“储藏”

git stash drop

> 删除git stash 的内容

git stash apply

> 恢复git stash内容

git stash pop

> 恢复的同时将stash内容删除

小结：当前任务还在进行，但不得不进行其他分支任务时，使用satsh指令保存当前任务

​			比如修改bug

### 版本库

#### 暂存区修改

git reset HEAD filename

> 当已经使用git add 提交但未进行commit，使用git reset HEAD filename
>
> 将暂存区修改撤销

git checkout - - file 

> 丢弃暂存区修改

#### 误删

> 当使用rm将工作区的文件误删时，使用git checkout - - file 的指令还
>
> > git chekout checkout 还原的原理其实是将版本库里的版本替换工作区的版本 

### 标签

创建标签

> git tag 标签名
>
> > git tag 标签名 [commit id] 创建流一个标签默认为HEAD ,也可以指定一个commit id

 git tag - a  标签名 -m“xxxx”

> 指定标签信息

git tag 

> 查看所有标签

git show 标签名 

>查看标签信息

git push origin  标签名

> 推送标签至远程仓库
>
> > 一次性推送所有标签：git push origin - - tags

git tag -d 标签名

>删除标签
>
>> git push origin ：refs/tags/tagname 可以远程删除标签

### 分支管理

git branch branchname

> 创建分支
>
> > git chekout -b branchname 创建分支并切换
> >
> > 等价于git branch 和git checkout 两条命令

git branch 

> 查看分支情况

git checkout branchname 

> 切换分支

git branch -d branch

> 删除分支
>
> > git branch -D branchname强行删除分支

git push origin（仓库名） branch

> 将分支推送至远程仓库

快速合并

git merge branch

> 将分支上的修改合并到master 上
>
> > 使用git log -- graph 可以查看分支合并图
> >
> > > 当存在分支冲突时，无法快速提交，必须优先解决冲突再提交
> > >
> > > > 冲突产生即master的修改和分支的修改发生后冲突

​		使用分支可同时进行多项任务，有助于多人协作，但是多人协作过程中冲突是存在的

> 当推送分支到远程仓库与他人发生冲突时：
>
> >		​		先用git pull 将最新的提交从origin/dev上抓取下来，在本地进行合并解决冲突再推送
> >
> >		> 在git pull 使用之前先将本地分支与远程分支链接根据提示即可（pull失败时会出现提示）

