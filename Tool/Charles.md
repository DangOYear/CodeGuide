---

---

# Charles使用教程

## 简介

当在开发APP后台的过程中，免不了与APP的开发同学进行联调。

这时候单纯的看日志进行问题定位是较为麻烦的。

使用Charles进行抓包，查看具体调用的接口和查看接口调用的返回结果是一种有效的方式。

## 教程环境

+ MacOS
+ iOS
+ Charles4.5.6

保证电脑和手机在同一网络下，各个教程的环境应该差别不大。

## Charles下载

[下载地址](https://www.charlesproxy.com/latest-release/download.do)

## Charles配置

<img src="../img/Charles设置进行代理.png" alt="image-20200928171325870" style="zoom:50%;" />



这时Charles已经可以抓取HTTP的包，这时候会发现HTTPS的包还是无法识别。



## Charles HTTPS抓包配置

+ Charles配置安装证书

<img src="../img/CharlesHTTP抓包设置.png" alt="image-20200928171558566" style="zoom:50%;" />

信任证书

<img src="../img/CharlesMac设置证书.png" alt="image-20200928171724623" style="zoom: 50%;" />



<img src="../img/Charles信任证书.png" alt="image-20200928171818915" style="zoom: 50%;" />

+ iOS上安装相应的CA证书



<img src="../img/Charles设置服务.png" alt="image-20200928172615179" style="zoom: 33%;" />

+ iOS访问chls.pro/ssl

下载证书

并且在以下两个位置信任证书

设置->通用->关于本机->证书信任设置

<img src="../img/CharlesiOS信任证书1.png" alt="image-20200928173203548" style="zoom:50%;" />

设置->通用->描述文件

<img src="../img/CharlesiOS信任证书2.png" alt="image-20200928173402020" style="zoom:50%;" />

+ Charles添加需要抓取的IP

<img src="../img/Charles设置SSL1.png" alt="image-20200928173512700" style="zoom:50%;" />

<img src="../img/Charles设置SSL2.png" alt="image-20200928173558091" style="zoom:50%;" />

+ iOS设置代理

<img src="../img/CharlesiOSWifi设置1.png" alt="image-20200928180004728" style="zoom:50%;" />

<img src="../img/CharlesiOSWifi设置2.png" alt="image-20200928180042711" style="zoom:50%;" />

+ 填入电脑的IP和端口号

<img src="../img/CharlesiOSWifi设置3.png" alt="image-20200928180117348" style="zoom:50%;" />



## 结束

