# ServerStatus-Hotaru
云探针、多服务器探针、云监控、多服务器云监控

基于ServerStatus-Toyo最新版本稍作修改，不太会脚本什么的，前端也垃圾。见谅

此项目又是从沐柏梓那借鉴~~白嫖~~来的 为了通用性做了适当修改~~删掉了他的所有信息~~XD

Test v0.014：图片来源：Pixiv：72725286

## 特性

``` 
	caddy提供基础web功能非nginx
```

多了个Region调用国旗。所以用原来Toyo版的需要稍作修改

Region的值的参考地址：
https://github.com/mylovesaber/ServerStatus-Hotaru/tree/master/web/img/clients


**web位于服务端**

## 安装方法

`系统要求：CentOS 7、Debian 7+、Ubuntu 14.04+、debian9+`

#### 使用命令下载脚本：
```bash
wget https://raw.githubusercontent.com/mylovesaber/ServerStatus-Hotaru/master/status.sh -P /root && chmod +x /root/status.sh && cd /root
```

#### 安装服务端：
```bash
bash status.sh s
#按1进入安装过程
```
会依次提示以下信息（以域名www.baidu.com 为例）：

```markdown
请输入 ServerStatus 服务端监听的端口[1-65535]（用于服务端接收客户端消息的端口，客户端要填写这个端口）
(默认: 35601):
#此端口在服务端和若干客户端中必须保证完全一样才能连接成功
```

```markdown
[信息] 是否由脚本自动配置HTTP服务(服务端的在线监控网站)，如果选择 N，则请在其他HTTP服务中配置网站根目录为：/usr/local/ServerStatus/web [Y/n]
(默认: Y 自动部署):
#默认即可
```

```markdown
请输入 ServerStatus 服务端中网站要设置的 域名[server]
默认为本机IP为域名，例如输入: toyoo.pw ，如果要使用本机IP，请留空直接回车
(默认: 本机IP):
#本机ip是127.0.0.1，如果本机域名为www.baidu.com，则可以填写此域名，之后客户端配置中将统一使用www.baidu.com
```

```markdown
请输入 ServerStatus 服务端中网站要设置的 域名/IP的端口[1-65535]（如果是域名的话，一般用 80 端口）
(默认: 8888):
#此端口设置后，浏览器打开www.baidu.com:8888即可看到此探针的网页
```

至此服务端安装完成

#### 安装客户端

```bash
bash status.sh c
#按1进入安装过程
```
会依次提示以下信息（以server端的域名www.baidu.com 为例）：

```markdown
[信息] 开始设置 用户配置...
请输入 ServerStatus 服务端的 IP/域名[server]
(默认: 127.0.0.1):
#如果一台服务器上同时安装客户端和服务端，那么可以选择默认，否则需要输入域名www.baidu.com或者作为服务端的服务器ip
```

```markdown
请输入 ServerStatus 服务端监听的端口[1-65535]（用于服务端接收客户端消息的端口，客户端要填写这个端口）
(默认: 35601):
#此端口在服务端和若干客户端中必须保证完全一样才能连接成功
```

```markdown
请输入 ServerStatus 服务端中对应配置的用户名[username]（字母/数字，不可与其他账号重复）
(默认: 取消):
#一个客户端一个用户名，此用户名和后面的密码会在之后服务端配置时会用得上
```

```markdown
请输入 ServerStatus 服务端中对应配置的密码[password]（字母/数字）
(默认: doub.io):
#可以多客户端使用相同密码
```

#### 配置服务端
修改配置文件文件：
```bash
/usr/local/ServerStatus/server/config.json
```

以下展示添加了两个客户端的写法：

```json
{"servers":
 [
  {
   "username": "aaa",
   "password": "111",
   "name": "随便填",
   "type": "随便填",
   "host": "客户端ip",
   "location": "随便填",
   "disabled": false ,
   "region": "国家名缩写例：德国是填写DE"
  },
  {
   "username": "bbb",
   "password": "222",
   "name": "坑爹op",
   "type": "独服",
   "host": "127.0.0.1（此处因为客户端和服务端同处一台机器，所以可以填写本地ip）",
   "location": "法国",
   "disabled": false,
   "region": "FR"
  }
 ]
}
```

单个客户端写法：

```json
{"servers":
 [
  {
   "username": "aaa",
   "password": "111",
   "name": "随便填",
   "type": "随便填",
   "host": "客户端ip",
   "location": "随便填",
   "disabled": false ,
   "region": "国家名缩写例：德国是填写DE"
  }
 ]
}
```


修改完成并保存退出后重启服务端即可完成配置

## 一些说明

网络实时流量单位为：G=GB/s，M=MB/s，K=KB/s

服务器总流量单位为：T=TB，G=GB，M=MB，K=KB

如果要修改网页标题或者网页顶部公告内容，打开/usr/local/ServerStatus/web/index.html

如果安装的toyo的版本，需卸载ServerStatus-Toyo安装ServerStatus-Hotaru，之后修改或替换配置文件，重启ServerStatus服务端即可（客户端&服务端重启方法见下）

## 相关文件位置
安装目录：/usr/local/ServerStatus

网页文件：/usr/local/ServerStatus/web

配置文件：/usr/local/ServerStatus/server/config.json

客户端查看日志：tail -f tmp/serverstatus_client.log

服务端查看日志：tail -f /tmp/serverstatus_server.log

## 服务端控制命令

**启动**：/etc/init.d/status-server start

**停止**：/etc/init.d/status-server stop

**重启**：/etc/init.d/status-server restart

**查看状态**：/etc/init.d/status-server status

## 客户端控制命令

**启动**：/etc/init.d/status-client start

**停止**：/etc/init.d/status-client stop

**重启**：/etc/init.d/status-client restart

**查看状态**：/etc/init.d/status-client status

## Caddy（HTTP服务）：

**启动**：/etc/init.d/caddy start

**停止**：/etc/init.d/caddy stop

**重启**：/etc/init.d/caddy restart

**查看状态**：/etc/init.d/caddy status

**Caddy配置文件**：/usr/local/caddy/Caddyfile

## 效果演示

![](https://i.loli.net/2019/04/05/5ca74fb05338f.png)

![](https://i.loli.net/2019/04/05/5ca74fc86db96.png)

当然前端可以自己自定义。

## 相关开源项目 ： 
* 原始脚本：https://github.com/ToyoDAdoubi/ServerStatus-Toyo
* 修改脚本：https://github.com/CokeMine/ServerStatus-Hotaru
* 模板来源：https://www.hostloc.com/thread-494384-1-1.html
* ServerStatus：https://github.com/BotoX/ServerStatus
* mojeda: https://github.com/mojeda 
* mojeda's ServerStatus: https://github.com/mojeda/ServerStatus
* BlueVM's project: http://www.lowendtalk.com/discussion/comment/169690#Comment_169690
* 逗比根据地：https://doubibackup.com/
