## Google Hacking

### GoogleHacking常用语法

1、intext：（仅针对Google有效）
把网页中的正文内容中的某个字符作为搜索的条件

2、intitle：
把网页标题中的某个字符作为搜索的条件

3、cache：
搜索搜索引擎里关于某些内容的缓存，可能会在过期内容中发现有价值的信息

4、filetype/ext：
指定一个格式类型的文件作为搜索对象

5、inurl：
搜索包含指定字符的URL

6、site：
在指定的(域名)站点搜索相关内容

### GoogleHacking其他语法

1、引号 '' "
把关键字打上引号后，把引号部分作为整体来搜索

2、or
同时搜索两个或更多的关键字

3、link
搜索某个网站的链接 link:baidu.com即返回所有和baidu做了链接的URL

4、info
查找指定站点的一些基本信息

### GoogleHackingDatabase

- [google-hacking-database](https://www.exploit-db.com/google-hacking-database)

### GoogleHacking典型用法

- 管理后台地址

```
site:target.com intext:管理 | 后台 | 后台管理 | 登陆 | 登录 | 用户名 | 密码 | 系统 | 账号 | login | system
site:target.com inurl:login | inurl:admin | inurl:manage | inurl:manager | inurl:admin_login | inurl:system | inurl:backend
site:target.com intitle:管理 | 后台 | 后台管理 | 登陆 | 登录
```

- 上传类漏洞地址

```
site:target.com inurl:file
site:target.com inurl:upload
```

- 注入页面

```
site:target.com inurl:php?id=
```

- 编辑器页面

```
site:target.com inurl:ewebeditor
```

- 目录遍历漏洞

```
site:target.com intitle:index.of
```

- SQL错误

```
site:target.com intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:”Warning: mysql_query()" | intext:”Warning: pg_connect()"
```

- phpinfo()

```
site:target.com ext:php intitle:phpinfo "published by the PHP Group"
```

- 配置文件泄露

```
site:target.com ext:.xml | .conf | .cnf | .reg | .inf | .rdp | .cfg | .txt | .ora | .ini
```

- 数据库文件泄露

```
site:target.com ext:.sql | .dbf | .mdb | .db
```

- 日志文件泄露

```
site:target.com ext:.log
```

- 备份和历史文件泄露

```
site:target.com ext:.bkf | .bkp | .old | .backup | .bak | .swp | .rar | .txt | .zip | .7z | .sql | .tar.gz | .tgz | .tar
```

- 公开文件泄露

```
site:target.com filetype:.doc | .docx | .xls | .xlsx | .ppt | .pptx | .odt | .pdf | .rtf | .sxw | .psw | .csv
```

- 邮箱信息 

```
site:target.com intext:@target.com
site:target.com 邮件
site:target.com email
```

- 社工信息

```
site:target.com intitle:账号 | 密码 | 工号 | 学号 | 身份证
```

![](google_hacking/1594459-20200119152425254-1738721113.png)