### 简单配置centos下的firewalld

firewalld引入了zone的概念，配置之前先看看默认的zone是哪个

`firewall-cmd --get-default-zone`

简单点，~~说话的方式简单点，哈哈~~

最简单的使用方式是允许端口，有两种方式

+ 直接允许端口

+ 开启服务来允许端口

## 直接允许端口

`firewall-cmd --zone=yourzone --add-port=yourport/tcp`

## 开启服务来允许端口

服务列表在`/usr/lib/firewalld/services/`下，可以复制一个xml文件到`/et/firewalld/services/test.xml`中

```
<?xml version="1.0" encoding="utf-8"?>
<service>
  <short>Example Service</short>
  <description>This is just an example service.  It probably shouldn't be used on a real system.</description>
  <port protocol="tcp" port="7777"/>
  <port protocol="udp" port="8888"/>
</service>
```

`firewall-cmd --reload`

test服务就会出现在`firewall-cmd --get-services`

`firewall-cmd --zone=yourzone --permanent --add-service=yourservices`
