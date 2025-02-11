本文主要介绍如何快速地将腾讯云 TRTC Electron SDK 集成到您的项目中。

## 支持的平台
-  Windows(PC)
-  Mac

## 环境要求

#### Windows 

前往 [下载地址](https://nodejs.org/en/download/)，选择 Windows 32-bit 版本，安装 node 环境。

>!trtc electron sdk 目前仅支持 Windows 32-bit 版本。

#### Mac

使用命令行安装 node:
```
brew install node
```

## 集成 TRTC Electron SDK

在您的项目中使用 npm 安装 SDK 包。

```
npm install trtc-eletron-sdk --save
```

在项目脚本里引入模块。

```javascript
const TRTCCloud = require('trtc-electron-sdk');
```

## 常见问题

### 1. 防火墙有什么限制？

由于 SDK 使用 UDP 协议进行音视频传输，所以对 UDP 有拦截的办公网络下无法使用，如遇到类似问题，请参考 [应对公司防火墙限制](https://cloud.tencent.com/document/product/647/34399)。
