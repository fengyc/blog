Title: 调整 ubuntu 的字体  
Date: 2015-07-17 11:20  
Category: blog  
Tags: blog 
Slug: adjust-ubuntu-fonts
Author: Yingcai FENG

安装完 Ubuntu 桌面版本的系统后，在默认情况下，字体的显示效果不是很好，会有模糊等现象。

So ，如果想调整一下字体，首先安装一些中文字体：

    sudo apt-get install fonts-wqy-zenhei
    sudo apt-get install fonts-wqy-microhei
    
这两个文泉驿字体能满足大部分的需求了，对于码农来说，最好还加一个 Adobe 的 source code pro 字体，这个字体用来显示等宽或代码时效果非常好

    wget https://github.com/adobe-fonts/source-code-pro/archive/1.017R.zip -O source-code-pro-1.017R.zip
    unzip source-code-pro-1.017R.zip
    sudo mkdir -p /usr/share/fonts/opentype
    sudo cp source-code-pro-1.017R /usr/share/fonts/opentype
    sudo fc-cache -f -v

安装了字体之后，使用 unity-tweak-tools 调整字体

    sudo apt-get install unity-tweak-tool

在 unity-tweak-tools 的字体选项中，将 monospace font 改成 source-code-pro，然后调整次像素平滑（hinting）为 sligtly等。

按照网上的一些说法，需要调整 `~/.font.conf` 

    <?xml version='1.0'?>
    <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
    <fontconfig>
        <match target="font">
            <edit mode="assign" name="autohint">
                <bool>false</bool>
            </edit>
        </match>
        <match target="font">
            <edit mode="assign" name="rgba">
                <const>rgb</const>
            </edit>
        </match>
        <match target="font">
            <edit mode="assign" name="hinting">
                <bool>true</bool>
            </edit>
        </match>
        <match target="font">
            <edit mode="assign" name="hintstyle">
                <const>hintmedium</const>
            </edit>
        </match>
        <match target="font">
            <edit mode="assign" name="antialias">
                <bool>true</bool>
            </edit>
        </match>
    </fontconfig>

然后，退出重新登录，字体生效。调整过之后，字体会好看一点～

另外，在 http://www.lulinux.com/archives/278 有一个打包好的脚本，用了微软雅黑和宋体，简单好用。
