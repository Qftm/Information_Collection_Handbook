## 工具枚举

常用子域名工具如下（Github上都可搜到）

```
OneForAll
Layer
Sublist3r
subDomainsBrute
K8
wydomain
dnsmaper
dnsbrute
Findomain
fierce等
```

个人推荐：`OneForAll`、`Layer`、`Sublist3r`、`subDomainsBrute`

### OneForAll

OneForAll是一款功能强大的子域收集工具，拥有多个模块和接口扫描，收集子域信息很全，包括子域、子域IP、子域常用端口、子域Title、子域Banner、子域状态等。

项目地址：`https://github.com/shmilylty/OneForAll`

子域名收集：`python3 oneforall.py --target=target.com run`

![](tools/1594459-20200119141949690-706245006.png)

### Layer

Layer子域名挖掘机的使用方法比较简单，在域名对话框中直接输入域名就可以进行扫描，它的显示界面比较细致，有域名、解析IP、开放端口、Web服务器和网站状态等

![](tools/1594459-20200119142000597-497061730.png)

### subDomainsBrute

subDomainsBrute的特点是可以用小字典递归地发现三级域名、四级域名,甚至五级域名等不容易被探测到的域名。

项目地址：`https://github.com/lijiejie/subDomainsBrute`

子域名收集：`python subDomainsbrute.py xtarget.com`

### Sublist3r

Sublist3r也是一个比较常用的工具， 它能列举多种资源，如在Google、Yahoo、 Bing、 Baidu和Ask等搜索引擎中可查到的子域名，还可以列出Netcraft、VirusTotal、ThreatCrowd、 DNSdumpster、SSL Certificates、和Reverse DNS查到的子域名。

项目地址：`https://github.com/aboul3la/Sublist3r`

子域名收集：`python sublist3r.py -d target.com -b -t 50 -p 80,443,21,22`

![](tools/1594459-20200119142016505-176536179.png)

