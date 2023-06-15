# datawork


jk.zhou's learning record about datawork。



# pydatawork

###### Thu Jun 15 22:50:22 CST 2023

制作了一个datawork库，名为pydatawork，在尝试阶段，只添加了测试内容。

可以正常通过pip安装：

```shell
pip3 install pydatawork
```


# Git使用方法


###### Thu Jun 15 23:09:56 CST 2023

git维护指令：

```shell
cd到datawork文件夹
git pull # 从远程拉取，确保远程端的内容都存到了本地——如果不一致，会提示优先处理完毕，该怎么处理怎么处理，以便让本地和远程端保持同步，避免冲突。每次都这么做，养成习惯，避免不必要的同步冲突
git status # 查看同步状态是否正常
git add .  # 暂存更改，为提交做准备
git commit -m "备注" # 说明此次维护做了什么，作为笔记记录 
git push 或 git push origin datawork 或 git push origin datawork:datawork，意思是将本地的 datawork 分支 推送到 远程端 origin 主机上的 datawork 分支。本地端和远程端要分清。远程端主机，默认就是写成 origin。在终端输入 git status 后，也能看到提示，提示会说明本地分支是 datawork，远程分支是 origin/datawork。

```


###### Wed Apr 5 15:24:18 CST 2023

开始使用git，配置好之后，下载了很多感兴趣的项目。

在linux系统上操作很方便，据说在linux中“一切皆文件”，所以每个操作过程都比较容易理解，如果是在windows中，那就得先去安装某个工具才行，路径就有点曲折了，刚接触时容易因为陌生和繁琐而放弃。


下载项目源码的指令为：

```shell
ssh git@github.com # 配置好之后，在终端执行这个命令，这时候会进行的过程是【让存在github的公钥和存在本地的私钥匹配上，以建立连接，这时候需要输入钥匙密码】
git init # 新建或进入某个文件夹，在该文件夹打开终端，输入指令，这时候会在该文件夹建立一个.git配置文件
git clone url # 获取某个项目的SSH下载链接，url指链接
```

初始配置需要用到的指令：

```shell
echo "# site-navigation" >> README.md # 指定文件夹和文件？？
git init #初始化git
git add . #将本地代码提交到暂存区
git commit -m "first commit" #提交到本地仓库
git remote add origin https://github.com/ideshun/site-navigation.git # 添加远程仓库。 1）第一次提交，需要先连接远程库；2）如果提示origin已存在，可以先用 git remote rm origin删除，然后重新执行
git push -u origin master #将本地的代码提交到远程仓库的master分支。 1）我的库的主分支改成datawork了，就需要修改。

# 特别说明（2023.6.15）：第一次操作时，由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需 git push origin master。这里的origin指远程主机，master指本地分支名字，如果是默认值，就是master。如果已经改了，完整操作是：git push origin 本地分支名字：远程分支名字

```

后续维护常用指令：

```shell
git pull # 每次提交代码之前，养成良好的习惯，先 pull 一下代码，每次都这么做
git status # 随时敲git status 随时有惊喜
git add . # 此命令会把所有更改的文件全部暂存起来
git add temp.txt # 如果要单个来，只需要 . 替换成对应的文件名即可
git commit -m "xxx" # 提交并加上注释说明改动了什么。1)-m 参数表示可以直接输入后面的 message，简要说明这次改动。2)每次 git commit之后，都会在本地版本库中生成一个 哈希值，就是 commit-id,这个 id 在进行版本回退的时候有大用。3)加的 -a 参数可以将所有已跟踪文件中的执行修改或删除操作的文件都提交到本地仓库，即使它们没有经过git add添加到暂存区。例如：`git commit -a -m "xxx"`
git push <远程主机名> <本地分支名>：<远程分支名> # 推送到远程端。 1)git push 的命令格式一般为：push <远程主机名> <本地分支名>：<远程分支名> 。例如：git push origin master:master。2)我在远程端和本地名字都叫datawork，写的时候，应写为origin datawork:datawork （注意，origin这个词是固定的单词）。3)当然，一般情况下，我们都不用写后面的，直接 git push 即可,或者，直接使用 git push origin datawork。

# 特别说明(2023.6.15)：要完整写的话，是：git push origin datawork:datawork。上面命令表示，将本地的datawork分支推送到origin主机的datawork分支。如果后者(第二个datawork)不存在，则会被新建。如果省略本地分支名(第一个datawork)，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。
```

# 参考文献

教程：

1、@带甜味的盐@ 《Git提交代码完整流程》：https://blog.csdn.net/s_y_w123/article/details/112465793

2、@梦魇 《手把手教你用git上传项目到GitHub：》https://zhuanlan.zhihu.com/p/193140870

3、《新手创建第一个GitHub项目，一步一步将本地项目提交到GitHub》：https://cloud.tencent.com/developer/article/1595821

4、@gblfy 《git push -u origin master和git push 远程主机名 本地分支名:远程分支名作用》：https://blog.csdn.net/weixin_40816738/article/details/105109944

5、@林皮皮s 《使用git将本地项目推送到远程仓库github》：https://www.jianshu.com/p/b1f9f684fac8

——————————————

联系方式：zhouqiling_bjfu@foxmail.com

