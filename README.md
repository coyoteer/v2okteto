# 在Okteto云部署v2ray

## 注意本项目有封号的风险，不要用常用的github账号

---

## 概述

### 注册地址：https://okteto.com/
本项目用于在Okteto上部署V2Ray WebSocket，部署完成后，每次启动应用时，运行的 V2Ray 将始终为最新版本

## 部署

### 步骤

 1. Fork 本专案到自己的 GitHub 账户（用户名以 `example` 为例）
 2. 如果有需要，修改UUID。在  `entrypoint.sh` 这个文件里修改
 3. 点击部署 ![image](https://user-images.githubusercontent.com/89477009/133904828-38ef592c-ece3-45e7-a85e-812af23b756a.png)
 4. 按要求链接后，找到本项目 ![image](https://user-images.githubusercontent.com/89477009/133905123-d40e3b72-49a5-46ca-9755-995f15dd49e5.png)  部署就行了

 

### 变量

对部署时需设定的变量名称做如下说明。

`ID`：`ad806487-2d26-4636-98b6-ab85cc8521f7`
`AID`：`64`
`WSPATH`：`/`

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
