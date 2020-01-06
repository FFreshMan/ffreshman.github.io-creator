---
title: "how to blog"
date: 2019-12-05T14:41:43+08:00
draft: false
---

# 如何用 hugo 搭建自己的个人博客

<!--more-->

## 1.下载[Hugo](https://github.com/gohugoio/hugo/releases)

    下载windows64位版本的压缩包，解压到一个文件夹（最好全英文），接着把安装路劲添加到path环境变量中，试着在控制台输入查看版本

```javascript
    hugo version
```

## 2.查看[Hugo 官网](https://gohugo.io/getting-started/quick-start/)搭建博客

1. 在你要创建的目录下输入

```javascript
hugo new site quickstart(取一个你喜欢的名字比如ffreshman.github.io-creator)
```

2. cd 进入你创建好的目录中运行以下代码

```javascript
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

这里的 ananke 是你的主题，后期可以选择跟换合适的主题

3. 接下来创建一个 markdown 文件，来写你文章的主体部分

```javascript
hugo new posts/你需要的博客标题.md
```

关于怎么写[markdown](https://www.mdeditor.com/)

4. 通过 hugo-sever 预览你的博客

```javascript
hugo server -D
```

这里你的 draft 状态保持为 true

![sever](/images/severs.png)

5. 接着创建一个准备上传到 github 的页面 public

```javascript
hugo - D;
```

然后把这个 public 上传到 github 仓库就可以查看你的博客了
