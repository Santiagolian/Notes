## Linux系统操作

### 文件管理

 `ls`：列出当前目录下的文件和目录，按列以字母排序。
选项：

    `-a`：列出所有文件
    `-d`:仅列出目录本身
    `-l`：列出文件的属性、权限等信息

`pwd`：显示当前所在工作目录的全路径

`cd`：切换目录

`mkdir`：创建新目录

    `-m`：配置文件权限
    `-p`：递归创建目录

`rmdir`：删除空目录

    `-p`：递归删除空目录

`rm`：移除文件或目录

    `-f`：强制删除
    `-i`：询问动作
    `-r`：递归删除

`cp`：复制文件或目录
```
格式：cp [options] source destination
```
    `-a`：相当于`-pdr`
    `-i`：询问动作
    `-p`：复制文件属性
    `-r`：递归复制

`mv`：移动文件或目录

    `-f`：强制
    `-i`：询问动作

查看文件内容
`cat`：从第一行开始显示文件内容
`tac`：从最后一行开始显示文件内容
`nl`：显示文件内容时一并显示行号
`head`：显示头几行
`tail`：显示尾几行

`vim`

按`ESC`进入命令模式
`:q`：退出
`:q!`：不保存退出
`:wq`：写入文件并退出
`:wq!`：强制写入并退出

apt命令：执行需要超级管理员权限
```
格式：apt [options] [command] [package]
```
`sudo apt update`：列出所有可更新的软件清单
`sudo apt upgrade`：升级软件包
`sudo apt install [package_name]`：升级软件包
`sudo apt remove [package_name]`：删除软件包
`apt list --installed`：列出所有已安装的包

## Git
Git是一个开源的分布式版本控制系统
### Git配置

`git --version`  显示版本信息
`git config --list`   显示已有的配置信息
`git config -e`      编辑git配置文件（针对当前仓库）
`yum remove git`      移除git
设置Git默认使用的文本编辑器
`git config --global core.editor 编辑器名`

#### 设置提交的用户信息

`git config --global user.email "github注册邮箱"`
`git config --global user.email "github用户名"`
去掉`--global`只对当前仓库有效

### Git分区
工作区：电脑中的目录
暂存区(stage或index)：一般存放在`.git`目录下的index文件中
版本库：工作区中的隐藏目录`.git`


`git init`    初始化一个Git仓库，在当前目录生成一个.git目录
`git status`  查看仓库当前的状态，显示有变更的文件

添加所有修改的文件到暂存区
`git add .`

将暂存区文件添加到本地仓库
`git commit`
`-m` 选项可在命令行中提供提交的注释
未设置`-m`选项，git将尝试打开一个编辑器来填写提交信息，默认打开vim
`git commit -m "备注信息"`    提交并备注信息
`-a` 参数设置修改文件后无须执行git add命令，直接进行提交

`git log`         查看历史提交记录
`git blame <file>` 以列表形式查看指定文件的历史修改记录

`git reset`       回退版本
`git diff`       比较文件的不同(暂存区和工作区的差异)

`git checkout`   分支切换
`git branch`      创建分支
`git merge`       合并分支
`git branch -d`   删除分支

分支合并冲突


## Git与Github

### SSH连接
1. 配置SSH密钥
`ssh-keygen -t rsa -C "github注册邮箱"`
密钥保存路径：C:\Users\Administrator/.ssh
可以使用gitbash来复制正确格式的密钥（`cat`命令）
将密钥粘贴至GitHub账户

2. 检测连接
`ssh -T git@github.com`

### 远程仓库操作
查看当前配置有哪些远程仓库（-v可看到每个别名的实际链接地址）
`git remote -v`

添加仓库origin
`git remote add origin url`

删除仓库
`git remote rm`

git提取远程仓库的更新
1. `git fetch [远程主机名]`   从远程仓库下载新分支与数据
2. `git merge`                将远程仓库的分支合并到当前分支                            

推送本地的分支到远程origin
`git push -u origin 分支名`
下载远程代码并合并
`git pull` = git fetch + git merge

fork

`git clone <repo> `   将远程Git仓库拷贝到本地  

master是Git的默认分支名

origin是Git克隆的仓库服务器的默认名

