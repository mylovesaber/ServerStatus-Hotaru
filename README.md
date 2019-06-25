# ServerStatus-Hotaru
云探针、多服务器探针、云监控、多服务器云监控

基于ServerStatus-Toyo最新版本稍作修改，不太会脚本什么的，前端也垃圾。见谅

Test v0.014：图片来源：Pixiv：72725286

## 特性

模板来自：<https://www.hostloc.com/thread-494384-1-1.html>

稍作修改。

多了个Region调用国旗。所以用原来Toyo版的需要稍作修改

web位于服务端

## 安装方法
#安装
系统要求：CentOS 7、Debian 7+、Ubuntu 14.04 +

1.使用命令下载脚本：

wget https://raw.githubusercontent.com/lbq1121/ServerStatus-Hotaru/master/status.sh && chmod +x status.sh
下载脚本后，根据需要安装客户端或者服务端：

 客户端管理菜单
bash status.sh c
 
 服务端管理菜单
bash status.sh s

## 修改方法

配置文件：/usr/local/ServerStatus/server/config.json备份并自行添加Region

![](https://i.loli.net/2019/02/07/5c5bca12df8b0.png)

卸载ServerStatus-Toyo安装ServerStatus-Hotaru替换配置文件，重启ServerStatus


## 效果演示

![](https://i.loli.net/2019/04/05/5ca74fb05338f.png)

![](https://i.loli.net/2019/04/05/5ca74fc86db96.png)

当然前端可以自己自定义。

## 相关开源项目 ： 
* ServerStatus-Toyo：https://github.com/ToyoDAdoubiBackup/ServerStatus-Toyo
* ServerStatus：https://github.com/BotoX/ServerStatus
* mojeda: https://github.com/mojeda 
* mojeda's ServerStatus: https://github.com/mojeda/ServerStatus
* BlueVM's project: http://www.lowendtalk.com/discussion/comment/169690#Comment_169690
