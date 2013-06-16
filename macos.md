mac os 备份
=====

### 安装tengine 

下载：[http://tengine.taobao.org/](http://tengine.taobao.org/)

```shell
./configure --with-http_concat_module
make
sudo make install
```

```shell
sudo nginx -t //检测配置文件是否有效
sudo nginx -s reload //重启
launchctl load -F /System/Library/LaunchDaemons/nginx.plist
```
### php

```shell
sudo port install php5 +fastcgi fcgi php5-gd php5-mysql php5-sqlite php5-eaccelerator php5-curl php5-iconv
```

将时区修改为：date.timezone = Asia/Chongqing

错误级别修改为：error_reporting = E_ALL & ~E_NOTICE

```shell
cd /Library/LaunchDaemons/
sudo vim org.macports.phpfcgi.plist
```

```shell
sudo launchctl load -w org.macports.phpfcgi.plist
sudo /opt/local/bin/spawn-fcgi -C 2 -p 9000 -f /opt/local/bin/php-cgi
sudo launchctl unload -w org.macports.phpfcgi.plist
pkill php-cgi
sudo launchctl load -w org.macports.phpfcgi.plist
```