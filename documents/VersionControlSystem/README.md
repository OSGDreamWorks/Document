# 版本控制工具git使用 #

**为什么要用git控制项目版本**
**BitBucket使用教程**
**git基础教程**
**团队合作注意事项**

# 为什么要用git控制项目版本

首先是管理代码，很多时候你会把你写的东西复制好几份，而正确的运用版本控制工具就没有这个必要。举个例子，比如你之前已经开发到一个状态，现在你要加上一个功能，然后你搞了很久发现把整个东西都搞乱掉了，你想回到之前修改前的状态。这个时候如果你之前有备份一个的话还有救，要是没有的话你就得十分小心的往回改，要耗费大量时间，往往还容易出问题。如果用了版本控制工具的话，一个revert轻松搞定，也不需要你自己手动备份什么的。其次是代码安全，用git的话由于它采用分布式的设计，一般本地一个仓库，远程一个仓库，如果你出现事故把东西弄没了可以轻松的从远程恢复。

# BitBucket使用教程
BitBucket简单来讲就是和Google Code，SourceForge类似的一个代码hosting站点。更有名的有一个GitHub，这个是基于Git的，一直以来各方面都做得比基于Hg的BitBucket好很多。然则BitBucket宣布加入Atlassian，并对免费用户提供无限的私人代码托管，我们可以利用BitBucket作为自己私人代码首，对于个人或者创业公司来说，非常方便。

*接下来让我们相创建账号。
在https://bitbucket.org注册一个新用户
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/101.jpg" width=512>
填写注册的详细信息,注册后使用电子邮件激活就可以了。
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/102.jpg" width=512>

*然后建立repository。如果是参与合作请略过此步。
登陆后可以创建自己的 repository 了
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/103.jpg" width=512>
这里我使用的 Repository Type 是 Git当然也可以使用别的，上面要把名称填好。
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/104.jpg" width=512>
这里可以把这个repository 设置为私有的 private 这样只有自己能访问到。
创建完成后 我们会得到一个repository 的地址：https://xxxxxxx@bitbucket.org/xxxxxxx/xxxxxxxxxxxxx.git
(其中 xxxx部分为自己的用户名和工程名等等。)

*然后生成ssh key或者BitBucket支持直接输入密码https下载。
在终端中运行ssh-keygen。
$ ssh-keygen -t rsa -C "your_email@example.com"
然后一路enter，直接到结束。不要理会中间的输入。
打开用户目录下.ssh/id_rsa.pub文件，复制其内容。
Bitbucket上点右上角的小头像，然后选择Manage account.
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/105.jpg" width=512>
左边目录选择SSH Keys， 然后选择add key。将刚才复制的内容粘贴进去，保存。
回到工程页面，将使用的协议选择为SSH。

*接下来通过克隆下载代码，修改提交，上传，实现多人合作开发。
我使用的是msysgit

# git基础教程
这里有两种工作方式 Git GUI(有操作界面的) 和 Git Bash(纯命令行)。首先介绍一下Bash命令

*创建或者克隆版本库。克隆用git clone命令，创建用git init。
使用git clone https://xxxxxxx@bitbucket.org/xxxxxxx/xxxxxxxxxxxxx.git
刚刚创建的代码仓库可以下载代码。
$ git clone 远程地址
如果新建需要用git init来初始化仓库并用 git remote add origin 来添加远程地址
$ git remote add origin 远程地址

*添加与修改文件 git add文文件。
使用add来将一个文件加入版本控制
$ git add 文件名
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/201.jpg" width=512>
使用git status查看文件状态
$ git status
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/201.jpg" width=512>

*提交版本上传
$ git commit -m “说明”。

*GUI操作git。
打开Git GUI，可以新建一个版本库，也可以打开一个现有的版本库
$ git gui
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/203.jpg" width=512>
创建一个新的版本库，指定本机的工作目录，指定好以后点击新建就好。
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/204.jpg" width=512>
创建了新的工作目录后，我们需要把这个工作目录和 Bitbucket上的 repository 绑定到一起，需要先添加一个remote。如果是第一次使用repository，我们要先初始化一下(选择 Initialize Remote Repository and Push)。
接下来我们需要准备代码，在界面的左侧，我们可以通过单击 “未缓存的改动” 列表中的项把它们添加到 "已缓存的改动" 列表中
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/205.jpg" width=512>
选好将要上传的代码后，就可以上传了。
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/206.jpg" width=512>
目标版本库的名字就是我们在第四步中填写的名字。
<img src="https://raw.githubusercontent.com/OSGDreamWorks/Document/master/resource/documents/VersionControlSystem/207.jpg" width=512>
当我们登陆到Bitbucket时可以看到我们的代码了，说明操作成功了。

# 团队合作注意事项
*细分项目
尽量分模块，每个人工作在不同的模块，可以一个文件夹代表一个模块。
*规避冲突
尽量避免同时修改同一个文件，必须避免修改同一个2进制文件，如同一张图，这样的冲突是无法解决的
*减少存储
不要把项目的工程文件上传，避免仓库过大，一般不需要上传的文件写在.gitignore里面