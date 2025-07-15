---
title: '[技术干货]如何将自建的网页上传至网上'
author: Tanger
date: 2020-11-23 09:52:00
tags:
  - 技术干货
  - 碎碎念
  - github-page
categories:
  - 技术干货
  - Web前端
---

# 如何将自建的网页上传至网上（划 💧）

网页在本地做好后，**如何上传到互联网上**？这是许多前端新手常遇到的问题。虽然听起来有点基础，但咱还是要把这个过程记下来，加深印象！

---

## 🚀 使用 GitHub Pages 部署网页

大家都知道 GitHub 是面向开源与私有项目的代码托管平台。**除了代码，它还支持网页部署！**我们可以用它把 HTML/CSS/JS 网页直接挂到网上。

---

## 📝 步骤一：新建一个 GitHub 仓库

1. 打开 [https://github.com](https://github.com)
2. 登录你的账号
3. 点击左上角 `+` → **New repository**

创建仓库时注意：

- 仓库名可以是你喜欢的名称（例如 `my-web-demo`）
- 可以选择 `Public` 或 `Private`
- 可以勾选 `Initialize with a README`（推荐）

---

## 🧩 步骤二：上传你的网页文件

有两种方式可以上传本地网页：

### ✅ 方法一：通过网页界面上传（适合新手）

1. 进入你刚创建的仓库页面
2. 点击 `Add file` → `Upload files`
3. 拖动你本地的网页文件（例如 `index.html`, `style.css`, `images/` 等）到上传区域
4. 点击下方绿色按钮 `Commit changes` 完成上传

### ✅ 方法二：通过 Git 上传（适合熟练用户）

```bash
# 初始化本地 Git 并上传
git init
git remote add origin https://github.com/你的用户名/你的仓库名.git
git add .
git commit -m "upload my website"
git push -u origin master
```

---

## 🔧 步骤三：启用 GitHub Pages

1. 打开你的仓库主页
2. 点击 `Settings` → 找到左侧菜单的 **Pages**
3. 在 `Source` 一栏中选择：

```
Deploy from a branch:
Branch: main（或 master）
Folder: / (root)
```

4. 保存设置，稍等片刻，你就会在上方看到一个自动生成的网址，比如：

```
https://yourusername.github.io/your-repo-name/
```

点击它就能访问你上传的网页啦！🎉🎉🎉

---

## 🌟 小贴士

- **主页文件名必须为 `index.html`**，否则打开页面时不会自动显示。
- GitHub Pages 支持静态资源（图片、CSS、JS），但不支持 PHP、Node 等后端语言。
- 每次修改网页文件后，重新 `push` 或上传即可自动更新上线内容。

---

## ✅ 总结流程

1. 注册 GitHub 账号并创建仓库
2. 上传你的网页文件
3. 在 Settings 中启用 GitHub Pages 功能
4. 等待几秒即可通过链接访问你的网站！

---

> 💬 如果你后续想绑定自己的域名、部署到 Vercel / Netlify / Cloudflare Pages，我也可以继续出教程哦！
