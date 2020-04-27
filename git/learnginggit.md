#git实践小结
## 情景一
<br/> 在本地的工作目录中,如果已经commit了,但是发现commit中有些不妥的地方,或者有两个文件不想提交怎么办?</br>
方案一:如果是commit中的注释写错了,想重新提交的话,只需要:   
<center><font color = red>git commit --amend</center> </font>  
此时会进入默认的vim编辑器,修改注释完毕后保存就好了.  
方案二:git reset 命令和参数  
git reset --soft HEAD^ &nbsp; 不删除工作区间改动的代码,撤销commit操作,但不撤销git add操作  
git reset --mixed HEAD^ &nbsp; 不删除工作区间改动的代码,撤销commit操作,同时也撤销git add的操作  
git reset --hard HEAD^ &nbsp; 删除工作区间改动的代码,撤销commit操作和git add的操作  

commit push 代码已经更新到远程仓库,想取消修改

对于已经把代码push到线上仓库,你回退本地代码其实也想同时回退线上代码,回滚到某个指定的版本,线上,线下代码保持一致.你要用到下面的命令

git revert commitid

revert 之后你的本地代码会回滚到指定的历史版本,这时你再 git push 既可以把线上的代码更新。

 

注意：git revert是用一次新的commit来回滚之前的commit，git reset是直接删除指定的commit，看似达到的效果是一样的,其实完全不同。

第一:上面我们说的如果你已经push到线上代码库, reset 删除指定commit以后,你git push可能导致一大堆冲突.但是revert 并不会.
第二:如果在日后现有分支和历史分支需要合并的时候,reset 恢复部分的代码依然会出现在历史分支里.但是revert 方向提交的commit 并不会出现在历史分支里.
第三:reset 是在正常的commit历史中,删除了指定的commit,这时 HEAD 是向后移动了,而 revert 是在正常的commit历史中再commit一次,只不过是反向提交,他的 HEAD 是一直向前的.

##情景二
如果文件不小心git add将文件提交到暂存区域,想取消这个操作   
使用git status给出的建议:  
git reset HEAD files...取消暂存  
如果想将修改的文件保持和版本中一模一样的版本,可以使用 git checkout file进行操作  
##情景三
