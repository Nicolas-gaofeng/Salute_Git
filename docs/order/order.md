## 一、环境配置

当安装Git后首先要做的事情是设置用户名称和email地址。这是非常重要的，因为每次Git提交都会使用该用户信息

### 1.1 查看配置信息

```bash
git config --list
git config user.name
git config user.email
```

### 1.2 设置用户信息 

```bash
设置用户名
git config --global user.name “***”
设置邮箱
git config --global user.email “*******@qq.cn”
```

通过上面的命令设置的信息会保存在~/.gitconfig文件中

### 1.3 在IDEA中配置Git

安装好IntelliJ IDEA后，如果Git安装在默认路径下，那么idea会自动找到git的位置，如果更改了Git的安装位置则需要手动配置下Git的路径。

选择File→Settings打开设置窗口，找到Version Control下的git选项：

![图片41](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131120.png)

选择git的安装目录后可以点击“Test”按钮测试是否正确配置

![图片42](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131140.png)

## 二、获取Git仓库

要使用Git对我们的代码进行版本控制，首先需要获得Git仓库。获取Git仓库通常有两种方式：

### 2.1 在本地初始化一个Git仓库

#### 2.1.1 命令行方式

执行步骤如下：

1. 在电脑的任意位置创建一个空目录（例如repo1）作为我们的本地Git仓库
2. 进入这个目录中，点击右键打开Git bash窗口
3. 执行命令

```bash
git init
```

如果在当前目录中看到.git文件夹（此文件夹为隐藏文件夹）则说明Git仓库创建成功

![图片13](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107130431.png)

#### 2.1.2 TortoiseGit 方式

直接右键点击 Git Create repository here 不用勾选，选择创建空文件夹

![cjck](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107130930.png)

![cjck2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107130947.png)

#### 2.1.3 IDEA 方式

在IDEA中创建工程并将工程添加至Git 

![image-20201224120739016](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131315.png)

![图片44](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131340.png)

将项目添加至Git管理后，可以从IDEA的工具栏上看到Git操作的按钮

### 2.2 从远程仓库克隆

如果你想获得一份已经存在了的 Git 仓库的拷贝，这时就要用到 git clone 命令。 Git 克隆的是该 Git 仓库服务器上的几乎所有数据（包括日志信息、历史记录等），而不仅仅是复制工作所需要的文件。 当你执行 git clone 命令的时候，默认配置下远程 Git 仓库中的每一个文件的每一个版本都将被拉取下来。

可以通过Git提供的命令从远程仓库进行克隆，将远程仓库克隆到本地

#### 2.2.1 命令行方式

命令形式为：

```bash
git clone 远程仓库地址 
```

#### 2.2.2 TortoiseGit 方式

文件夹中右键点击 Git Clone,输入需要克隆的项目地址即可

![kl](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131612.png)

![kl2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131625.png)

#### 2.2.3 IDEA 方式

打开IDEA时选择check out form version contorl,选择git，选择地址后确定即可。

![图片48](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107131801.png)

## 三、本地仓库操作

### 3.1 查看文件状态

#### 3.1.1 命令行方式

命令形式为：

```bash
git status 
git status –s   # 使输出信息更加简洁
```

### 3.2 文件加入暂存区

#### 3.2.1 命令行方式

将文件添加到暂存区

```bash
git add 文件名
```

将暂存区的文件取消暂存

```bash
git reset 文件名 
```

#### 3.2.2 TortoiseGit 方式

右键文件，选择add

![tjzcq](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107132551.jpg)

#### 3.2.3 IDEA 方式

右键项目，选择Git,add

![图片45](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107132655.png)

### 3.3 将暂存区的文件提交到本地仓库

#### 3.3.1 命令行方式

```bash
git commit -m "随便的日志信息str"
```

如果不加 -m会进入编辑器 输入 i 变成插入模式，然后按esc  输入：wq 退出

#### 3.3.2 TortoiseGit 方式

右键选择 git commit，填入日志信息选择commit即可。

![tjzcq1](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107133114.jpg)

![tjzcq2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107133122.jpg)

#### 3.3.3 IDEA 方式

在导航栏选择commit，输入日志信息点击commit即可。

![图片46](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107133258.png)

### 3.4 删除文件

#### 3.4.1 命令行方式

```bash
git rm 文件名
git commit -m "str"
```

上面删除的只是工作区的文件，需要提交到本地仓库（git commit -m "str"）,rm命令默认将文件添加到暂存区，而直接通过右键删除的方式没有将文件添加到暂存区，需要手动添加文件到暂存区之后（git add 文件名）才能commit。

命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容。

找回删错的文件

```bash
git checkout – 文件名
```

### 3.5 将文件添加至忽略列表

一般我们总会有些文件无需纳入Git 的管理，也不希望它们总出现在未跟踪文件列表。 通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等。 在这种情况下，我们可以在工作目录中创建一个名为 .gitignore 的文件（文件名称固定），列出要忽略的文件模式。下面是一个示例：

