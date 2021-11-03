GIT

初始配置

```shell
git config	#配置 
```

```shell
git config --system	[选项]	#ˈsɪstəm配置所有用户	/etc/gitconfig
git config --system user.name 用戶名	#设置用户名
```

```shell
git config --global [选项]	#ˈɡloʊbl配置当前用户 ～/.gitconfig
git config --global user.email snakeqiang@hotmail.com	#设置邮箱
```

```shell
git config [选项]	#配置当前项目 	project/.git/config
git config core.editor pycharm	#kɔːr ˈedɪtər配置编译器
#初次创建需初始化仓库
```

```shell
git config --list	#查看配置信息
```

基本命令

```shell
git init	#初始化仓库
#将某个项目目录变为git操作目录，生成git本地仓库。即该项目目录可以使用git管理
```

```shell
git status	#ˈsteɪtəs查看本地仓库状态
#说明: 初始化仓库后默认工作在master分支，当工作区与仓库区不一致时会有提示。
```

```shell
git add 文件名	#将工作内容记录到暂存区
```

扩展

```shell
file            #表示忽略file文件
*.a             #表示忽略所有 .a 结尾的文件
!lib.a          #表示但lib.a除外
build/          #bɪld表示忽略 build/目录下的所有文件，过滤整个build文件夹；

```

```shell
git rm --cached	文件名	#kæʃt取消文件暂存记录
```

```shell
git commit [file] -m [message]	#kəˈmɪt将文件同步到本地仓库
git commit -m 'init add'
```

```shell
git log
git log --pretty=oneline #ˈprɪti查看commit 日志记录
```

```shell
git diff  [file]	#dɪf比较工作区文件和仓库文件差异
```

```shell
git checkout [commit] -- [file]	#ˈtʃekaʊt将暂存区或者某个commit点文件恢复到工作区 （--是为了防止误操作，checkout还有切换分支的作用）
```

```shell
git  mv  [file] [path]	#pæθ移动文件
git  rm  [files]	#删除文件
#注意: 这两个操作会修改工作区内容，同时将操作记录提交到暂存区。
```

版本控制

```shell
git reset --hard HEAD^	#退回到上一个commit节点
#注意 ： 一个^表示回退1个版本，依次类推。当版本回退之后工作区会自动和当前commit版本保持一致
```

```shell
git reset --hard [commit_id]	#退回到指定的commit_id节点
```

```shell
git reflog	#查看所有操作记录
#注意:最上面的为最新记录，可以利用commit_id去往任何操作位置
```

```shell
git  tag  [tag_name] [commit_id] -m  [message]	#tæɡ创建标签(commit位置添加快照)
#说明: commit_id可以不写则默认标签表示最新的commit_id位置，message也可以不写，但是最好添加。
```

```shell
git tag  #查看标签列表	
git show [tag_name]  #查看标签详细信息
```

```shell
git reset --hard [tag]	#去往某个标签节点
```

```shell
git tag -d  [tag]	#删除标签
```

保存工作区

```shell
git stash save [message]	#stæʃ保存工作区内容
```

```shell
git stash  list	#查看工作区列表
```

```shell
git stash  apply  [stash@{n}]	#应用某个工作区
```

```shell
git stash drop [stash@{n}]  #删除某一个工作区
git stash clear  #əˈplaɪ删除所有保存的工作区
```

分支管理 

定义: 分支即每个人在原有代码（分支）的基础上建立自己的工作环境，单独开发，互不干扰。完成开发工作后再进行分支统一合并。

```shell
git branch	#查看分支情况
#说明: 前面带 * 的分支表示当前工作分支
```

[branch][bræntʃ]分支

```shell
git branch [branch_name]	#bræntʃ创建分支
#说明: 基于a分支创建b分支，此时b分支会拥有a分支全部内容。在创建b分支时最好保持a分支"干净"状态。
```

```shell
git checkout [branch]	#切换工作分支
#说明: 2,3可以同时操作，即创建并切换分支
```

```shell
git merge [branch]	#mɜːrdʒ合并分支
```

[merge][mɜːrdʒ]合并

```shell
git branch -d [branch]  #删除分支
git branch -D [branch]  #删除没有被合并的分支
```



GitHub

[生成token][https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token]

```
头像=>Settings=>Developer settings=>personal access tokens=>note (input)=>Expiration（token期限)=>Generate token(生成token)
#FAQ 如果无法输入新密码，可先将计算机中原来的凭据彻底删除，删除方法是,控制面板>用户账户>凭据管理器>Windows凭据，然后找出所有与git有关的凭据，统统删除。
```

