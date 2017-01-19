## 设置vsftpd

首先关闭SELINUX

在`/etc/selinux/config`中配置

`SELINUX=disable`

重启后selinux就关闭了。

运行命令`dnf install vsftpd`，安装vsftpd

配置`/etc/vsftpd/vsftpd.conf`

```
#不允许匿名登录
anonymous_enable=NO

#允许本地登录
local_enable=YES

#允许写
write_enable=YES

#创建文件的umask，设置为002是为了让同组用户可以修改，创建文件为775权限
local_umask=002

```

`systemctl start vsftpd.service`运行vsftpd服务

## 添加用户组

`groupadd yourgroupname` 添加组名。

为组用户建个目录`mkdir yourgroupdirectory`

把该目录的所有权给组用户`chown root:yourgroupname yourgroupdirectoy`

设置该目录的权限`chmod 775 yourgroupdirectoy`

该目录就可以被所有组成员共享了。

## 添加用户

Linux 添加用户时会建立一个与用户同名的组，这个组叫做user private group 文档中说是为了方便管理用户用的，就当是这样吧。

所以在建立用户的时候如果不想建立user private group，使用 `useradd -N`命令

`useradd yourusername -N -d userhomedirectory -s /sbin/nologin -g yourgroupname`

`-d`后目录指定该用户的主目录，`/sbin/nologin`说明这个用户不能登录系统。


