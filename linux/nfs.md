## 如何在CentOS 7搭建nfs服务器端

1. 服务器端安装**nfs-utils**和**rpcbind**。

2. 创建共享目录，例如：/home/mntxwall/share，并设置目录权限。

3. 编辑/etc/exports文件，格式如下：

```
/home/mntxwall/share *(rw,sync,root_squash)
```

使用`exportfs -r` 使配置生效

4. 启动rpcbind和nfs-service服务

`systemctl start rpcbind && systemctl start nfs`

5. 使用`rpcinfo -p`查看使用了哪些端口

```
   program vers proto   port  service                      
    100000    4   tcp    111  portmapper                                                                               
    100000    3   tcp    111  portmapper                                                   
    100000    2   tcp    111  portmapper                 
    100000    4   udp    111  portmapper                      
    100000    3   udp    111  portmapper                     
    100000    2   udp    111  portmapper                                                       
    100024    1   udp  43561  status                                        
    100024    1   tcp  44459  status                                                                        
    100005    1   udp  20048  mountd                  
    100005    1   tcp  20048  mountd                                                           
    100005    2   udp  20048  mountd                       
    100005    2   tcp  20048  mountd                                  
    100005    3   udp  20048  mountd                              
    100005    3   tcp  20048  mountd                                                               
    100003    3   tcp   2049  nfs                             
    100003    4   tcp   2049  nfs                                      
    100227    3   tcp   2049  nfs_acl                               
    100021    1   udp  52548  nlockmgr                                      
    100021    3   udp  52548  nlockmgr           
    100021    4   udp  52548  nlockmgr            
    100021    1   tcp  37969  nlockmgr     
    100021    3   tcp  37969  nlockmgr         
    100021    4   tcp  37969  nlockmgr
```

记录下这些端口，写入`/etc/sysconfig/nfs`文件中

```
MOUNTD_PORT=20048                                                        
STATD_TCPPORT=44459                            
STATD_UDPPORT=43561                           
LOCKD_TCPPORT=37969                                 
LOCKD_UDPPORT=52548 
```

6. 在防火墙中开放这些端口，具体操作参考`firewall.md`
