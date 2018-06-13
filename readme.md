1、将当前目录变成git可以管理的仓库，即工作区（本地仓库）：git init

2、把文件放入git仓库：1）、git add 文件 或 git add .     2）、git commit -m '说明信息' 

3、查看仓库状态命令，如果有修改文件，会有“modified:修改的文件”提示信息：git status 

4、比较文件不同：git diff 文件名（如果不输入文件名，会显示所有更改的差别，且不会退出当前命令状态，键入q退出该状态）

5、查看提交历史记录：git log

6、git当前版本是head，上一版本是head^，上上版本是head^^，以此类推，也可以写成head~100表示上一百版本；退回到上一版本：git reset --hard head^（再去看修改的文件已经还原到上一版本了）

7、如果不想退回了，想还原到没退回之前版本，如下操作：1）、git reflog 命令找出操作记录，第一列为提交时ID　　2）、git reset --hard 提交ID 即可

8、对比当前文件与仓库文件区别：git diff head -- 文件名

9、如果没有执行git add命令，将文件还原到仓库最新版本：git checkout -- 文件名

10、如果执行过git add命令没有执行过git commit命令：1）、git reset head 文件名　　2）、git checkout -- 文件名

11、如果执行了git commit，就要用第6步，执行退回到指定历史记录

12、删除文件（先本地删除）：1）、git add . （或者 git rm 文件名）　　2）、git commit -m '提交信息'

13、如果本地删除，通过git重新获取：git checkout -- 文件名

14、将当前项目加入到github（前提是注册并通过SSH建立信任连接，参考此处）：1）、在GitHub上创建同名仓库　　2）、根据提示先将本地仓库与GitHub仓库关联，命令如    git remote add origin https://github.com/hujiapeng/learngit.git（origin此处的作用是给远程仓库起一个名字，也可以改成别的，但习惯是叫origin）3）、推送当前项目或修改到GitHub，命令如   git push -u origin master（-u参数是将本地仓库与GitHub仓库做关联，此处关联的是origin的master，以后推送就不用-u参数了）

15、远程仓库下载：git clone 远程仓库地址（clone or download 下拉窗，右上角可以选择use https或者use ssh）

 16、创建并切换到dev分支：git checkout -b dev　　也可以把创建和切换分开操作，1）创建dev分支：git branch dev 2）切换到dev：git checkout dev

17、查看当前分支：git branch（前面带*的分支为当前操作的分支）

18、在dev分支下修改文件后，add,commit后，更改记录只保存在当前分支，如果切换回master分支，再查看修改过的文件，修改的记录没有了

19、切换回master分支后，将dev分支合并到master：git merge dev（将dev分支合并到当前分支）

20、再去查看修改的文件，修改的内容可以看到了，此时已经合并，所以可以将dev分支安全的删除了：git branch -d dev

21、如果不同分支上修改同一文件同一行，不同分支在add和commit后，在执行merge命令时会出现冲突，需要手动合并冲突文件（git用<<<<<<<，=======，>>>>>>>标记不同分支内容），再在master分支上add和commit，然后可以正常删除其他分支了

22、查看分支合并情况：git log --graph --pretty=oneline --abbrev-commit　　（或git log --graph）