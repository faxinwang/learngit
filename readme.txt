创建仓库
-->git init

添加文件到缓存区
-->git add file1.txt file2.txt file3.txt
-->git add *.java *.cpp

把文件提交到本地仓库
-->git commit -m "提交内容的描述"

查看当前缓存区状态
-->git status

查看某文件最近一次修改的内容
-->git diff file.txt
查看工作区和版本库某文件的区别
-->git diff HEAD -- file.txt

查看提交历史
详细信息:
-->git log
-->git reflog
简单信息:
-->git log --pretty=online
图像表示:
-->git log --graph

回到上一个版本
-->git reset --hard HEAD^
回到上上一个版本
-->git reset --hard HEAD^^
回到前n个版本
-->git reset --hard HEAD~n
回到特定版本
-->git reset --hard HEAD commitID

丢弃工作区当前的修改
-->git checkout -- file.txt
将已添加到缓存区的文件撤销放回工作区
-->git reset HEAD file.txt

显示文件内容
-->cat file.txt

删除工作区中文件
-->rm file.txt
删除git仓库中的文件
-->git rm file.txt
如果工作区中的文件被误删,可以从git仓库中还原
-->git checkout -- file.txt

使用远程仓库:
-->ssh-keygen -t -rsa -C "myemail@abc.com"
运行该命令后, 在用户主目录下的.ssh目录中有id_rsa和id_rsa.pub两个文件分别保存私钥和公钥
然后登陆GitHub，打开“Account settings”，“SSH Keys”页面,点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

添加远程仓库:
1.先在github上创建一个仓库
2.正在本地运行如下git命令
-->git remote add origin git@github.com:userName/reposName.git
3.将本地内容推送到远程仓库(将当前master分枝推送到远程仓库,-u命令可让本地master分枝与远程master分枝关联起来,
  以后推送就可以简化命令git push origin master)
-->git push -u origin master

将远程仓库克隆到本地
-->git clone git@github.com:username/reposName.git

创建并切换到新分枝
-->git checkout -b <BranchName>
相当于如下两条命令(创建分枝, 切换分枝)
-->git branch <name>
-->git checkout <BranchName>

查看所有分枝,以及当前处于那一个分枝
-->git branch

合并分枝(首先切换到master分枝)
-->git merge <Bname>
禁用fast-forward模式(因为本次合并会新建一个commit, 所以用-m 参数添加描述信息)
-->git merge --no-ff -m "merge with no-ff" <BName>
删除分枝
-->git branch -d <Bname>

保存工作现场
-->git stash
查看所有保存的工作现场
-->git stash list
stash@{0}: WIP on dev: 6224937 add merge
恢复并删除最近一次保存的工作现场
-->git stash pop
恢复到指定的工作现场
-->git stash apply stash@{n}
删除指定的工作现场
-->git stash drop stash@{n}

查看远程仓库列表(加-v可查看详细信息)
-->git remote (-v)

添加标签(标签都是打到某一个commit上,默认是HEAD上)
-->git tag <TagName> 
添加标签到特定的commit上
-->git tag <Tname> commitID
指定标签信息
-->git tag <Tname> -m "add some comments"
查看所有标签
-->git tag
查看特定标签的提交信息
-->git show <Tname>
创建的标签都保存在本地,使用如下命令将特定标签推送到远程
-->git push origin <Tname>
一次性将本地未推送的标签全部推送到远程
-->git push origin --tags
删除本地标签
-->git tag -d <Tname>
删除远程标签
-->git push origin :refs/tags/tName
