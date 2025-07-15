---
title: '[技术干货] 一次性带你了解讲完markdown语法🎈✨'
author: Tanger
date: 2021-12-10 10:38:50
tags:
  - markdown
  - 碎碎念
categories:
  - 开发日志
  - markdown
---

# Hello~ 我是不干人事的 Tanger 👋

首先欢迎你阅读我的文章 😀，也很期待各位大佬的指正。如果对这篇文章感兴趣的话，不妨收藏一下 ⭐ 本页面。如果有什么想对作者说的话可以通过以下两种方式联系我：

- **简单粗暴法**：直接在下方的评论区留言 🎈（可能回复稍慢）
- **花里胡哨法**：发送邮件至 `1907065810@qq.com`，我会尽快回复你 ✨

---

## 关于这篇文章 😂

这篇文章其实没什么卵用，主要是因为我总记不住 Markdown 的语法，每次写博客都要上网查，属实是菜得真实，于是干脆写一篇自己的语法总结，图个清爽！

---

## 目录 📚

- 😁 [Markdown 精讲之文章头部](#markdown-精讲之文章头部-1)
- 😀 [Markdown 精讲之标题](#markdown-精讲之标题-2)
- 😂 [Markdown 精讲之段落](#markdown-精讲之段落-3)
- 🤣 [Markdown 精讲之区块引用](#markdown-精讲之区块引用-4)
- 😃 [Markdown 精讲之代码区块](#markdown-精讲之代码区块-5)
- 😄 [Markdown 精讲之强调](#markdown-精讲之强调-6)
- 😅 [Markdown 精讲之列表](#markdown-精讲之列表-7)
- 😆 [Markdown 精讲之分割线](#markdown-精讲之分割线-8)
- 😋 [Markdown 精讲之链接](#markdown-精讲之链接-9)
- 😎 [Markdown 精讲之图片](#markdown-精讲之图片-10)
- 🙂 [Markdown 精讲之反斜杠 \](#markdown-精讲之反斜杠-11)
- 🤔 [Markdown 精讲之符号 `](#markdown-精讲之符号-12)
- 😳 [Markdown 精进之内嵌 HTML 标签](#markdown-精进之内嵌-html-标签-13)
- 🥰 [Markdown 扩展语法：表格、任务列表、脚注等](#markdown-扩展语法)
- 😘 [最后的最后：鸣谢](#最后的最后一些话以及鸣谢)

---

## Markdown 精讲之文章头部 #1

使用 Hexo 写博客时，每篇文章的头部可以配置如下信息：

```yaml
---
layout: Tanger的思源地
title: new article
date: 2021-05-15 13:13:29
author: Tanger
cover: true
top: true
toc: true
img: /medias/featureimages/1.jpg
coverImg: /medias/featureimages/0.jpg
mathjax: true
summary: 自定义文章摘要内容
categories: 博客
tags:
  - Markdown
  - 教程
---
```

这些信息的生成逻辑与 Hexo 根目录配置有关，比如你在 `_config.yml` 中写了：

```yaml
new_post_name: :title.md
default_layout: Tanger的思源地
```

然后你执行：

```bash
hexo new "new article"
```

就会自动创建上述头部内容。

---

## Markdown 精讲之标题 #2

Markdown 支持六级标题，用 `#` 表示，越多级别越小：

```markdown
# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题
```

🚫 不建议文章中频繁使用一级标题，容易导致目录混乱，推荐从二级标题开始写正文内容。

---

## Markdown 精讲之段落 #3

段落的创建非常简单，只需**空一行回车即可**。

```markdown
我是一个段落

我是另一个段落
```

---

## Markdown 精讲之区块引用 #4

区块引用使用 `>`，可以嵌套：

```markdown
> 前端学习
>
> > 前端三大件
> >
> > > HTML
> > > CSS
> > > JavaScript
```

---

## Markdown 精讲之代码区块 #5

代码可以用 \`\`\` 包裹起来，指定语言会高亮：

```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
    cout << "Hello World!" << endl;
    return 0;
}
```

---

## Markdown 精讲之强调 #6

| Markdown 语法            | 效果       |
| ------------------------ | ---------- |
| `**加粗**` 或 `__加粗__` | **加粗**   |
| `*斜体*` 或 `_斜体_`     | _斜体_     |
| `~~删除线~~`             | ~~删除线~~ |

---

## Markdown 精讲之列表 #7

无序列表使用 `*` `-` 或 `+`：

```markdown
- 项目 A
- 项目 B
- 项目 C
```

有序列表：

```markdown
1. 第一项
2. 第二项
3. 第三项
```

---

## Markdown 精讲之分割线 #8

使用三个及以上 `*` `-` `_` 创建分割线：

```markdown
---
---

---
```

---

## Markdown 精讲之链接 #9

行内式：

```markdown
[Tanger 的 GitHub 主页](https://github.com/redhat123456)
```

参考式：

```markdown
[Tanger 的 GitHub 主页 1][1]

[1]: https://github.com/redhat123456 'Markdown'
```

---

## Markdown 精讲之图片 #10

```markdown
![图片描述](https://example.com/image.png)
```

⚠ 图片地址需为公网链接。

---

## Markdown 精讲之反斜杠 \ #11

反斜杠 `\` 可用于转义 Markdown 中的特殊符号：

```markdown
\*不会加粗\*
```

输出：\*不会加粗\*

---

## Markdown 精讲之符号 ` #12

用于行内代码片段：

```markdown
`Ctrl + C`
```

输出：`Ctrl + C`

---

## Markdown 精进之内嵌 HTML 标签 #13

可以直接嵌入 HTML 标签，比如让图片居中：

```html
<p align="center">
  <img src="https://example.com/image.jpg" width="300" />
</p>
```

---

## Markdown 扩展语法

### 表格

```markdown
| 姓名 | 年龄 | 性别 |
| ---- | ---- | ---- |
| 张三 | 18   | 男   |
| 李四 | 20   | 女   |
```

### 任务列表

```markdown
- [x] 写完基础语法
- [ ] 写完扩展语法
- [ ] 发布文章
```

### 脚注（部分平台支持）

```markdown
Markdown[^1] 是一种轻量级标记语言。

[^1]: Created by John Gruber
```

---

## 最后的最后：一些话以及鸣谢 😘

谁在用 Markdown？

- GitHub
- 简书
- Stack Overflow
- Apollo
- Reddit
- ……

推荐工具：

- 在线编辑器：StackEdit、Dillinger.io
- Chrome 插件：markdown-here
- Windows：MarkdownPad
- macOS：Mou
- Linux：ReText

> ⚠ 不同平台支持的 Markdown 语法略有不同，具体可查看你使用的平台说明。

---

### 鸣谢

> 感谢 [younghz/Markdown](https://github.com/younghz/Markdown) 项目，让我有机会参考并完成这篇文章！🎉🎉🎉
