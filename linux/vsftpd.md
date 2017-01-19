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

`systemctl start vsftpd.service`

