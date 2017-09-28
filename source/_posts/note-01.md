---
title: note-01
date: 2017-09-28 15:26:30
categories: note
---

{% note default %} curl {% endnote %}
```sh
curl -X GET [URL] -H "DAAUTH:token [tokenStr]]"
curl -X GET [URL] -H "DAAUTH:basic [base64_encode('username:pwd')]" -H "API:mobile 1.0"
```
***

# Apache
> ## httpd

```dos
$ httpd.exe -k install -n "httpd-2.4.27-vc14"
$ httpd.exe -k uninstall -n "httpd-2.4.27-vc14"
```
***

# PHP
> ## php扩展库curl

+ 将php解压文件中的libssh2.dll、php_curl.dll、ssleay32.dll、libeay32.dll放入Windows/System32文件夹(即使是用64位系统)
+ 然后，把libssh2.dll放入Apache2.4解压目录下的bin文件夹
+ 最后，在php.ini中，把extension=php_curl.dll前面的分号去掉,重启Apache，OK！

> ## php odbc hive

```
Driver={%s};HiveServerType=2;AuthMech=2;Schema=dm_finance;host=%s;port=%d
```

> ## php 

+ ### isset 
    + 若变量不存在则返回 FALSE 
    + 若变量存在且其值为NULL，也返回 FALSE 
    + 若变量存在且值不为NULL，则返回 TURE 
+ ### empty
    + ""、0、"0"、NULL、、FALSE、array()、var $var; 以及没有任何属性的对象
***

# Windows
> ## windows cmd

+ ### net user
```dos
net user test testpwd /add 
net localgroup administrators test /add 
net localgroup admimistrators
net user test
net localgroup admimistrators test /del 
net user test /del
net users
```
+ ### 以某个用户运行
```dos
runas /user:jiangjh5 cmd
```
+ ### win+R 快捷命令
  - msconfig
  - shell:startup
***

# JS
> ## JS

+ getEventListeners($0)
+ $("").trigger("");
***

# Postgres
> ## postgres

+ select * from pg_available_extensions;
+ CREATE EXTENSION tablefunc;
```sh
$ sudo su postgres
$ psql

$ \l // list database
$ \c // connect a database
$ \conninfo // 数据库连接信息
```
***

# Java Keytool
> ## 查看apk签名信息

+ keytool -list -printcert -jarfile codata_v0.11.20170912_release_20170912183830.apks

> ## adb shell dumpsys activity

+ adb shell dumpsys activity activities // 导出task任务栈

> ## adb pull 日志文件到本地目录

+ adb pull /sdcard/crash .
