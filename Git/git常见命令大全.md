git init: 在当前目录下初始化一个新的 Git 仓库。      
git clone [url]: 从远程仓库克隆项目到本地。    
git add [file]: 将指定文件或文件夹添加到暂存区。      
git status: 显示工作区的状态，包括已修改、已暂存和未跟踪的文件。      
git diff: 显示未暂存的文件和上次提交之间的差异。       
git commit -m "message": 将暂存区的文件提交到版本库，并附上提交消息。      
git log: 显示提交历史记录。     
git branch: 显示当前分支列表，以及当前所在分支。    
git checkout [branch_name]: 切换到指定分支。        
git checkout -b [branch_name]: 创建并切换到新的分支。      
git merge [branch_name]: 将指定分支合并到当前分支。        
git pull: 从远程仓库拉取最新版本到本地。        
git push: 将本地提交推送到远程仓库。            
git remote -v: 显示远程仓库的详细信息。             
git reset [file]: 从暂存区中移除指定文件，但保留在工作区中的修改。        
git reset --hard: 重置暂存区和工作区，将它们恢复到上次提交的状态。       
git tag [tag_name]: 给当前提交打标签。        
git rm [file]: 从版本控制中删除指定文件，并将其从工作目录中删除。    

git stash：         
当你正在进行一些工作，但突然需要切换到另一个分支去做一些其他的工作时，但你又不想提交当前的修改，也不想创建一个新的分支来保存这些修改时，你可以使用 git stash 命令。     
git stash 会将当前工作目录中未提交的修改存储到一个临时堆栈中，然后将工作目录恢复到最后一次提交时的状态，以便你可以在其他分支上工作。       
当你完成其他任务后，可以使用 git stash pop 命令来恢复之前暂存的修改，并将其应用到当前工作目录中。      

git fetch：       
当你想要查看远程仓库中的最新变更，但又不想立即合并这些变更到本地分支时，你可以使用 git fetch 命令。       
git fetch 会从远程仓库下载最新的变更，但不会自动将其合并到本地分支中。它会将远程分支的变更保存到本地仓库中的一个隐藏分支中。     
一旦使用 git fetch 下载了最新的变更，你可以使用其他命令（如 git merge 或 git rebase）来将这些变更合并到你的本地分支中。     

一旦使用 git fetch 下载了远程仓库的最新变更，你可以使用以下命令来查看这些变更：       

查看远程分支列表： 使用 git branch -r 命令可以列出所有远程分支，包括远程仓库的最新状态。      
```code
git branch -r
```
查看远程分支的详细信息： 使用 git log 命令结合远程分支名称可以查看远程分支的提交历史和详细信息。        
```code
git log origin/<branch_name>
```
查看远程仓库的所有分支及其最新状态： 使用 git remote show <remote_name> 命令可以查看远程仓库的详细信息，包括所有分支的情况。      
```code
git remote show origin
```
通过这些命令，你可以随时查看远程仓库的最新状态和变更，然后决定是否要将这些变更合并到你的本地分支中。         
