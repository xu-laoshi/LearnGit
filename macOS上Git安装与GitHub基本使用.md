# macOS上Git安装与GitHub基本使用



**1.下载安装**

首先看看你自己电脑之前有没有安装过Git，在终端输入git，如果出现以下就表示之前安装过（我自己都没印象自己啥时候装过的23333）

![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013140900506-1474309394.png)

 

如果之前没安装过也不要慌，有下面两种方法可以安装：

**1）通过homebrew安装Git**

 

Mac OS X是基于Unix的，它可以使用非常多Linux平台上开源的优秀工具，比如wget，比如dos2unix脚本工具等。

 

但是OS X系统本身却缺少Linux下的包管理器。比如Fedora的yum与dnf，比如Ubuntu的apt-get，比如ArchLinux的Pacman等。

 

于是这些优秀的开源软件在Mac上的安装只能通过下载源码，编译，安装，配置环境变量的步骤来完成安装。对于大部分的软件，在安装过程中是需要很多的依赖库的，手动去解决这些依赖库是十分痛苦的事情。包管理器干的就是这样的事情：解决软件安装过程中的依赖关系。

 

有一个开源的项目叫Homebrew，完美解决了Mac OS X上没有包管理器的尴尬。

 

如果之前未安装homebrew，需安装homebrew，在终端输入：``

​    `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

 

安装git：brew install git

 

**2)通过Xcode安装**

直接从AppStore安装Xcode，Xcode集成了Git，不过默认没有安装，你需要运行Xcode，选择菜单“Xcode”->“Preferences”，在弹出窗口中找到“Downloads”，选择“Command Line Tools”，点“Install”就可以完成安装了

 

## **2.**创建ssh key、配置git

1）设置username和email（github每次commit都会记录他们）

​        `git config --global user.name "wurui"`

\```    git config --global user.email "1428173426@qq.com"`

   

2)通过终端命令创建ssh key

​      `ssh-keygen -t rsa -C "1428173426@qq.com"`

​    *![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013143233189-204003889.png)*

由于这里我原来已经创建过，这里我选n，没有创建过的，会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在~/下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key

终端查看`.ssh/id_rsa.pub`文件: 

```
                 open .ssh/id_rsa.pub
```

\```回车后，就会新弹出一个终端，然后复制里面的key,``或者用cat命令查看:                 ``cat .ssh/id_rsa.pub`

 

3)登录GitHub（没注册的就先注册），添加ssh key，点击Settings，如图：

​    ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013144311067-1647740102.png)

 

  然后添加SSH Key

![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013144423995-1334229603.png)

 

4）链接验证

​       `ssh -T git@github.com`

```
   终端输出结果： ``  ![img](https://img2018.cnblogs.com/blog/1493506/201810/1493506-20181013144801239-1055664908.png)              
```

 

​    说明已经链接成功

 

## 3.提交本地项目到GitHub

1）在GitHub上新创建一个 repository或者Start a Project，如图：

  ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013145039575-304377688.png)

 

2）填写项目信息，如下图所示：

![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013145344245-815808780.png)

 

3）Clone工程到本地，首先复制ssh 地址

   ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013145611210-772982957.png)

 

4）打开终端，这里只是测试，我想把工程克隆在桌面，首先在终端中切换路径到桌面，输入以下命令：

​                   `cd /Users/jamesruio/Desktop/`

   然后克隆项目,终端输入:

​                 `git clone https://github.com/jamesruio/LearnGit.git`

   https://github.com/jamesruio/LearnGit.git为刚才复制的ssh路径，终端结果如下：

​    ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013150124024-1997993244.png)     

​    这时，工程已经被克隆到桌面了，如下图：

​    ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013150249355-2131758876.png)

 

5)在Xcode中新创建一个工程，保存的路径为刚刚克隆下来的LearnGit文件夹下，如下图所示：

​                                      ![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013150541077-1153183249.png)

 

 

6)提交修改，首先切换到LearnGit文件路径：

​       `cd /Users/jamesruio/Desktop/LearnGit`

  然后输入:

​      *//文件添加到仓库（.代表提交所有文件）*

​    *git add .*

   *//把文件提交到仓库*

​    *git commit -m "First Commit"*

  *//上传到github* 

​    *git push*

*![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013151315997-814014088.png)*

查看GitHub上的项目，LearnGit已经上传成功啦，如下图所示：

![img](/Users/xujiajie/git/LearnGit/resources/1493506-20181013151752904-91209735.png)