在左上角搜索栏搜索想要的获取的项目

选择项目后复制项目git地址

```shell
git clone https://github.com/xxxxxxxxx #将项目获取到本地
```

[clone][kloʊn] 克隆

注意： 获取到本地的项目会自动和github远程仓库建立连接。且获取的项目本身也是个git项目。

创建删除git仓库：

点击右上角加号下拉菜单，选择新的仓库

 [repository][rɪˈpɑːzətɔːri] 仓库 [organization][ˌɔːrɡənəˈzeɪʃn]组织 

填写相应的项目信息即可

github仓库相对本地主机就是一个远程仓库 通过remote连接，如果需要输入密码输入github密码即可。连接后即可使用远程仓库操作命令操作。readme文件会被自动作为项目介绍

如果是在自己的仓库界面选择settings，在最后可以选择删除仓库。

远程仓库操作命令：所有操作在本地git仓库下进行

```shell
git remote  add origin https://github.com/xxxxxxxxx #添加远程仓库
```

[remote][rɪˈmoʊt]远程

```shell
git remote	#查看连接的主机 注意: 一个git项目连接的远程主机名不会重复
```

```shell
git remote rm [origin]	#删除远程主机
```

[origin][ˈɔːrɪdʒɪn]起源

```shell
git push -u origin master #将本地分支推送给远程仓库
#将master分支推送给origin主机远程仓库，第一次推送分支使用-u表示与远程对应分支建立自动关联
```

[master][ˈɔːrɪdʒɪn]控制者

```shell
git push	#推送代码到远程仓库
```

[push][pʊʃ]推

推送标签

```shell
git push origin [tag]  #推送本地标签到远程
git push origin --tags  #推送本地所有标签到远程
```

推送旧的版本

```shell
git push --force origin  #用于本地版本比远程版本旧时强行推送本地版本
```

[force][fɔːrs]强迫

删除远程分支和标签

```shell
git branch -a  #查看所有分支 
git push origin  [:branch]  #删除远程分支 
git push origin --delete tag  [tagname]  #删除远程仓库标签
```

从远程获取代码

```shell
git pull #获取远程分支代码
```

```shell
git fetch origin  master:tmp  #将远程分支master拉取到本地，作为tmp分支
```

[fetch][fetʃ]拿 取得

区别: pull将远程内容直接拉取到本地，并和对应分支内容进行合并 fetch将远程分支内容拉取到本地，但是不会和本地对应分支合并，可以自己判断后再使用merge合并。

## 软件项目开发流程

```
需求分析 ----》 概要设计  ---》 项目计划 ----》详细设计---》编码测试 -----》项目测试 ----》调试修改 ---》项目发布----》后期维护
```

> 需求分析 ： 确定用户的真实需求 
>
> > 1. 确定用户的真实需求，项目的基本功能
> > 2. 确定项目的整体难度和可行性分析
> > 3. 需求分析文档，用户确认

> 概要设计：对项目进行初步分析和整体设计
>
> > 1. 确定功能模块
> > 2. 进行可行性分析 搭建整体架构图
> > 3. 确定技术思路和使用框架
> > 4. 形成概要文档指导开发流程

> 项目计划 ： 确定项目开发的时间轴和流程
>
> > 1. 确定开发工作的先后顺序
> > 2. 确定时间轴  ，事件里程碑
> > 3. 人员分工 
> > 4. 形成甘特图和思维导图等辅助内容

> 详细设计 ： 项目的具体实现
>
> > 1.形成详细设计文档 ： 思路，逻辑流程，功能说明，技术点说明，数据结构说明，代码说明

> 编码测试 ： 按照预定计划实现代码编写，并且做基本检测
>
> > 1. 代码编写
> > 2. 写测试程序
> > 3. 技术攻关

> 项目测试 ： 对项目按照功能进行测试
>
> > 1. 跨平台测试 ，使用测试
> > 2. 根据测试报告进行代码修改
> > 3. 完成测试报告

> 项目发布
>
> > 1.项目交付用户进行发布 2.编写项目说明文档

> 后期维护
>
> > 1.维护项目正常运转 2.进行项目的迭代升级

### 项目注意事项

- 按时完成项目工作和项目时间不足之间的冲突
- 项目实施人员之间的冲突

### 项目工具的使用

编写文档： word  ppt  excel  markdown   LaTex 项目流程图 ： Mindmanager  visio 项目管理 ： project 代码管理 ： svn   git
