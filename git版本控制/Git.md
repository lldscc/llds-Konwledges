
## git常用命令

```bash
git init                 //在当前目录中初始化一个新的Git仓库。git init -b <分支名称> 
git add <file>           //将文件添加到暂存区，准备提交。常用git add .
git commit -m "commit message"     //将暂存区的更改提交到本地仓库，并添加提交消息。
git push                           //将本地的更改推送到远程仓库。

git remote add <remote-name> <repository-url>   //添加一个新的远程仓库。并换
git clone <repository-url>                      //克隆一个远程仓库到本地。
git remote remove <remote-name>                 //移除指定的远程仓库。

git remote -v          //查看已配置的远程仓库列表。
git status             //查看当前工作目录和暂存区的状态。
git log                //查看提交历史记录。

git branch -b 分支名        //创建分支
git branch -m master main    //修改本地分支为mian
git push -u origin main     //将本地main分支推送到远程仓库
git branch                   //查看本地分支列表。
git checkout <branch-name>  //切换到指定的分支。
git merge <branch-name>    //将指定分支的更改合并到当前分支。


git config user.name   /查看当前Git账户的用户名
git config user.email  //示当前配置的Git邮箱
git config --list   //所有的Git配置信息

```

## ssh身份绑定

### 获取ssh密钥

```
ssh-keygen -t rsa -C “git账号”    //生成.ssh文件夹下的id_rsa.pub
ssh-keygen -t rsa -b 4096 -C "changllds666@gmail.com"   //名称：id_rsa id_ecdsa id_ed25519


ssh -T git@github.com     //验证当前用户

```

### 身份绑定

```
//全局
git config --global user.name “git账号”
git config --global user.email “git邮箱，注册时候的邮箱”  
//局部
git config  user.name “git账号”
git config  user.email “git邮箱，注册时候的邮箱”
```

## 推送步骤

```
git init 
git add .
git commit "xx"
git remote  add origin ssh地址
git push origin main
```





## gitignore文件

### 添加语法：
项目根目录创建`.gitignore`文件，添加要忽略的文件

#### 一般情况

```gitignore
# 每一项配置独占一行
# 每一行可以是：文件名，路径，或者正则表达式匹配模式
.vscode
a.txt
```
#### 复杂情况

1. 空行不匹配任何文件，因此常用作分隔符（以方便阅读）。
2.  用于注释，\ 表示转义（如对 a!bc.txt，需改为 a\!bc.txt）。
3.  可以匹配任何字符(0或多次)，? 可以匹配任何字符(1次)
4. 当 / 在开头时，表示从项目根目录开始匹配。否则，下级都将匹配。
	/abc 只能匹配 /abc，不能匹配 /x/abc 或 /x/y/abc等。
5.  当 / 在末尾时，只匹配目录，否则，则同名的目录和文件都将匹配。
	举例：  /abc/ 只能匹配 /abc目录，不能匹配/abc文件。
	举例：  abc/ 能匹配 /abc/ 或 /x/abc/ 或 /x/y/abc/等，不能匹配 /abc 或 /x/abc 等。
```gitignore
# 每一行可以是：文件名，路径，或者正则表达式匹配模式
/src/temp/   #目录路径
*.log        #匹配.log结尾的文件
```

### 规则检查命令
```bash
git check-ignore -v {文件或者路径}
```
有输出则表明这个文件被忽略了


> [gitignore忽略文件](https://www.bilibili.com/read/cv19909520/)



## 分支管理
**分为主分支(main)与开发分支(dev)**
```bash

git branch                   //查看本地分支列表。
git init -b <分支名称>        //同时初始化仓库并创建一个分支
git branch  <分支名称>        //创建一个分支
git branch -m master main    //修改本地分支为mian
git checkout <分支名>      //切换到指定的分支。
git branch -D <分支名称>     //删除分支
git merge <branch-name>    //将指定分支的更改合并到当前分支。
```

##  tag标签管理

![image-20231018172345649](https://cdn.jsdelivr.net/gh/Shuncsx/image/git-tags.png)

```bash
git  log --oneline		//查看提交历史日志
git tag			        //查看当前仓库中的所有标签
git show <标签名>		//详细信息

git  tag v1.0			       //创建轻量标签
git	tag -a <标签名> -m <备注>	//创建注释标签

git tag -d <标签名>						//删除本地标签
git push origin -d tag <标签名1> <标签名2>  //删除本地标签

git push origin <标签名>		  //推送标签到远程仓库
git push origin --tags			//推送全部
```





## Github-fork/PR

fork：分叉，服务端的代码仓库克隆

PR：Pull Request 贡献回原仓库



















```
Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git status
On branch cate
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   manifest.json
        modified:   pages/cate/cate.vue

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        project.config.json
        project.private.config.json

no changes added to commit (use "git add" and/or "git commit -a")

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git add .
warning: in the working copy of 'manifest.json', LF will be replaced by CRLF the next time Git touches it

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git status
On branch cate
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   pages/cate/cate.vue
        new file:   project.config.json
        new file:   project.private.config.json


Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git commit -m"分类页面"
[cate 16939d2] 分类页面
 3 files changed, 191 insertions(+), 2 deletions(-)
 create mode 100644 project.config.json
 create mode 100644 project.private.config.json

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git push -u origin cate
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 16 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 2.58 KiB | 2.58 MiB/s, done.
Total 7 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'cate' on GitHub by visiting:
remote:      https://github.com/lldscc/Heima-weixinMinProject/pull/new/cate
remote:
To github.com:lldscc/Heima-weixinMinProject.git
 * [new branch]      cate -> cate
branch 'cate' set up to track 'origin/cate'.

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (cate)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (main)
$ git merge cate
Updating c71c475..16939d2
Fast-forward
 pages/cate/cate.vue         | 158 +++++++++++++++++++++++++++++++++++++++++++-
 project.config.json         |  28 ++++++++
 project.private.config.json |   7 ++
 3 files changed, 191 insertions(+), 2 deletions(-)
 create mode 100644 project.config.json
 create mode 100644 project.private.config.json

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (main)
$ git push
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:lldscc/Heima-weixinMinProject.git
   c71c475..16939d2  main -> main

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (main)
$ git branch -d cate
Deleted branch cate (was 16939d2).

Lenovo@llds MINGW64 /f/Github-lldscc/weixin-小程序 (main)
$

```



