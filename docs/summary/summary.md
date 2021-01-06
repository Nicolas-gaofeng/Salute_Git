## Git的前世今生

- 今生：

  git是目前世界上最先进的分布式版本控制系统。

- 前世：

  Git 诞生于一个极富纷争大举创新的年代。Linus Torvalds 在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！

  你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。不过，到了2002年，Linux系统已经发展了十年了， 绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991－2002年间）。 代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。

  安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议(这么干的其实也不只他一个)，被BitMover公司发现了(监控工作做得不错！)，于是BitMover公司怒了，要收回Linux社区的免费使用权。Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的，在2005年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。

  实际情况是这样的：Linus花了两周时间自己用C写了一个分布式版本控制系统，Linus对新的系统制订了若干目标：速度;简单的设计;对非线性开发模式的强力支持（允许成千上万个并行开发的分支）;完全分布式;有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）等，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

## Git特点

- 版本控制：
  - 可以解决多人同时开发的代码问题，也可以解决找回历史代码的问题。
- 分布式：
  - Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。首先找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。可以自己搭建这台服务器，也可以使用GitHub网站。

## Git与SVN对比

### SVN

是集中式版本控制系统，版本库是集中放在中央服务器的，而开发人员工作的时候，用的都是自己的电脑，所以首先要从中央服务器下载最新的版本，然后开发，开发完后，需要把自己开发的代码提交到中央服务器。

集中式版本控制工具缺点：

- ​	服务器单点故障

- ​	容错性差

![SVN](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011237.png)

### Git

是分布式版本控制系统（Distributed Version Control System，简称 DVCS） ，分为两种类型的仓库：本地仓库和远程仓库。

- 本地仓库：是在开发人员自己电脑上的Git仓库
- 远程仓库：是在远程服务器上的Git仓库
- Clone：克隆，就是将远程仓库复制到本地
- Push：推送，就是将本地仓库代码上传到远程仓库
- Pull：拉取，就是将远程仓库代码下载到本地仓库

![git_ll](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011258.png)

## Git工作流程

工作流程如下：

1．从远程仓库中克隆代码到本地仓库

2．从本地仓库中checkout代码然后进行代码修改

3．在提交前先将代码提交到暂存区

4．提交到本地仓库。本地仓库中保存修改的各个历史版本

5．修改完成后，需要和团队成员共享代码时，将代码push到远程仓库

![工作流程](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011316.png)

## 工作目录、暂存区以及版本库概念

- 版本库
  - 前面看到的.git隐藏文件夹就是版本库，版本库中存储了很多配置信息、日志信息和文件版本信息等
- 工作目录（工作区）
  - 包含.git文件夹的目录就是工作目录，主要用于存放开发的代码
- 暂存区
  - .git文件夹中有很多文件，其中有一个index文件就是暂存区，也可以叫做stage。暂存区是一个临时保存修改文件的地方，还有git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。因为我们创建git版本库时，git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

![图片15](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011330.png)

## Git工作目录下文件的两种状态

Git工作目录下的文件存在两种状态：

- untracked 未跟踪（未被纳入版本控制）
- tracked 已跟踪（被纳入版本控制）
  - Unmodified 未修改状态
  - Modified 已修改状态
  - Staged 已暂存状态

这些文件的状态会随着我们执行Git的命令发生变化

## Git代码托管服务

如何搭建Git远程仓库呢？我们可以借助互联网上提供的一些代码托管服务来实现，其中比较常用的有GitHub、码云、GitLab等。

### Gitee

- 地址： https://gitee.com/
- 是国内的一个代码托管平台，由于服务器在国内，所以相比于GitHub，码云速度会更快

### GitHub

- 地址：https://github.com/ 
- 是一个面向开源及私有软件项目的托管平台，因为只支持Git 作为唯一的版本库格式进行托管，故名gitHub

### GitLab

- 地址： https://about.gitlab.com/
- 是一个用于仓库管理系统的开源项目，使用Git作为代码管理工具，并在此基础上搭建起来的web服务

## SSH协议

### 什么是SSH协议

SSH 为 Secure Shell（安全外壳协议）的缩写，由 IETF 的网络小组（Network Working Group）所制定。SSH 是目前较可靠，专为远程登录会话和其他网络服务提供安全性的协议。利用 SSH 协议可以有效防止远程管理过程中的信息泄露问题。

由于本地Git仓库和远程仓库之间的传输是通过SSH加密的，所以必须要让远程仓库服务器认证你的SSH key，在此之前，必须要生成SSH key。

使用ssh协议通信时，推荐使用基于密钥的验证方式。你必须为自己创建一对密匙（公钥和私钥），并把公匙放在需要访问的服务器上。

### Git支持的传输协议

由于Git的远程仓库并不在我们本地，当我们在使用远程仓库的时候（例如克隆、拉取、推送）就会涉及到数据的网络传输，Git支持多种数据传输协议

- 本地协议（Local）
- HTTPS 协议
- SSH（Secure Shell）协议
- Git 协议

![image-44](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011708.png)

### 配置SSH协议

可以使用Git提供的命令行工具Git Bash生成公钥和私钥，具体操作过程如下：

1、使用命令ssh-keygen –t rsa生成公钥和私钥，执行完成后在window本地用户.ssh目录C:\Users\用户名\.ssh下面生成如下名称的公钥和私钥

```bash
ssh-keygen –t rsa
ssh-keygen -t rsa -C "邮箱地址"
```

![image-22](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011800.png)

2、复制公钥文件内容至码云服务器

![image-11](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107011822.png)