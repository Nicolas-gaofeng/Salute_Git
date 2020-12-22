![](https://github.com/gaofeng1366/Salute_Git/blob/main/image/Git.jpg?raw=true)

* [Salute\_Git](#salute_git)
  * [介绍](#介绍)
  * [下载](#下载)
  * [Git概述](#git概述)
    * [Git的前世今生](#git的前世今生)
    * [Git特点](#git特点)
    * [Git与SVN对比](#git与svn对比)

## 介绍

1. 这是一份学习Git的菜鸟教程-从入门到跑路

2. Markdown编辑器使用[Typora](https://typora.io/)

3. 主题使用[Drake](https://theme.typora.io/theme/Drake/)

## 下载

1.[Git](https://git-scm.com/download/win)

2.[tortoisegit](https://tortoisegit.org/download/)



## Git概述 

### Git的前世今生

- 今生：git是目前世界上最先进的分布式版本控制系统。

- 前世：Git 诞生于一个极富纷争大举创新的年代。Linus Torvalds 在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。不过，到了2002年，Linux系统已经发展了十年了，Linux 内核开源项目有着为数众多的参与者， 绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991－2002年间）。 代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议(这么干的其实也不只他一个)，被BitMover公司发现了(监控工作做得不错！)，于是BitMover公司怒了，要收回Linux社区的免费使用权。Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的，在2005年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。实际情况是这样的：Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

Linus对新的系统制订了若干目标：

1. 速度
2. 简单的设计
3. 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
4. 完全分布式
5. 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）

### Git特点

- 版本控制：可以解决多人同时开发的代码问题，也可以解决找回历史代码的问题。
- 分布式：Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。首先找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。可以自己搭建这台服务器，也可以使用GitHub网站。

### Git与SVN对比

- SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而开发人员工作的时候，用的都是自己的电脑，所以首先要从中央服务器下载最新的版本，然后开发，开发完后，需要把自己开发的代码提交到中央服务器。

  集中式版本控制工具缺点：

​	服务器单点故障

​	容错性差

Git是分布式版本控制系统

