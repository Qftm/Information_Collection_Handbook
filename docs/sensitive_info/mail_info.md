## 邮箱信息收集

### Infoga

Infoga可从不同的公共源网络（搜索引擎，pgp密钥服务器和shodan）收集电子邮件帐户信息（ip，主机名，国家/地区...）。是一个用法非常简单的工具，但是，对于渗透测试的早期阶段，或者只是为了了解自己公司在互联网上的可见性是非常有效的。

- 安装

```
git clone https://github.com/m4ll0k/Infoga.git /data/infoga
cd /data/infoga
pip3 install requests
python3 infoga.py
```

- 使用

```
python3 infoga.py --domain site.com --source all -v 3 | grep Email | cut -d ' ' -f 3 | uniq | sed -n '/-/!p'
python3 infoga.py --info emailtest@site.com
python3 infoga.py --info emailtest@site.com -b
```

### Google Hacking

```
site:target.com intext:@target.com
site:target.com 邮件
site:target.com email
```

![](mail_info/1594459-20200119161412993-1570311002.png)

### Online Search Email

通过全球最大的几个数据泄露站点在线查询邮箱信息泄露情况

```
https://monitor.firefox.com/

https://haveibeenpwned.com/

https://ghostproject.fr/
```

