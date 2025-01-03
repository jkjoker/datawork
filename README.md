# introduction

jk.zhou's datawork.


# datawork (desktop app, windows)


**简介**：
datawork是一个本地知识库工具，支持本地markdown全文检索与提取，支持多选项卡记纯文本笔记，支持国内外AI大模型调用，支持ollama和部分第三方大模型api供应商，旨在帮助个人更好地用上自己的知识和通过AI调用知识。项目基于python的tkinter构建，目前已支持windows。


datawork v3.0 for windows 已发布：【全新支持本地向量知识库】
https://github.com/jkjoker/datawork/releases

临时链接：（坚果云，datawork v3.0.6 for windows）
https://www.jianguoyun.com/p/Deu-BHEQtuX_CRjU4-YFIAA


**设计理念**：
在某程度上，datawork算是“集成”了obsidian、python和ai，是把笔记、自动化与大模型三者的能力结合起来了，我希望每个人在日常生活和工作中都能得到这三者的联合助力，然后能更好地关注自己的想法和思考、所面对的每一项真实业务，以及在每一次行动中有效积累。


**致谢**：
感谢cursor、claude-3.5-sonnet-20240620在datawork开发过程中提供的坚强助力。
如果您在使用过程中有任何建议和想法，或发现软件存在漏洞，欢迎给我发邮件，也欢迎在github提交issue，非常感谢！

**使用场景**：
- 通过关键词从多个obsidian库按指定模式提取内容，供进一步研究。
- 通过ollama调用本地大模型，探索ai。
- 通过api调用国内外主流大模型（openai、claude、gemini、零一万物、kimi、智谱、讯飞、混元、通义千问、deepseek等），探索ai。
- 通过第三方api供应商接入大模型，探索ai。
- 在同一个会话窗口调用不同大模型，探索ai。
- 精准控制多轮会话和提示词，探索ai。
- 自定义agent，调用任何喜欢的api，为每个agent设定语言风格、行为原则。
- 同时与多个agent对话。
- 选择多个agent参与主题讨论，设定主题与轮数后，agent自行参与指定主题的讨论。
- 完备的prompt管理。
- 在agent对话中使用prompt，将其当作“知识库”功能来使用。
- 在桌面随手记笔记，通过多选项卡常置多条笔记，笔记自动保存到指定位置，如obsidian的某个文件夹。
- 更多场景...

**功能特性**：
- 知识库：检索与提取。内置3种信息提取模式；支持多关键词+二次检索实现完整、精准且高度的检索；也支持自定义正则表达式检索与提取。
- 笔记：记笔记。支持自动保存；支持多选项卡；支持callout；可与obsidian等第三方编辑器同时使用。
- AI：对话。支持结构化提示词，可自定义系统级prompt；支持精准控制多轮会话准确度；可通过日志查看功能调用链及响应；自定义agent；多agent对话；多agent自动主题讨论。
- 本地向量知识库：支持本地向量知识库，需授权使用。
- 日志：查阅。支持查看程序运作逻辑链条，了解背后的数据处理原理；
- 其他：支持窗口置顶、全局快捷窗口、检索结果和聊天记录导入导出等。

**数据安全**：
- 免安装；
- 无注册无登录；
- 不索引本地文件；
- 不绑定任何文件或文件夹；
- 不联网（仅使用第三方AI供应商的api服务时需要使用网络）。

**使用方法**：
- 1.下载压缩包到本地，解压。解压后文件夹中包括一个.exe程序和一个图标。
- 2.将整个解压后的文件夹（包括.exe和图标）放到任何位置。
- 3.使用时，双击.exe即可启动。.exe程序所在的文件夹中会产生一个配置文件和一个日志文件。
- 4.程序启动后，根据提示，进入“设置”页，选定一个文件夹（或输入一个文件夹路径）作为基础工作路径。
- 5.设定完基础路径后，选定一个文件夹（或输入一个文件夹路径）作为笔记存放路径。
- 6.简言之，程序不需要安装，日志和配置存在程序所在的文件夹，启动后根据提示设定完基础路径和笔记保存路径即可正常使用——而这时候，实际上你也知道了所有重要文件的存放位置，在后续使用过程中，如有需要，可在设置页快速找到所有入口。

**软件许可与免责声明**：
- 1）MIT LICENSE 不对 datawork app 起作用；
- 2）该程序仅供个人用户以学习、教育、研究以及兴趣探索为目的使用；
- 3）保留一切权利；
- 4）为保证用户软件使用安全，未经许可，任何第三方不能以任何形式直接或间接传播本仓库所提供的.exe软件包，用户可通过官方仓库的下载页面下载.exe软件包；
- 5）目前软件处于测试阶段，用户使用时应注意个人数据备份，使用过程中一切后果自行承担。

**软件内页截图**：


<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020241027233110.png" width = "600" height = "455" alt="" align=center />

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020241027233206.png" width = "600" height = "455" alt="" align=center />

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020241027233045.png" width = "600" height = "455" alt="" align=center />

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020241027233421.png" width = "600" height = "455" alt="" align=center />



# pydatawork（pypi）

2023.6.15 22:50:22

**简介**：
pydatawork是一个python库，目的是让每个人都能将python用于办公自动化。已上传pypi，可以通过pip安装。

**项目特性**：
在教程辅助下，小白用户只需管理好相关文件路径，即可借助python实现部分大批量数据操作，让电脑发挥出“计算机”的潜力。

