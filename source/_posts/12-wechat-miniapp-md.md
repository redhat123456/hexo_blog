---
title: '[技术干货] JavaScript 开发微信小程序这样行不行？'
author: Tanger
date: 2020-08-13
tags:
  - 碎碎念
  - 微信小程序
categories:
  - 技术干货
  - 微信小程序
---

# JavaScript 开发微信小程序

## 注册小程序

开发小程序的第一步是注册账号。访问微信公众平台：[https://mp.weixin.qq.com/](https://mp.weixin.qq.com/)，可以看到账号分为三类：

- 服务号
- 订阅号
- 小程序

这里我们只关注“小程序”，点击进入即可注册。

## 配置服务器

微信小程序本身已经提供了大量的 API 接口，满足大多数功能需求。但如果已有后端服务，也可以直接在小程序中调用已有接口，甚至直接嵌入已有网页。

如果有这方面需求，首先需要在小程序控制台做一些设置：

### 1. appid 和 AppSecret

在“小程序设置” - “开发者 ID”页面可以获取：

- **AppID**：小程序唯一标识；
- **AppSecret**：开发使用的秘钥。

这些在后续开发中非常关键。

### 2. 服务器域名配置

（本节暂略，可在后续配置中根据接口部署情况进行设置）

## 关联设置

可以在小程序后台将其与公众号或微信开放平台账号绑定。

绑定的好处包括：

- 公众号菜单可跳转到小程序；
- 小程序内可跳转公众号；
- 获取 **UnionID**（需用户关注公众号并绑定开放平台）。

⚠️ 注意：如果用户仅使用小程序而没有关注公众号，是无法获取 UnionID 的。

## 微信开发者工具

微信官方提供了开发工具 —— **微信 Web 开发者工具**，下载安装即可开始项目开发。

## 项目结构

微信小程序项目结构由多个配置和入口文件组成，以下是核心文件说明：

### 1. `project.config.json`

记录项目的配置参数，例如：

```json
{
  "appid": "your-app-id",
  "projectname": "demo-app",
  ...
}
```

开发工具根据 `appid` 判断项目归属，项目上传时依赖此配置。

### app.json

小程序的全局配置文件，包括页面路径、窗口样式、底部 tabBar 等信息。

```json
{
  "pages": ["pages/index/index", "pages/logs/logs"],
  "tabBar": {
    "list": [
      {
        "pagePath": "pages/index/index",
        "text": "首页"
      }
    ]
  }
}
```

- 所有页面都必须在 `pages` 数组中声明；

- 页面的 `.wxml`、`.js`、`.json`、`.wxss` 文件将自动关联。

### app.js

全局逻辑入口文件，其中可定义全局变量：

```js
App({
  globalData: {
    baseUrl: 'https://api.example.com',
    userInfo: null,
  },
})
```

在页面中使用：

```js
const app = getApp()
console.log(app.globalData.baseUrl)
```

以上是开发微信小程序的基本步骤与结构介绍，建议新手从官方文档入门，并动手实践每个模块的配置与开发。
