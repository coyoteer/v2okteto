# oktetov2ray
# V2Ray Okteto

## 注意本项目有封号的风险，不要用常用的github账号

## 概述

### 注册地址：https://okteto.com/
本专案用于在 Okteto上部署 V2Ray WebSocket，

部署完成后，每次启动应用时，运行的 V2Ray 将始终为最新版本

## 首先声明一下

### 本项目为 https://github.com/bclswl0827/v2ray-heroku 大佬的heroku项目修改，因为有人反映同时fork二者会有冲突，我才将此重新上传改为本人的项目
### 不是剽窃，感谢bclswl0827大佬的付出，谢谢！

## 部署

### 步骤

 1. Fork 本专案到自己的 GitHub 账户（用户名以 `example` 为例）
 2. 如果有需要，修改UUID  在  `entrypoint.sh` 这个文件里修改
 3. 点击部署 ![image](https://user-images.githubusercontent.com/89477009/133904828-38ef592c-ece3-45e7-a85e-812af23b756a.png)
 4. 按要求链接后，找到本项目 ![image](https://user-images.githubusercontent.com/89477009/133905123-d40e3b72-49a5-46ca-9755-995f15dd49e5.png)  部署就行了

 

### 变量

对部署时需设定的变量名称做如下说明。

| 变量 | 默认值 | 说明 |
| :--- | :--- | :--- |
| `ID` | `ad806487-2d26-4636-98b6-ab85cc8521f7` | VMess 用户主 ID，用于身份验证，为 UUID 格式 |
| `AID` | `64` | 为进一步防止被探测所设额外 ID，即 AlterID，范围为 0 至 65535 |
| `WSPATH` | `/` | WebSocket 所使用的 HTTP 协议路径 |

## 接入 CloudFlare

以下两种方式均可以将应用接入 CloudFlare，从而在一定程度上提升速度。

 1. 为应用绑定域名，并将该域名接入 CloudFlare
 2. 通过 CloudFlare Workers 反向代理

## 注意

 1. **请勿滥用本专案，类似 Heroku 的免费服务少之又少，且用且珍惜**
 2. 若使用域名接入 CloudFlare，请考虑启用 TLS 1.3
 3. AWS 绝大部分 IPv4 地址已被 Twitter 屏蔽
