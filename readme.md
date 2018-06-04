
Git
===
## Windows install

网上自行搜索安装git客户端

安装完成后还需要最后一步设置，在命令行输入：

    $ git config --global user.name  "Your Name"
    $ git config --global user.email "Your Email"


# 1. 先有本地仓库,后有远程库
详细内容参看： [廖雪峰Git教程-添加远程库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000)

## 创建版本库
在一个合适的目录执行以下命令：

    $ git init
将在这个目录创建一个空的仓库（empty Git repository），该目录下会多一个.git的文件夹。

## 文件添加到仓库 
### 第一步：
在工目录下添加一个文件（如readme.txt）用命令git add 告诉git，添加到仓库：

    $ git add readme.txt

### 第二步：
将文件提交到仓库：

    $ git commit -m "wrote a readme file"
    [master (root-commit) cb926e7] wrote a readme file
    1 file changed, 2 insertions(+)
    create mode 100644 readme.txt

## 关联远程仓库

### github创建仓库
 登录**github**，然后在右上角找到`"Create a new repository"`按钮，创建一个新的仓库。`Repository name`填入`git_test`，
 然后点击`"Create repository"`按钮就可以创建了新的git仓库。
### 远程仓库与本地仓库关联
    $ git remote add origin git@github.com:YourGithubName/git_test.git
### 推送到远程库
    $ git push -u origin master
由于远程库是空的，第一次推送的master分支时加上了 -u 的参数，Git不但会把本地的master分支内容推送到远程新的master分支，
还会把本地的master分支和远程的master分支关联起来，在以后的推送和拉取就可以简化命令。

# 1. 先有远程库
创建远程库，详细内容参看： [廖雪峰Git教程-从远程库克隆](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000)
在Github创建仓库后，下一步就需要 `clone` 克隆一个本地库：
`$ git clone git@github.com:YourGithubName/git_test.git`


## 关联远程库 ssh秘钥问题
你也许还注意到，GitHub给出的地址不止一个，还可以用https://github.com/michaelliao/gitskills.git这样的地址。实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。

使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。
#### 使用ssh协议
1. git命令创建SSH Key
方法参见： [廖雪峰Git教程-从远程库克隆](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000)
2. TortoiseGit 创建Key
在windows程序中，找到TortoiseGit下的Puttygen并打开，

## Git Command
除了以上提到的git命令外，介绍下其他常用命令
### 修改
- `git status`: 查看状态
- `git log `: 查看历史记录
- `git reset`: 版本退回   Git 内部有一个指向当前版本的**HEAD**指针。**HEAD**指向那个版本号，
  就把当前版本定位到那。所以用`$ git reset --head HEAD(指针)`来回退版本或者回复版本。
- `git reflog`: `HEAD`版本号可以用命令`git reflog`查看。

    $ git reflog
    ea34578 HEAD@{0}: reset: moving to HEAD^
    3628164 HEAD@{1}: commit: append GPL
    ea34578 HEAD@{2}: commit: add distributed
    cb926e7 HEAD@{3}: commit (initial): wrote a readme file
    
- `git diff HEAD -- file`: 查看工作区与版本库里面最新版本的区别。如`git diff HEAD -- readme.txt`

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
        
- `git checkout -- file`: 文件在工作区的修改全部撤销  
- `git rm`: 版本库中删除文件 
 
### 分支管理
