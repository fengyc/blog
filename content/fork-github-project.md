Title: 参与 github 开源项目开发    
Date: 2015-07-13 21:20    
Category: blog    
Tags: blog  github  
Slug: fork-github-project  
Author: Yingcai FENG

开源是一种态度，只要想参与，都可以向开源社区贡献力量。参与到开源并不只是提交代码，还可以以很多方式参与，如提交 bug ，给出建议，帮助更新文档，协助进行本地化等等。再加上现在有 github 这样方便的工具，参与到开源其实是很简单的事情。

github 上有很多的开源项目，并提供一些辅助的工具来帮助项目发展，如 Issues 、 Pull requests 、 Wiki 、 GitHub Pages 等等。

github 使用 git 作为 VCS 系统。如果想向项目贡献代码，还是需要了解 git 的基本使用，最好还了解 gitflow、gerrit 等等周边工具，很多项目会同时使用这些工具来作为分支流程管理标准和代码审核、bug跟踪管理等等。

github 上通过 fork 克隆一个项目到自己的 github 库，然后自己用 git 下载下来修改，修改完毕后，更新到 github 上。然后可以通过创建一个 Pull request 给项目维护者，让维护者把你的代码合并进项目里面。

具体的操作如下：

    <fork 代码库>
    git clone <你的代码库 URL>
    <修改>
    git commit -a '<修改信息>'
    git push
    <创建 pull request>

如果修改的时间很长，这个时候可能原始代码库已有其他人的更新，因此需要把其他人的更新合并到自己的代码库中。首先要把原始代码库作为 git 的远程库，通常这个远程库以 upstream 为名字:

    git remote add upstream <原始代码库 URL>

然后，取得 upstream 的更新：

    git fetch upstream

并合并到当前分支，以 origin/master 为例：

    git merge upstream/master origin/master
    git push

一般来说，建议以 ssh + 非对称密钥 方式访问 git，这样安全性比较高，同时不需要在 push 时输入口令，相对方便一点。

ssh + 非对称密钥的方法也很简单。首先，生成一对公私钥：

    ssh-keygen -t rsa -C '<你的邮箱>'

生成的公私钥在 `~/.ssh/id_rsa` `~/.ssh/id_rsa.pub` 中。然后在github的账户设置SSH-keys中，把 `~/.ssh/id_rsa.pub` 的内容拷贝到一个新的 ssh key。并使用以下的命令测试是否成功：

    ssh -T git@github.com

测试成功时，会显示：

    Hi <xxx>! You've successfully authenticated, but GitHub does not provide shell access.

