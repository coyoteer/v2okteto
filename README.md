# 在Okteto云部署v2ray

## 注意本项目有封号的风险，不要用常用的github账号

## 概述

注册地址：https://okteto.com/

本项目用于在Okteto上部署V2Ray WebSocket，部署完成后，每次启动应用时，运行的 V2Ray 将始终为最新版本

## 部署

### 步骤

1. 登录Okteto云，点击Deploy

![](https://img.misaka.sbs/imgs/20210919162316.png)

2. 复制本项目的git地址 `https://github.com/vhqyeo50893/v2okteto.git`
3. 点击Git URL，粘贴git地址，点击`Deploy`

![](https://img.misaka.sbs/imgs/20210919162442.png)

 

### 变量

对部署时需设定的变量名称做如下说明。

`uuid`：`ad806487-2d26-4636-98b6-ab85cc8521f7`

`端口`：`443`

`额外id`：`64`

`传输协议`：`ws`

`伪装域名`：`okteto app的域名或cf workers域名`

`路径`：`/`

`底层传输安全`：`tls`

## 接入 CloudFlare

cf workers反代代码：

```
const SingleDay = 'appname.cloud.okteto.net'
const DoubleDay = 'appname.cloud.okteto.net'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
