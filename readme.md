
Git
===
## Windows install
  安装完成后还需要最后一步设置，在命令行输入：
  $ git config --global user.name  "You Name"
  $ git config --global user.email "You Email"
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