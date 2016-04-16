linux在使用过程中自我总结的技巧，会保持更新。

## 安装字体

linux下安装字体其实很简单，并不需要root权限。

把下载好的字体放在`~/.fonts/`目录底下。如果该目录不存在，使用`mkdir`建立该目录。

使用命令`fc-cache ~/.fonts`让字体生效。

`DejaVu San Mono`字体在emacs里显示得有点奇怪，10号字体常见得太小，12号又太大，11号字体看上去不像等宽字体。

`Liberation Mono`字体感觉起来不错，设为以后默认使用的字体。

## xfce4 teminal 主题设置

网络上大都是教我们把他们定义好的`terminalrc`放到`~/.config/xfce4/terminal`下。

这种做法是可以的，但是每次要修改termial主题时都要重新放置一次该文件，不太方便。

我们可以根据terminalrc里的内容把它改变成`*.theme`文件。

把该文件放在`/usr/share/xfce4/terminal/colorschemes`中，这样就可以在xfce terminal的首选项里找到该配置，非常方便。

下以`solarized`为例，把`github`上`Base16-xfce4-terminal`clone下来

把文件加上以下内容

```
[Scheme]
Name=WeiSolarized (dark)
```

去掉原来`terminalrc`里面的`[configuration]`把文件另存为`*.theme`放入先前说的目录中，修改就完成了。

把修改后的`*.theme`放在目录底下。


## 生成ssh key

在没有key认证前，要在小本子上记录好多服务器的密码。

有了key后，把它加入到服务器的信任列表中，就没有这些困扰了。

```
ssh-keygen -t rsa -b 2048 -f /path/keyname
```

会在path下生成`keyname`和`keyname.pub`文件。

把`keyname.pub`的内容贴到服务器`~/.ssh/authorized_keys`中

或者使用`ssh-copy-id user@ip`来完成该步聚。

在client端把生成的`keyname`和`keyname.pub`放入`~/.ssh`中

如果你只需要一个key，那么把`keyname`和`keyname.pub`重命名为`id_rsa`和`id_rsa.pub`。

如果有多个key，需要配置`~/.ssh/config`文件来区分这些key分别是用来登录哪台服务器。

```
Host github.com
IdentityFile ~/.ssh/keyname
```

通过上条命令的配置，我们就能使用`~/.ssh/`目录下的`keyname`这个key来登录[github.com](https://github.com)

## sublime text

安装inputHelper来实现中文的输入。

在目录.config/sublime-text-3/Packages中，运行`git clone https://github.com/xgenvn/InputHelper.git`完成安装

默认使用`ctrl+shift+z`打开Input Helper。
