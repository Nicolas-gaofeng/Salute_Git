![](./image/Git.jpg)

[TOC]

## 介绍

1. 这是一份学习Git的菜鸟教程-从入门到跑路

2. Markdown编辑器使用[Typora](https://typora.io/)

3. 主题使用[Drake](https://theme.typora.io/theme/Drake/)

## 下载

1.[Git](https://git-scm.com/download/win)

2.[Tortoisegit](https://tortoisegit.org/download/)



## 一、Git概述 

### 1.1 Git的前世今生

- 今生：

  git是目前世界上最先进的分布式版本控制系统。

- 前世：

  Git 诞生于一个极富纷争大举创新的年代。Linus Torvalds 在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。不过，到了2002年，Linux系统已经发展了十年了， 绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991－2002年间）。 代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。

  安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议(这么干的其实也不只他一个)，被BitMover公司发现了(监控工作做得不错！)，于是BitMover公司怒了，要收回Linux社区的免费使用权。Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的，在2005年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。

  实际情况是这样的：Linus花了两周时间自己用C写了一个分布式版本控制系统，Linus对新的系统制订了若干目标：速度;简单的设计;对非线性开发模式的强力支持（允许成千上万个并行开发的分支）;完全分布式;有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）等，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

### 1.2 Git特点

- 版本控制：
  - 可以解决多人同时开发的代码问题，也可以解决找回历史代码的问题。
- 分布式：
  - Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。首先找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。可以自己搭建这台服务器，也可以使用GitHub网站。

### 1.3 Git与SVN对比

#### SVN

是集中式版本控制系统，版本库是集中放在中央服务器的，而开发人员工作的时候，用的都是自己的电脑，所以首先要从中央服务器下载最新的版本，然后开发，开发完后，需要把自己开发的代码提交到中央服务器。

集中式版本控制工具缺点：

- ​	服务器单点故障

- ​	容错性差

![SVN.png](./image/SVN.png)

#### Git

是分布式版本控制系统（Distributed Version Control System，简称 DVCS） ，分为两种类型的仓库：本地仓库和远程仓库。

- 本地仓库：是在开发人员自己电脑上的Git仓库
- 远程仓库：是在远程服务器上的Git仓库
- Clone：克隆，就是将远程仓库复制到本地
- Push：推送，就是将本地仓库代码上传到远程仓库
- Pull：拉取，就是将远程仓库代码下载到本地仓库

![git_ll.png](.\image\git_ll.png)

### 1.4 Git工作流程

工作流程如下：

1．从远程仓库中克隆代码到本地仓库

2．从本地仓库中checkout代码然后进行代码修改

3．在提交前先将代码提交到暂存区

4．提交到本地仓库。本地仓库中保存修改的各个历史版本

5．修改完成后，需要和团队成员共享代码时，将代码push到远程仓库

![工作流程](.\image\工作流程.png)

### 1.5 工作目录、暂存区以及版本库概念

- 版本库
  - 前面看到的.git隐藏文件夹就是版本库，版本库中存储了很多配置信息、日志信息和文件版本信息等
- 工作目录（工作区）
  - 包含.git文件夹的目录就是工作目录，主要用于存放开发的代码
- 暂存区
  - .git文件夹中有很多文件，其中有一个index文件就是暂存区，也可以叫做stage。暂存区是一个临时保存修改文件的地方

![图片15](.\image\图片15.png)

### 1.6 Git工作目录下文件的两种状态

Git工作目录下的文件存在两种状态：

- untracked 未跟踪（未被纳入版本控制）
- tracked 已跟踪（被纳入版本控制）
  - Unmodified 未修改状态
  - Modified 已修改状态
  - Staged 已暂存状态

这些文件的状态会随着我们执行Git的命令发生变化

## 二、Git代码托管服务

如何搭建Git远程仓库呢？我们可以借助互联网上提供的一些代码托管服务来实现，其中比较常用的有GitHub、码云、GitLab等。

### 2.1 码云（Gitee）

- 地址： https://gitee.com/
- 是国内的一个代码托管平台，由于服务器在国内，所以相比于GitHub，码云速度会更快

### 2.2 GitHub

- 地址：https://github.com/ 
- 是一个面向开源及私有软件项目的托管平台，因为只支持Git 作为唯一的版本库格式进行托管，故名gitHub

### 2.3 GitLab

- 地址： https://about.gitlab.com/
- 是一个用于仓库管理系统的开源项目，使用Git作为代码管理工具，并在此基础上搭建起来的web服务

## 三、Git常用命令

### 3.1 环境配置

当安装Git后首先要做的事情是设置用户名称和email地址。这是非常重要的，因为每次Git提交都会使用该用户信息

#### 3.1.1 查看配置信息

```
git config --list

git config user.name

git config user.email
```

#### 3.1.2 设置用户信息 

```
git config --global user.name “***”

git config --global user.email “*******@qq.cn”
```

通过上面的命令设置的信息会保存在~/.gitconfig文件中

### 3.2 获取Git仓库

要使用Git对我们的代码进行版本控制，首先需要获得Git仓库。获取Git仓库通常有两种方式：

#### 3.2.1 在本地初始化一个Git仓库

执行步骤如下：

1. 在电脑的任意位置创建一个空目录（例如repo1）作为我们的本地Git仓库

2. 进入这个目录中，点击右键打开Git bash窗口

3. 执行命令git init

如果在当前目录中看到.git文件夹（此文件夹为隐藏文件夹）则说明Git仓库创建成功

![1559580617566](.\image\图片13.png)

#### 3.2.2 从远程仓库克隆

可以通过Git提供的命令从远程仓库进行克隆，将远程仓库克隆到本地

命令形式为：

```
git clone 远程Git仓库地址 
```

### 3.3 本地仓库操作

#### 3.3.1 查看文件状态

```
git status 
git status –s   # 使输出信息更加简洁
```

#### 3.3.2 将未跟踪的文件加入暂存区

```
git add 文件名
```

#### 3.3.3 将暂存区的文件取消暂存

```
git reset 文件名
```

#### 3.3.4 将暂存区的文件修改提交到本地仓库

```
git commit -m "随便的日志信息str"
```

如果不加 -m会进入编辑器 输入 i 变成插入模式，然后按esc  输入：wq 退出

#### 3.3.5 删除文件

```
git rm 文件名
```

上面删除的只是工作区的文件，需要提交到本地仓库（git commit -m "str"）,rm命令默认将文件添加到暂存区，而直接通过右键删除的方式没有将文件添加到暂存区，需要手动添加文件到暂存区之后（git add 文件名）才能commit。

#### 3.3.6 将文件添加至忽略列表

一般我们总会有些文件无需纳入Git 的管理，也不希望它们总出现在未跟踪文件列表。 通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等。 在这种情况下，我们可以在工作目录中创建一个名为 .gitignore 的文件（文件名称固定），列出要忽略的文件模式。下面是一个示例：

windows下 .gitignore文件的创建方式，右键Git bush here里输入touch .gitignore 

```
# no .a files
*.a
# but do track lib.a, even though you're ignoring .a files above
!lib.a
# only ignore the TODO file in the current directory, not subdir/TODO
/TODO
# ignore all files in the build/ directory
build/
# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt
# ignore all .pdf files in the doc/ directory
doc/**/*.pdf
```

#### 3.3.7 查看日志记录

```
 git log 
```

按回车查看信息，出现end代表显示完毕。按q可以退出log页面

### 3.4 远程仓库操作

####   3.4.1 查看远程仓库

如果想查看已经配置的远程仓库服务器，可以运行 git remote 命令。 它会列出指定的每一个远程服务器的简写。 如果已经克隆了远程仓库，那么至少应该能看到 origin ，这是 Git 克隆的仓库服务器的默认名字

```
 git remote 
 git remote -v # 显示远程地址 fetch代表抓取 push代表推送
 git remote show origin # 显示更详细的信息
```

####   3.4.2 添加远程仓库

运行 git remote add <shortname> <url> 添加一个新的远程 Git 仓库，同时指定一个可以引用的简写。远程仓库的名称跟本地仓库名称可以不一致，但最好一致。一个本地仓库可以添加多个远程地址。

```
git remote add <shortname> <url>      
git remote add origin <url>      
```

####   3.4.3 从远程仓库克隆

如果你想获得一份已经存在了的 Git 仓库的拷贝，这时就要用到 git clone 命令。 Git 克隆的是该 Git 仓库服务器上的几乎所有数据（包括日志信息、历史记录等），而不仅仅是复制工作所需要的文件。 当你执行 git clone 命令的时候，默认配置下远程 Git 仓库中的每一个文件的每一个版本都将被拉取下来。

克隆仓库的命令格式是 git clone [url] 

```
git clone [url] 
```

####   3.4.4 移除无效的远程仓库

如果因为一些原因想要移除一个远程仓库 ，可以使用

```
git remote rm 名称
```

注意：此命令只是从本地移除远程仓库的记录，并不会真正影响到远程仓库，远程仓库还是存在的

####   3.4.5 从远程仓库中抓取与拉取 

git fetch 是从远程仓库获取最新版本到本地仓库，不会自动merge

```
git fetch
git fetch origin master # 从origin仓库抓取master分支数据
git merge origin/master # 通过git merge手动合并
```

git pull 是从远程仓库获取最新版本并merge到本地仓库

```
git pull
```

注意：如果当前本地仓库不是从远程仓库克隆，而是本地创建的仓库，并且仓库中存在文件，此时再从远程仓库拉取文件的时候会报错（fatal: refusing to merge unrelated histories ），解决此问题可以在git pull命令后加入参数--allow-unrelated-histories

```
git pull --allow-unrelated-histories
```

要求输入日志时直接输入 wq！退出即可。

####   3.4.6 推送到远程仓库 

当你想分享你的代码时，可以将其推送到远程仓库。 命令形式：

```
git git push [remote-name][branch-name]
```



### 3.5 Git分支

几乎所有的版本控制系统都以某种形式支持分支。 使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线。Git 的master分支并不是一个特殊分支。 它跟其它分支没有区别。 之所以几乎每一个仓库都有 master 分支，是因为git init 命令默认创建它，并且大多数人都懒得去改动它。

在本章节我们会学习到关于分支的相关命令，具体如下：

#### 3.5.1 查看分支 

\# 列出所有本地分支

$ git branch

\# 列出所有远程分支

$ git branch -r

\# 列出所有本地分支和远程分支

$ git branch -a

![1559617419855](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片33.png)

#### 3.5.2 创建分支

![1559617439442](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片34.png)

#### 3.5.3 切换分支 

![1559617458282](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片35.png)

​	

#### 3.5.4 推送至远程仓库分支 

![1559617505369](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片36.png)

#### 3.5.5 合并分支 

![1559617538380](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片37.png)

有时候合并操作不会如此顺利。 如果你在两个不同的分支中，对同一个文件的同一个部分进行了不同的修改，Git 就没办法合并它们，同时会提示文件冲突。此时需要我们打开冲突的文件并修复冲突内容，最后执行git add命令来标识冲突已解决

![1559617557838](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片38.png)

#### 3.7.5 删除分支

![1559617599269](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片39.png)

如果要删除的分支中进行了一些开发动作，此时执行上面的删除命令并不会删除分支，如果坚持要删除此分支，可以将命令中的-d参数改为-D

![1559617620953](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片40.png)

注：如果要删除远程仓库中的分支，可以使用命令git push
origin –d branchName

## 四、在IDEA中使用Git 

### 4.1 在IDEA中配置Git 

安装好IntelliJ IDEA后，如果Git安装在默认路径下，那么idea会自动找到git的位置，如果更改了Git的安装位置则需要手动配置下Git的路径。

选择File→Settings打开设置窗口，找到Version Control下的git选项：

![1559619887418](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片41.png)

选择git的安装目录后可以点击“Test”按钮测试是否正确配置

​                       ![1559619915169](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片42.png)

### 4.2 在IDEA中使用Git

#### 4.2.1在IDEA中创建工程并将工程添加至Git 

![1559619986255](C:\Users\zgf\Desktop\AppData\Roaming\Typora\typora-user-images\1559619986255.png)

![1559620003251](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片44.png)

​                                  将项目添加至Git管理后，可以从IDEA的工具栏上看到Git操作的按钮

#### 4.2.2 将文件添加到暂存区

![1559620213702](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片45.png)

#### 4.2.3 提交文件 

![1559620242587](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片46.png)

#### 4.2.4 将代码推送到远程仓库 

![1559620258317](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片47.png)

#### 4.2.5 从远程仓库克隆工程到本地

![1559620271237](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片48.png)

#### 4.2.6 从远程拉取代码

![1559620286937](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片49.png)

#### 4.2.7 版本对比

![1559620300302](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片50.png)

#### 4.2.8 创建分支 

![1559620312520](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片51.png)

#### 4.2.9 切换分支

![1559620325257](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片52.png)

#### 4.2.10 分支合并

![1559620338050](C:\Users\zgf\Desktop\git\08-就业课(2.1)-Git\笔记\img\图片53.png)

