---
title: hexo 克隆master分支
date: 2024-10-29 19:23:55
tags:
---

如果你想克隆GitHub仓库的 `master` 分支，可以使用以下步骤：

### 1. 克隆GitHub仓库
首先，使用 `git clone` 命令克隆整个仓库。默认情况下，`git clone` 会克隆默认分支（通常是 `main` 或 `master`）。

```bash
git clone git@github.com:luojiannx/luojiannx.github.io.git
```

### 2. 切换到 `master` 分支
进入克隆下来的项目目录：

```bash
cd luojiannx.github.io
```

然后，使用 `git checkout` 命令切换到 `master` 分支：

```bash
git checkout master
```

### 3. 更新 `master` 分支
如果你在原始电脑上更新了 `master` 分支并推送到GitHub，你可以使用以下命令获取最新的更新：

```bash
git pull origin master
```

### 4. 安装Hexo及其依赖
确保你已经安装了Node.js和Git。然后，进入项目目录并安装Hexo及其依赖：

```bash
npm install hexo-cli -g
npm install
```

### 5. 生成和预览博客
在新的电脑上，你可以使用以下命令生成和预览博客：

```bash
hexo generate
hexo server
```

这会在本地启动一个服务器，你可以在浏览器中访问 `http://localhost:4000` 预览你的博客。

### 6. 部署博客（可选）
如果你需要在新电脑上部署博客到GitHub Pages，可以使用以下命令：

```bash
hexo deploy
```

### 总结
通过以上步骤，你可以在其他电脑上克隆并切换到 `master` 分支，获取最新的Hexo博客目录更新，并继续开发和部署你的博客。确保每次更新后都推送到GitHub，这样其他电脑上都可以获取到最新的内容。
