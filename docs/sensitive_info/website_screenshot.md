## 网站截图        

对目标网站页面进行截图，通过截图找到敏感页面

### webscreenshot

基于[`url-to-image`](https://github.com/kimmobrunfeldt/url-to-image/)的网站截图工具

- 安装

```
git clone https://github.com/maaaaz/webscreenshot.git

apt-get update && apt-get -y install phantomjs

phantomjs -v

Ubuntu 16 中安装 phantomjs 出现 QXcbConnection 问题
	export QT_QPA_PLATFORM=offscreen
	export QT_QPA_FONTDIR=/usr/share/fonts
```

- 使用

```
cd webscreenshot/

python2.7 webscreenshot.py -i url.txt
```

![](website_screenshot/1594459-20200119161002755-701856606.png)