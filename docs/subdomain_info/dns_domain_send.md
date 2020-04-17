## DNS域传送漏洞

目前来看"DNS域传送漏洞"已经很少了。

### DNS记录分类

常见的DNS记录有以下几类：

```
A记录       IP地址记录,记录一个域名对应的IP地址
AAAA记录    IPv6地址记录，记录一个域名对应的IPv6地址
CNAME记录   别名记录，记录一个主机的别名
MX记录      电子邮件交换记录，记录一个邮件域名对应的IP地址
NS记录      域名服务器记录 ,记录该域名由哪台域名服务器解析
PTR记录     反向记录，也即从IP地址到域名的一条记录
TXT记录     记录域名的相关文本信息
```

### DNS注册信息

Whois查询

### DNS域传送漏洞原理

DNS服务器分为：`主服务器`、`备份服务器`和`缓存服务器`。在主备服务器之间同步数据库，需要使用`“DNS域传送”`。域传送是指备份服务器从主服务器拷贝数据，并用得到的数据更新自身数据库。

若DNS服务器配置不当，可能导致攻击者获取某个域的所有记录。造成整个网络的拓扑结构泄露给潜在的攻击者，包括一些安全性较低的内部主机，如测试服务器。同时，黑客可以快速的判定出某个特定zone的所有主机，收集域信息，选择攻击目标，找出未使用的IP地址，绕过基于网络的访问控制。

### DNS域传送漏洞检测

#### nslookup

基本过程

```
1) nslookup             #进入交互式shell
2) server dns.xx.yy.zz  #设定查询将要使用的DNS服务器
3) ls xx.yy.zz          #列出某个域中的所有域名
4) exit                 #退出
```

漏洞检验-不存在漏洞

```
> nslookup
Server:  lkwifi.cn
Address:  192.168.68.1

*** lkwifi.cn can't find nslookup: Non-existent domain
> server ss2.bjfu.edu.cn
Default Server:  ss2.bjfu.edu.cn
Address:  202.204.112.67

> ls bjfu.edu.cn
[ss2.bjfu.edu.cn]
*** Can't list domain bjfu.edu.cn: Query refused
The DNS server refused to transfer the zone bjfu.edu.cn to your computer. If this
is incorrect, check the zone transfer security settings for bjfu.edu.cn on the DNS
server at IP address 202.204.112.67.

> exit
```

漏洞检验-存在漏洞

```
> nslookup
> server dns1.xxx.edu.cn
> ls xxx.edu.cn
```

![](dns_domain_send/1594459-20200119142122378-365876425.png)

#### nmap

利用nmap漏洞检测脚本"dns-zone-transfer"进行检测

```
nmap --script dns-zone-transfer --script-args dns-zone-transfer.domain=xxx.edu.cn -p 53 -Pn dns.xxx.edu.cn
```

```
--script dns-zone-transfer 表示加载nmap漏洞检测脚本dns-zone-transfer.nse，扩展名.nse可省略

--script-args dns-zone-transfer.domain=xxx.edu.cn 向脚本传递参数，设置列出某个域中的所有域名

-p 53 设置扫描53端口

-Pn 设置通过Ping发现主机是否存活
```

![](dns_domain_send/1594459-20200119142135615-565066925.png)

#### dig

使用说明 `dig -h`

漏洞测试

```
dig @dns.xxx.edu.cn axfr xxx.edu.cn
```

`axfr` 是q-type类型的一种: axfr类型是Authoritative Transfer的缩写，指请求传送某个区域的全部记录。

![](dns_domain_send/1594459-20200119142148997-23789284.png)