# datawork


jkzhou's learning record about datawork.



# 使用记录

###### Wed Apr 5 15:24:18 CST 2023

开始使用git，配置好之后，下载了很多感兴趣的项目。

在linux系统上操作很方便，据说在linux中“一切皆文件”，所以每个操作过程都比较容易理解，如果是在windows中，那就的先去安装某个工具才行，路径就有点曲折了，刚接触的人容易因为陌生和繁琐而放弃。


下载项目源码的指令为：

```shell
ssh git@github.com 
# 配置好之后，在终端执行这个命令，这时候会进行的过程是【让存在github的公钥和存在本地的私钥匹配上，以建立连接，这时候需要输入钥匙密码】
git init 
# 新建或进入某个文件夹，在该文件夹打开终端，输入指令，这时候会在该文件夹建立一个.git配置文件
git clone url 
# 获取某个项目的SSH下载链接，url指链接
```

常用指令：

```shell
echo "# site-navigation" >> README.md 
# 指定文件夹和文件？？
git init 
#初始化git
git add . 
#将本地代码提交到暂存区
git commit -m "first commit" 
#提交到本地仓库
git remote add origin https://github.com/ideshun/site-navigation.git 
# 添加远程仓库。 1）第一次提交，需要先连接远程库；2）如果提示origin已存在，可以先用 git remote rm origin删除，然后重新执行
git push -u origin master 
#将本地代码提交到远程仓库的master分支。 1）我的库的主分支叫datawork，就需要修改
```

常用指令理解：

```shell
git pull 
# 每次提交代码之前，养成良好的习惯，先 pull 一下代码。不 pull 代码万一导致代码冲突了就不美了
git status 
# 随时敲git status 随时有惊喜
git add . 
# 此命令会把所有更改的文件全部暂存起来
git add temp.txt 
# 如果要单个来，只需要 . 替换成对应的文件名即可
git commit -m "xxx" 
# 提交并加上注释说明改动了什么。1)-m 参数表示可以直接输入后面的 message，简要说明这次改动。2)每次 git commit之后，都会在本地版本库中生成一个 哈希值，就是 commit-id,这个 id 在进行版本回退的时候有大用。3)加的 -a 参数可以将所有已跟踪文件中的执行修改或删除操作的文件都提交到本地仓库，即使它们没有经过git add添加到暂存区。例如：`git commit -a -m "xxx"`
git push <远程主机名> <本地分支名>：<远程分支名> 
# 推送到远程端。 1)git push 的命令格式一般为：push <远程主机名> <本地分支名>：<远程分支名> 。例如：git push origin master:master。2)我在远程端和本地名字都叫datawork，不叫master。3)当然，一般情况下，我们都不用写后面的，直接 git push 即可
```

参考教程：

1、@带甜味的盐@ 《Git提交代码完整流程》：https://blog.csdn.net/s_y_w123/article/details/112465793

2、@梦魇《手把手教你用git上传项目到GitHub：》https://zhuanlan.zhihu.com/p/193140870

3、《新手创建第一个GitHub项目，一步一步将本地项目提交到GitHub》：https://cloud.tencent.com/developer/article/1595821


——————————————

联系方式：zhouqiling_bjfu@foxmail.com

