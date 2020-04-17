## 源码泄露

### 常见源码泄露

```
/.bzr/
/CVS/Entries
/CVS/Root
/.DS_Store  MacOS自动生成
/.hg/
/.svn/ (/.svn/entries)
/.git/
/WEB-INF/src/
/WEB-INF/lib/
/WEB-INF/classes/
/WEB-INF/database.properties
/WEB-INF/web.xml

Robots.txt
```

上述源码泄露在Github上都可以找到相应的利用工具

### 源码泄露扫描工具

将常见源码泄露加入字典配合FUZZ、御剑等扫描器进行扫描收集

### 源码泄露利用工具

- .git源码泄露：https://github.com/lijiejie/GitHack

- .DS_Store泄露：https://github.com/lijiejie/ds_store_exp

- .bzr、CVS、.svn、.hg源码泄露：https://github.com/kost/dvcs-ripper