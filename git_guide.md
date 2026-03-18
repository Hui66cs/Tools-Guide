    git是本地的，github的远程仓库才是起到云端备份的作用

**处理网络问题最稳定的办法：VPN，假如端口是7890，该仓库第一次用git时要在命令行输入**
```bash
#vpn代理时
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890

git config --global --get http.proxy #用于验证，若执行输出http://127.0.0.1:7890则成功了

#不用vpn时
git config --global --unset http.proxy
git config --global --unset https.proxy
```

若多人协作，建议各自创立一个branch，这样在merge的时候不容易报错
```bash
初始化仓库时发布分支遇到问题
git pull origin main --allow-unrelated-histories  #将远程main分支拉取到本地，允许合并不相关的历史记录
git branch [新分支名]  #创立一个新分支,但没切换过去
git checkout [分支名]  #切换到指定分支
git checkout -b [新分支名]  #创立一个新分支，并切换过去
此时你的分支名仅创建在本地，需要发布到远程仓库
git push -u origin [新分支名]  #将新分支发布到远程仓库，并将本地分支和远程分支关联。这样就可以正常使用了

git branch #查看当前所有分支，*号表示当前所在分支
git branch -d [分支名] #删除本地分支
```

拉取别人的仓库到本地
```bash 
git clone [仓库地址]
```
此时本地仓库会自动与远程仓库关联，默认仓库名为origin

将自己的本地仓库与远程仓库关联
```bash
git remote add origin [URL]
```
注意：如果远程仓库创建时选择了README.md等文件，远程仓库就不是空的了，这时直接git push会报错。需要先将远程仓库拉取到本地，合并后再push（远程仓库提交的是main分支，而本地默认是master分支导致的）

**tips**
1. git remote可以查看当前git仓库名
2. 默认分支名起origin
3. git remote rename [当前仓库名] origin  #重命名

**Git常用命令汇总：**
```bash
git init #将本地文件夹初始化为git仓库

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

## in the future, you can simply use 'git pull' without specifying the remote and branch

git push origin [branch_name] --force  
## use the local git repository to overwrite the remote repository

git reset --hard [commit_id]
## reset the current branch to the specified commit_id, discarding all changes after that commit
```

**gitignore**
.gitignore文件用于指定哪些文件或文件夹不应该被git跟踪和提交到版本控制系统中。常见的用途包括：
1. 忽略编译生成的文件，如`.class`、`.o`等
2. 忽略日志文件，如`.log`
3. 忽略操作系统生成的文件，如`.DS_Store`（macOS）或`Thumbs.db`（Windows）
4. 忽略敏感信息，如包含密码的配置文件

使用方法：在.git同级目录下创建一个名为.gitignore的文件，里面内容为：
```
# --- 操作系统临时文件 ---
.DS_Store
Thumbs.db
desktop.ini

# --- 编辑器/IDE 配置 ---
.vscode/
.idea/
*.sublime-project
*.sublime-workspace

# --- Python 运行产生的文件 ---
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
venv/
pip-log.txt
setup.cfg

# --- Conda/虚拟环境 ---
.conda/
.env
.venv

# --- 数据集与大型模型（重要！AI项目常见） ---
# 建议不要把巨大的数据集和权重文件传到 GitHub
# 如果文件大于 50MB，GitHub 会警告；大于 100MB 会报错
datasets/
data/
*.zip
*.tar.gz
*.pth
*.h5
*.onnx
*.weights

# --- 日志与临时文件 ---
logs/
*.log
temp/
```
说明：
- `#`开头的行是注释
- `folder/`表示忽略整个文件夹及其内容
- `*`表示通配符，匹配任意字符。如*.zip表示忽略所有.zip结尾的文件
- 可以根据项目需要自定义忽略规则，确保不必要的文件不会被提交
- `!`表示取反。如`!important.log`表示忽略所有.log文件，但important.log不会被忽略



