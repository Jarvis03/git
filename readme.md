
Git
===
## Windows install
安装完成后还需要最后一步设置，在命令行输入：

    $ git config --global user.name  "Your Name"
    $ git config --global user.email "Your Email"

## 创建版本库
在一个合适的目录执行以下命令：

    $ git init
将在这个目录创建一个空的仓库（empty Git repository），该目录下会多一个.git的文件夹。

## 文件添加到仓库 
###第一步：
在工目录下添加一个文件（如readme.txt）用命令git add 告诉git，添加到仓库：

    $ git add readme.txt

###第二步：
将文件提交到仓库：

    $ git commit -m "wrote a readme file"
    [master (root-commit) cb926e7] wrote a readme file
    1 file changed, 2 insertions(+)
    create mode 100644 readme.txt

##关联远程仓库
###github创建仓库
 登录**github**，然后在右上角找到`"Create a new repository"`按钮，创建一个新的仓库。`Repository name`填入`git_test`，
 然后点击`"Create repository"`按钮就可以创建了新的git仓库。
###远程仓库与本地仓库关联
    $ git remote add origin git@github.com:YourGithubName/git_test.git
###推送到远程库
    $ git push -u origin master
由于远程库是空的，第一次推送的master分支时加上了**-u**的参数，Git不但会把本地的master分支内容推送到远程新的master分支，
还会把本地的master分支和远程的master分支关联起来，在以后的推送和拉取就可以简化命令。

## Git Command
除了以上提到的git命令外，介绍下其他常用命令
### 修改
- `git status`: 查看状态
- `git log `: 查看历史记录
- `git reset`: 版本退回   Git 内部有一个指向当前版本的`HEAD`指针。`HEAD`指向那个版本号，
  就把当前版本定位到那。所以用`$ git reset --head HEAD(指针)`来回退版本或者回复版本。
- `git reflog`:`HEAD`版本号可以用命令`git reflog`查看。

    $ git reflog
    ea34578 HEAD@{0}: reset: moving to HEAD^
    3628164 HEAD@{1}: commit: append GPL
    ea34578 HEAD@{2}: commit: add distributed
    cb926e7 HEAD@{3}: commit (initial): wrote a readme file
    
- `git diff HEAD -- file`:查看工作区与版本库里面最新版本的区别。如`git diff HEAD -- readme.txt`

    $ git diff HEAD -- readme.txt 
    diff --git a/readme.txt b/readme.txt
    index 76d770f..a9c5755 100644
    --- a/readme.txt
    +++ b/readme.txt
    @@ -1,4 +1,4 @@
     Git is a distributed version control system.
     Git is free software distributed under the GPL.
     Git has a mutable index called stage.
    -Git tracks changes.
    +Git tracks changes of files
- `git checkout -- file`:文件在工作区的修改全部撤销  
- `git rm`:版本库中删除文件  