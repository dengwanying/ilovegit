#git 入门

##一,创建库
git init
##二,添加文件
###第一步, git add
例如:git add readme.txt

注:可反复多次使用,添加多个文件.

###第二步,git commit
git commit -m 

例如:git commit -m "wrote a readme file",-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

注:可以一次提交很多文件

                 git add file1.txt
                 git add file2.txt file3.txt
                 git commit -m "add 3 files."
如果不git add 到暂存区,就不能加入到 commit中.
   
##三,查看
git status

此命令可以让我们时刻掌握仓库当前的状态,随时使用

git diff  

例如:git diff readme.txt用来查看修改内容

git diff HEAD -- readme.txt

查看工作区和版本库里面最新版本的差别

git log

此命令显示从最近到最远的提交日志(回退)

    git log --pretty=oneline

解决输出信息太多的问题,查看版本号.如果使用可视化工具查看Git历史，就可以更清楚地看到提交历史的时间线,怎么看??

HEAD表示当前版本,HEAD^是上一个,HEAD^^是上上个,往上100个版本写作HEAD~100

git reset

例如:git reset --hard HEAD^从当前版本回退到上一个版本
git reset --hard <版本号前几位> 回到指定的某一版本

cat

例如:cat readme.txt查看文档内容

git reflog 

用来记录每一次命令(重返未来)

##四,撤销修改
git checkout -- readme.txt

让这个文件回到最近一次git commit或git add时的状态.

git reset HEAD readme.txt

将暂存区的修改撤销掉,重新放回工作区

     丢弃工作区修改用git checkout --file
     添加到暂存区后,想丢弃修改,用git reset HEAD file,再用上一步
     已经提交版本库再修改,用版本回退
     
git rm test.txt
删除一个文件,如果一个文件已经被提交到版本库,则不用担心误删,但是只能恢复文件到最新版本,会丢失最近一次提交后修改的内容.
        

##从远程克隆
git clone
例如:git clone https://...

##分支管理

git branch查看分支

git branch <name>创建分支

git checkout <name>切换分支

git checkout -b <name>创建+切换分支

git merge<name>合并某分支到当前分支

git branch -d <name>删除分支

git log --graph命令可以看到分支合并图
例如git log --graph --pretty=oneline --abbrev-commit??为何具体操作如此??

       当git无法自动合并分支时,就必须首先解决冲突问题,解决冲突后,再提交,合并完成.
       
合并分支时,加上--no-ff参数就可以用普通模式合作,合并后的历史有分支,能看出曾经合并,而fast forward合并就看不出曾经做过合并.

###bug分支管理
git stash暂时"储存"现场

git stash list查看"储存"

git stash apply恢复储存

git stash drop删除储存

git stash pop 恢复现场+删除储存

###feature分支管理
开发新功能,最好新建一个feature

git branch -D <name>强行删除一个没有被合并过的分支.