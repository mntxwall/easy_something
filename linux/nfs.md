## 如何在CentOS 7搭建nfs服务器端

1. 服务器端安装**nfs-utils**和**rpcbind**。

2. 创建共享目录，例如：/home/mntxwall/share，并设置目录权限。

3. 编辑/etc/exports文件，格式如下：

```
/home/mntxwall/share *(rw,sync,root_squash)
```

使用`exportfs -r` 使配置生效

