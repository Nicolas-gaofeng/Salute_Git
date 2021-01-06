## 创建仓库

(1)注册github账户，登录后，点击"New respository "

![clip_image002](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013026.png)

(2)在新页面中，输入项目的名称，勾选'README.md'，点击'create repository'

![clip_image004](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013046.png)

(3)添加成功后，转到文件列表页面.

![img](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107012943.png)

## 添加ssh账户

1. 如果某台机器需要与github上的仓库交互，那么就要把这台机器的ssh公钥添加到这个github账户上。点击账户头像后的下拉三角，选择'settings'。

   ![clip_image008](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013156.png)

2. 点击'SSH and GPG keys'，添加ssh公钥。

![clip_image010](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013228.png)

3. 在ubuntu的命令行中，回到用户的主目录下，编辑文件.gitconfig，修改某台机器的git配置。

![clip_image012](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013329.png)

4. 修改为注册github时的邮箱，填写用户名。

![clip_image014](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013407.png)

5. 使用如下命令生成ssh密钥。

```bash
ssh-keygen -t rsa -C "邮箱地址"
```

![clip_image016](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013448.png)

6. 进入主目录下的.ssh文件件，下面有两个文件。

   公钥为id_rsa.pub

   私钥为id_rsa

   查看公钥内容，复制此内容

   ![clip_image018](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013522.png)

7. 回到浏览器中，填写标题，粘贴公钥

![clip_image020](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107013547.png)

## 自动生成README.md目录

由于码云和github的markdown解析器，都不支持 [TOC]，码云官方推荐的是使用<a>标签来生成目录，但是如果文档目录过多，这种方式显然很不现实。

因此我们使用神器[gh-md-toc](https://github.com/ekalinin/github-markdown-toc.go/releases)

首先将README.md文档复制到[gh-md-toc.exe](./gh-md-toc.exe)的根目录下。

接着按住shift键同时右击。

![image-20201224155327338](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107012509.png)

打开Powershell窗口后，直接键入。

```bash
./gh-md-toc.exe README.md
```

然后将生成的这一大段内容粘贴到你的md文件中，上传到码云或github即可显示目录

## github删除某个文件夹

在github上只能删除仓库,却无法删除文件夹或文件, 所以只能通过命令来解决

首先进入你的master文件夹下, Git Bash Here ,打开命令窗口

```bash
$ git --help                                      # 帮助命令
$ git pull origin master                    # 将远程仓库里面的项目拉下来
$ dir                                                # 查看有哪些文件夹
$ git rm -r --cached target              # 删除target文件夹
$ git commit -m '删除了target'        # 提交,添加操作说明
$ git push -u origin master # 将本次更改更新到github项目上去
```

注:本地项目中的target文件夹不收操作影响,删除的只是远程仓库中的target, 可放心删除
每次增加文件或删除文件，都要commit 然后直接 git push -u origin master，就可以同步到github上了

## 给README文件添加icon

![license-Apache 2-green](https://gitee.com/zgf1366/pic_store/raw/master/img/20210107012640.svg)

实际上分别是由三个不同的第三方生成的图:

https://shields.io

这个网站可以自定义一些徽章，并且还提供了从github上读取状态的功能。

https://travis-ci.org

这个是一个持续集成网站，他会对项目持续编译，然后给出一个徽章显示实时的状态。

https://bintray.com

这个是一个代码仓库，说到jcenter应该就比较熟悉了，他就是jcenter，项目传到jcenter后会给个徽章实时显示当前的最新版本。



添加Github中的star/fork/watch按钮,详见文档：https://ghbtns.com/

所需参数

您必须为以下每个 URL 参数声明一个值：

| 选项   | 描述                                                         |
| ------ | :----------------------------------------------------------- |
| `user` | 拥有仓库的 GitHub 用户名                                     |
| `repo` | GitHub 仓库名称                                              |
| `type` | 要显示的按钮类型: `star`、`watch`、`fork`、`sponsor`、`follow` |

可选参数

不需要以下 URL参数。根据需要添加它们。

| 选项    | 描述                                                  |
| ------- | :---------------------------------------------------- |
| `count` | 显示可选的观察器或分叉计数：*默认情况下*没有或`true`  |
| `size`  | 用于使用较大按钮的可选标志：*默认情况下*没有或`large` |

- Star

```html
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=star&count=true&size=large" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>
 
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=star&count=true" frameborder="0" scrolling="0" width="150" height="20" title="GitHub"></iframe>
```

- Watch

```html
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=watch&count=true&size=large&v=2" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>
 
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=watch&count=true&v=2" frameborder="0" scrolling="0" width="150" height="20" title="GitHub"></iframe>
```

- Fork

```html
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=fork&count=true&size=large" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>
 
<iframe src="https://ghbtns.com/github-btn.html?user=twbs&repo=bootstrap&type=fork&count=true" frameborder="0" scrolling="0" width="150" height="20" title="GitHub"></iframe>
```

可用选项

SSL 支持

示例按钮与 URL 一起显示。当 SSL 选项托管在 GitHub 页面上时，SSL 选项通过[CloudFlare 的免费通用 SSL 产品](https://blog.cloudflare.com/introducing-universal-ssl/)提供。如果您愿意，您仍然可以使用 。`https://` `http://`

语法格式

```html
// markdown语法
[![Travis](https://img.shields.io/badge/CSDN-阿钟-brightgreen.svg)](http://blog.csdn.net/a_zhon)

//html语法
<a target="_blank" href="http://blog.csdn.net/a_zhon"><img
        src="https://img.shields.io/badge/CSDN-%E9%98%BF%E9%92%9F-brightgreen.svg"></a>
```

