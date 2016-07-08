# Windows 上使用 cygwin 连接到 docker toolbox #

Docker 确实给软件开发带来一些好处，在简化部署、统一开发、测试和生产环境上，有它独到的理念。Linux 上可直接安装 docker ，使用起来也比较简单。 Windows 上是通过虚拟机运行 docker ，然后通过 ssh 连接到虚拟机中。在目前最新的 docker 版本 1.8.3 中，已使用了 docker-machine 来定义 docker 虚拟机，并可以运行多个 docker 虚拟机实例。

Docker toolbox 是一系列 docker 工具的集合，包括 windows 上的 docker client ， docker machine ， Kitematic （实验性的图形界面）， virtualbox 。但是 toolbox 里面缺少了 docker-compose，这个还要想办法解决 （可能可以在 cygwin 的环境下运行）（https://github.com/docker/compose/releases）

Docket toolbox 工具在安装时，带有一个 git for windows 。git for windows 会在右键菜单上注册几个 git 操作，由于已经使用了 tortoise git，就没有必要使用 git for windows。仔细研究了一下，其实 toolbox 只是为了使用 git for windows 里面的 shell 来运行 docker 启动命令，因此完全可以使用 cygwin 等替代。

首先，看看桌面上默认安装的快捷方式

	Docker Quickstart Terminal

查看文件的属性，发现它使用了 git for windows 的 shell 环境，来运行 toolbox 的 start.sh 脚本，直接用 cygwin 的 mintty.exe 替换掉，如下：

	D:\Programs\cygwin\bin\mintty.exe "C:\Program Files\Docker Toolbox\start.sh"

运行，发现脚本运行报错，缺少了 clear 命令。 clear 命令属于 ncurses 包，在 cygwin 的安装工具中，把 ncurses 加上即可。

现在可以把 git for windows 卸载掉了。