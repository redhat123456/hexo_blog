---
title: '[技术干货] 如何将 Hexo 迁到一台新电脑上'
author: Tanger
date: 2020-08-25 09:49:21
tags:
  - 技术干货
  - 碎碎念
categories:
  - 技术干货
  - hexo
---

# 如何将 Hexo 迁到一台新电脑上

网上的很多教程都又长又繁琐，这里我总结了一种非常简单直接的方法，几步就能搞定！

---

## 步骤一：在新电脑上安装依赖

在新电脑上安装好以下两个工具：

- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)

建议安装最新版。

---

## 步骤二：复制原电脑的 Hexo 文件

1. 找到你在原电脑上的 Hexo 博客文件夹（就是有 `themes`、`source`、`_config.yml` 那个根目录）。
2. 把整个文件夹压缩（.zip 或 .rar）。
3. 拷贝到新电脑并解压。

---

## 步骤三：安装依赖包

在解压后的 Hexo 博客根目录，**右键选择 Git Bash Here**，然后执行：

```bash
npm install
```

等待安装完成即可。

如果文件夹里有 `.deploy_git` 或 `.git` 等部署文件夹，也可以选择先删除重新生成。

---

## 步骤四：配置 Git SSH 密钥（部署到 GitHub Pages 必须）

1. 在博客根目录 **右键 → Git Bash Here**，执行：

```bash
ssh-keygen -t rsa -C "your-email@example.com"
```

将 `"your-email@example.com"` 替换为你自己的邮箱。

2. 连续三次回车，密钥会默认保存在本地的 `~/.ssh` 文件夹中。

3. 输入以下命令将公钥复制到剪贴板：

```bash
clip < ~/.ssh/id_rsa.pub
```

4. 登录 [GitHub](https://github.com) → 点击右上角头像 → `Settings` → `Deploy keys` → `Add deploy key`：

- Title: 随便起一个名字，如 `MyNewLaptop`
- Key: 粘贴刚才复制的公钥内容（Ctrl+V）

然后点击 **Add key** 即可完成绑定！

---

## 更新提示（小 Bug）

我发现迁移后使用 `hexo deploy` 上传博客时，如果你直接用原电脑部署过的 `.deploy_git` 文件夹，可能会导致：

- 原来部署时的内容会直接覆盖，而不是更新。

为避免该问题，建议迁移后删除 `.deploy_git` 文件夹，重新执行一次：

```bash
hexo clean
hexo g
hexo d
```

---

## 完成！

现在你已经可以在新电脑上愉快地使用 Hexo 继续写博客了 🎉

---

📌 **总结一句话版本：**  
配好 Node + Git → 拷贝博客目录 → `npm install` → 配置 Git SSH → OK！