windows下 .gitignore文件的创建方式，右键Git bush here里输入touch .gitignore 

```text
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

### 3.6 查看日志记录

```bash
 git log 
```

按回车查看信息，出现end代表显示完毕。按q可以退出log页面

### 3.7 回退到某个版本

其中HEAD表示当前最新版本，HEAD^表示当前版本的前一个版本,HEAD^^表示当前版本的前前个版本，也可以使用HEAD~1表示当前版本的前一个版本,HEAD~100表示当前版本的前100版本。

```bash
git reset --hard HEAD^
git reset --hard 版本号
git reflog  命令可以查看我们的操作记录
```

## 四、远程仓库操作

### 4.1 查看远程仓库

如果想查看已经配置的远程仓库服务器，可以运行 git remote 命令。 它会列出指定的每一个远程服务器的简写。 如果已经克隆了远程仓库，那么至少应该能看到 origin ，这是 Git 克隆的仓库服务器的默认名字

```bash
 git remote 
 git remote -v # 显示远程地址 fetch代表抓取 push代表推送
 git remote show origin # 显示更详细的信息
```

### 4.2 添加远程仓库

运行以下命令添加一个新的远程 Git 仓库，同时指定一个可以引用的简写。远程仓库的名称跟本地仓库名称可以不一致，但最好一致。一个本地仓库可以添加多个远程地址。

```bash
git remote add <shortname> <url>      
git remote add origin <url>   
```

### 4.3 移除无效的远程仓库 

如果因为一些原因想要移除一个远程仓库 ，可以使用

```bash
git remote rm 名称
```

注意：此命令只是从本地移除远程仓库的记录，并不会真正影响到远程仓库，远程仓库还是存在的

### 4.4 从远程仓库中抓取与拉取 

#### 4.4.1 命令行方式

git fetch 是从远程仓库获取最新版本到本地仓库，不会自动merge

```bash
git fetch
git fetch origin master # 从origin仓库抓取master分支数据
git merge origin/master # 通过git merge手动合并
```

git pull 是从远程仓库获取最新版本并merge到本地仓库

```bash
git pull
```

注意：如果当前本地仓库不是从远程仓库克隆，而是本地创建的仓库，并且仓库中存在文件，此时再从远程仓库拉取文件的时候会报错（fatal: refusing to merge unrelated histories ），解决此问题可以在git pull命令后加入参数--allow-unrelated-histories

```bash
git pull --allow-unrelated-histories
```

要求输入日志时直接输入 :wq！退出即可。

#### 4.4.2 TortoiseGit 方式

![lqdm](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135052.jpg)

![lqdm2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135104.jpg)

#### 4.4.3 IDEA 方式

![图片49](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135159.png)

### 4.5 推送到远程仓库 

当你想分享你的代码时，可以将其推送到远程仓库。

#### 4.5.1 命令行方式

 命令形式：

```bash
git push [remote-name][branch-name]
```

#### 4.4.2 TortoiseGit 方式

![ts](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135407.jpg)

![ts1](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135415.jpg)

#### 4.4.3 IDEA方式

![图片47](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135438.png)

## 五、Git分支

### 5.1 概念

几乎所有的版本控制系统都以某种形式支持分支。使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线。Git的master分支并不是一个特殊分支。 它跟其它分支没有区别。 之所以几乎每一个仓库都有 master 分支，是因为git init 命令默认创建它，并且大多数人都懒得去改动它。

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。

如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了git又学会了SVN！

![image002](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135614.png)

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

### 5.2 查看分支 

执行 git branch 命令可以查看当前有几个分支并且看到在哪个分支下工作。

\# 列出所有本地分支 

```bash
$ git branch
```

\# 列出所有远程分支

```bash
$ git branch -r
```

\# 列出所有本地分支和远程分支

```bash
$ git branch -a
```

### 5.3 创建分支

git把我们之前每次提交的版本串成一条时间线，这条时间线就是一个分支。截止到目前只有一条时间线，在git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

(1) 一开始的时候，master分支是一条线，git用master指向最新的提交，再用HEAD指向master，就能确定当前分支，以及当前分支的提交点：

![image0012](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135736.png)

每次提交，master分支都会向前移动一步，这样，随着你不断提交，master分支的线也越来越长。

(2)当我们创建新的分支，例如dev时，git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上：

![clip_image0014](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135806.png)

git创建一个分支很快，因为除了增加一个dev指针，改变HEAD的指向，工作区的文件都没有任何变化。

(3)不过，从现在开始，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针不变：

![clip_image0016](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135832.png)



(4)假如我们在dev上的工作完成了，就可以把dev合并到master上。git怎么合并呢？最简单的方法，就是直接把master指向dev的当前提交，就完成了合并：

![clip_image0018](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135847.png)

git合并分支也很快，就改改指针，工作区内容也不变。

(5)合并完分支后，甚至可以删除dev分支。删除dev分支就是把dev指针给删掉，删掉后，我们就剩下了一条master分支：

![clip_image0101](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107135911.png)

#### 5.3.1 命令行方式

创建分支：

```bash
$ git branch <name>
$ git branch 分支名称
```

#### 5.3.2 TortoiseGit 方式

![cjfz](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140059.jpg)



![cjfz2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140109.jpg)

#### 5.3.3 IDEA 方式

![图片51](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140157.png)

### 5.4 切换分支 

#### 5.4.1 命令行方式 

```bash
$ git checkout <name>
```

创建+切换分支

```bash
$ git checkout -b <name>
```

#### 5.4.2 TortoiseGit 方式

![qhfz](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140355.jpg)

![qhfz2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140359.jpg)

#### 5.4.3 IDEA 方式

![图片52](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140418.png)

### 5.5 合并分支

有时候合并操作不会如此顺利。 如果你在两个不同的分支中，对同一个文件的同一个部分进行了不同的修改，Git 就没办法合并它们，同时会提示文件冲突。git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容。此时需要我们打开冲突的文件并修复冲突内容，最后执行git add命令来标识冲突已解决

#### 5.5.1 命令行方式

```bash
$ git merge branchName 
$ git add 文件名称 
$ git push origin master #推送分支
```

通常，合并分支时，如果可能，git会用fast forward模式，但是有些快速合并不能成而且合并时没有冲突，这个时候会合并之后并做一次新的提交。但这种模式下，删除分支后，会丢掉分支信息。

#### 5.5.2 TortoiseGit 方式

![hbfz](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140659.jpg)

![hbfz2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140703.jpg)

#### 5.5.3 IDEA 方式

![图片53](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140753.png)

### 5.6 推送分支

推送分支，就是把该分支上的所有本地提交推送到远程库，推送时要指定本地分支，这样，git就会把该分支推送到远程库对应的远程分支上

```bash
$ git push origin 分支名称 
例：
git push origin smart
```

### 5.7 从远程分支上拉取代码

```bash
git pull orgin 分支名称
例：
git pull orgin smart
```

使用上述命令会把远程分支smart上的代码下载并合并到本地所在分支。

### 5.8 将本地分支跟踪服务器分支

```bash
git branch --set-upstream-to=origin/远程分支名称 本地分支名称
例：
git branch --set-upstream-to=origin/smart smart
```

### 5.9 删除分支

删除分支删除的是本地的分支，远程分支不会受到影响。

```bash
$ git branch -d branchName 
```

如果要删除的分支中进行了一些开发动作，此时执行上面的删除命令并不会删除分支，如果坚持要删除此分支，可以将命令中的-d参数改为-D

```bash
$ git branch -D branchName 
```

注：如果要删除远程仓库中的分支，可以使用命令git push


```bash
$ git push origin –d branchName  
```

### 5.10 Bug分支 

软件开发中，bug就像家常便饭一样。有了bug就需要修复，在git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。

(1)当你接到一个修复一个代号001的bug的任务时，很自然地，你想创建一个分支bug-001来修复它，但是，等等，当前正在dev上进行的工作还没有提交

并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？

(2)git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作：

```bash
$ git stash
```

![image-20201224153835244](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141643.png)

(3)首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支：

![image-20201224153808155](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141704.png)

(4)现在修复bug,把 the new line删掉，然后提交。

![image-20201224153931463](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141724.png)

(5)修复完成后，切换到master分支，并完成合并，最后删除bug-001分支。

![clip_image00122](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141739.png)

(6)现在bug-001修复完成，是时候接着回到dev分支干活了！

![clip_image0044](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141757.png)

(7)工作区是干净的，刚才的工作现场存到哪去了？用git stash list命令看看：

![clip_image0406](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141809.png)

工作现场还在，git把stash内容存在某个地方了，但是需要恢复一下。修复后，再git stash pop，恢复工作现场。

![clip_image0048](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107141830.png)

## 六、Git标签

像其他版本控制系统（VCS）一样，Git 可以给历史中的某一个提交打上标签，以示重要。 比较有代表性的是人们会使用这个功能来标记发布结点（v1.0 、v1.2等）。标签指的是某个分支某个特定时间点的状态。通过标签，可以很方便的切换到标记时的状态。

### 6.1 列出已有的标签

```bash
$ git tag
```

### 6.2 查看tag信息

```bash
$ git show [tag]
```

### 6.3 创建新标签

```bash
$ git tag [tagName]
```

### 6.4 将标签推送至远程仓库

```bash
$ git push [remote] [tag] # 提交指定tag
$ git push origin v0.1
```

### 6.5 检出标签

```bash
$ git checkout -b [branch] [tag] # 新建一个分支，指向某个tag
```

### 6.6 删除标签

```bash
$ git tag -d [tag] # 删除本地tag
```

### 6.7 删除远程标签

```bash
$ git push origin :refs/tags/[tag] # 删除远程tag
```



## 七、其他

### 7.1 版本对比

![图片50](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107140847.png)