**设计理念**：
个人电脑不应该只是个笔记本，而是计算机。

**pydatawork安装指令**：

```shell
pip3 install pydatawork 或 pip install pydatawork
```

**pydatawork官方文档**：

https://pypi.org/project/pydatawork/


**其他**：

pypi维护指令：

```shell
# 在第二步，如果自己的电脑能直接用python，可直接用python，而不必用python3
cd 到pydatawork文件夹
python3 setup.py sdist bdist_wheel # 打包
twine check dist/* # 检查
twine upload dist/* # 上传，需要输入帐号密码

```

pypi初始使用：

```shell
# 先注册pypi
# 再安装工具：如果自己的电脑安装的是pip，可以用pip，而不是pip3
pip3 install twine # 安装twine，后续使用twine上传包
pip3 install --upgrade setuptools wheel twine # 升级工具，如果没安装需要先安装

```


# Git使用方法


2023.6.15 23:09:56

git维护指令：

```shell
cd到datawork文件夹（在vscode中使用终端，也需要先cd到datawork文件夹）
git pull # 从远程拉取，确保远程端的内容都存到了本地——如果不一致，会提示优先处理完毕，该怎么处理怎么处理，以便让本地和远程端保持同步，避免冲突。每次都这么做，养成习惯，避免不必要的同步冲突
git status # 查看同步状态是否正常
git add .  # 暂存更改，为提交做准备
git commit -m "备注" # 说明此次维护做了什么，作为笔记记录 
git push 或 git push origin datawork 或 git push origin datawork:datawork，意思是将本地的 datawork 分支 推送到 远程端 origin 主机上的 datawork 分支。本地端和远程端要分清。远程端主机，默认就是写成 origin。在终端输入 git status 后，也能看到提示，提示会说明本地分支是 datawork，远程分支是 origin/datawork。

```



2023.4.5 15:24:18

开始使用git，配置好之后，下载了很多感兴趣的项目。

在linux系统上操作很方便，据说在linux中“一切皆文件”，所以每个操作过程都比较容易理解，如果是在windows中，那就得先去安装某个工具才行，路径就有点曲折了，刚接触时容易因为陌生和繁琐而放弃。


下载项目源码的指令为：

```shell
ssh git@github.com # 配置好之后，在终端执行这个命令，这时候会进行的过程是【让存在github的公钥和存在本地的私钥匹配上，以建立连接，这时候需要输入钥匙密码】
git init # 新建或进入某个文件夹，在该文件夹打开终端，输入指令，这时候会在该文件夹建立一个.git配置文件
git clone url # 获取某个项目的SSH下载链接，url指链接
```

在linux中初始配置需要用到的指令：

```shell
echo "# site-navigation" >> README.md # 指定文件夹和文件？？
git init #初始化git
git add . #将本地代码提交到暂存区
git commit -m "first commit" #提交到本地仓库
git remote add origin https://github.com/ideshun/site-navigation.git # 添加远程仓库。 1）第一次提交，需要先连接远程库；2）如果提示origin已存在，可以先用 git remote rm origin删除，然后重新执行
git push -u origin master #将本地的代码提交到远程仓库的master分支。 1）我的库的主分支改成datawork了，就需要修改。

# 特别说明（2023.6.15）：第一次操作时，由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需 git push origin master。这里的origin指远程主机，master指本地分支名字，如果是默认值，就是master。如果已经改了，完整操作是：git push origin 本地分支名字：远程分支名字

```


在windows中，配置git需要用到的指令：

```shell
# 在Git Bash中操作
git config --global user.name "git账户名，可与github一致" # 配置git账户名
git config --global user.email "邮箱，可与github一致" # 配置git邮箱
git config --list # 查看配置信息
ssh-keygen -t rsa # 生成密钥，包含公钥和私钥，需要设置匹配密码
ssh -T git@github.com # 公钥添加到github后，测试是否能连接成功，需要输入匹配密码
```

在windows中，进入某个文件夹使用git：

```shell
# 在Git Bash中操作
# 先进入datawork文件夹
git status # 查看状态
git pull # 拉取最新内容，需要输入匹配密码
git add . # 暂存修改内容
git commit -m "xxx" # 添加修改备注
git push origin datawork:datawork # 推送，需要输入匹配密码

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

在windows中配置git教程：

1、国内下载地址：https://registry.npmmirror.com/binary.html?path=git-for-windows/

2、安装教程参考
《windows的git配置流程》：https://blog.csdn.net/Wmeihua/article/details/123257553

《Git for Windows. 国内镜像》：https://blog.csdn.net/jiesunliu3215/article/details/111559125


在linux中配置git教程：

1、@带甜味的盐@ 《Git提交代码完整流程》：https://blog.csdn.net/s_y_w123/article/details/112465793

2、@梦魇 《手把手教你用git上传项目到GitHub》：https://zhuanlan.zhihu.com/p/193140870

3、《新手创建第一个GitHub项目，一步一步将本地项目提交到GitHub》：https://cloud.tencent.com/developer/article/1595821

4、@gblfy 《git push -u origin master和git push 远程主机名 本地分支名:远程分支名作用》：https://blog.csdn.net/weixin_40816738/article/details/105109944

5、@林皮皮s 《使用git将本地项目推送到远程仓库github》：https://www.jianshu.com/p/b1f9f684fac8

——————————————

联系方式：zhouqiling.bjfu@foxmail.com

