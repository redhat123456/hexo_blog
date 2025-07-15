---
title: '[Tanger的开发者日志] 开发小程序日志（一）'
author: Tanger
date: 2020-08-20 09:44:47
tags:
  - 开发日志
  - 微信小程序
categories:
  - 开发日志
  - 微信小程序
---

# 开发小程序日志（一）

## 微信小程序介绍

小程序，顾名思义，就是一种**“用完即走”**的轻量级应用形态。

现代人手机里的应用很多，但据统计有 **70% 的应用几乎不用**，真正频繁使用的只占 30%。这些长时间不用的 App 却常年占用内存、流量和资源。基于此背景，**微信小程序**应运而生 —— 不用下载，随用随开，体验轻便。

---

## 小程序的目录结构

通常，一个页面对应一个文件夹，包含以下 **四个必要文件**：

- `.wxml` —— 页面结构（类似 HTML）
- `.wxss` —— 样式文件（类似 CSS）
- `.js` —— 页面逻辑
- `.json` —— 页面配置

这四个文件缺一不可，后续可通过跳转链接在页面间切换。

⚠️ 注意：**`wxss` ≈ `css`**，只是为了小程序定制做了扩展。

---

## 基础布局容器：`<view>`

小程序的语法风格和 Vue 非常接近。

### hover 效果

如果你想让一个 `view` 像按钮一样，**按下时改变样式**，可以这样写：

```html
<view class="box" hover-class="boxHover">
  wdnmd
  <view class="item" hover-class="boxHover"></view>
  wdnmd
</view>
```

接着，在 `.wxss` 文件中添加样式定义：

```css
.box {
  width: 100px;
  height: 100px;
  background-color: blue;
}
.box:hover {
  background-color: cornsilk;
}
.item {
  width: 30px;
  height: 50px;
  background-color: rgb(209, 209, 209);
}
.item:hover {
  background-color: green;
}
```

这样，在页面中点击相应元素时，会改变背景颜色。

---

## 弹性布局 `flex-direction`

设置主轴方向：

- `flex-direction: row` → **横向布局**
- `flex-direction: column` → **纵向布局**

可以在容器中通过 `flex-direction` 设置子元素排列方式：

```css
.container {
  display: flex;
  flex-direction: row; /* 横向 */
}
```

---

## 幻灯片容器 `swiper`

小程序中的 `<swiper>` 元素类似于网页中的幻灯片轮播图。

常见属性说明：

- `interval`：幻灯片切换间隔（单位：ms）
- `previous-margin`：设置前边距，优化视觉体验

示例用法可参考官方文档或自行添加演示效果。

---

这是第一篇小程序开发日志，后续我将继续记录和分享开发过程中的经验与问题，欢迎留言讨论！
