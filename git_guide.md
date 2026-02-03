git是本地的，github的远程仓库才是起到云端备份的作用

**处理网络问题最稳定的办法：VPN，假如端口是7890，该仓库第一次用git时要在命令行输入**
```bash
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890

git config --global --get http.proxy #用于验证，若执行输出http://127.0.0.1:7890则成功了
```

若多人协作，建议各自创立一个branch，这样在merge的时候不容易报错
```bash
git checkout -b [新分支名]  #创立一个新分支，并切换过去
此时你的分支名仅创建在本地，需要发布到远程仓库
git push -u origin [新分支名]  #将新分支发布到远程仓库，并将本地分支和远程分支关联。这样就可以正常使用了

git branch #查看当前所有分支，*号表示当前所在分支
git checkout [分支名] #切换到指定分支
```

**tips**
1. git remote可以查看当前git仓库名
2. 默认分支名起origin
3. git remote rename [当前仓库名] origin  #重命名

**Git常用命令汇总：**
```bash
git status
## check the status of the working directory and staging area, red files are modified but not staged, green files are staged

git add [file_name]
## stage the specified file for commit

git add .
## stage all modified and new files for commit

git commit -m "commit message"
## commit the staged changes with a descriptive message to the local repository

git push origin [branch_name]
## push the committed changes to the specified remote repository and branch

##you can set the default git_name and branch_name using:
git push -u origin [branch_name]
## in the future, you can simply use 'git push' without specifying the remote and branch

git pull origin [branch_name]
## fetch and merge changes from the specified remote repository and branch to the local repository

## you can set the default git_name and branch_name using:
git pull -u origin [branch_name] 
## in the future, you can simply use 'git pull' without specifying the remote and branch

git push origin [branch_name] --force  
## use the local git repository to overwrite the remote repository

git reset --hard [commit_id]
## reset the current branch to the specified commit_id, discarding all changes after that commit
```


