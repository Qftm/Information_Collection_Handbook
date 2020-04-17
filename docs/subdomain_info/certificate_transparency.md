## 证书透明度公开日志枚举


证书透明度(Certificate Transparency, CT)是证书授权机构(CA) 的一个项目，证书授权机构会将每个SSL/TLS证书发布到公共日志中。一个SSL/TLS证书通常包含域名、子域名和邮件地址， 这些也经常成为攻击者非常希望获得的有用信息。查找某个域名所属证书的最简单的方法就是使用搜索引|擎搜索一些公开的CT日志。

### 在线第三方平台查询

- [crt.sh](https://crt.sh)
- [censys](https://censys.io)
- [myssl](https://myssl.com)

```
crt:
https://crt.sh/?q=baidu.com
```

![](certificate_transparency/1594459-20200119142032842-592842557.png)
![](certificate_transparency/1594459-20200119142046971-121764509.png)

```
censys:
https://www.censys.io/certificates?q=baidu.com
```


![](certificate_transparency/1594459-20200119142058672-37856097.png)

### 工具枚举查询

通过工具可以调用各个证书接口进行域名查询 

常用工具

```
Findomain
Sublist3r（SSL Certificates）等
```

#### Findomain

Findomain不使用子域名寻找的常规方法，而是使用证书透明度日志来查找子域，并且该方法使其工具更加快速和可靠。该工具使用多个公共API来执行搜索：

```
Certspotter
Crt.sh
Virustotal
Sublist3r
Facebook 
Spyse (CertDB)
Bufferover
Threadcrow
Virustotal with apikey 
```

项目地址：`https://github.com/Edu4rdSHL/findomain`

子域名收集：`findomain -t target.com `

使用所有API搜索子域并将数据导出到CSV文件：`findomain -t target.com -a -o csv`