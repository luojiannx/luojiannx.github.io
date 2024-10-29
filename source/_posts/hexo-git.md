---
title: 如何让hexo在多台电脑上同时使用
date: $date
tags: hexo github git
---

要在其他电脑上获取最新的Hexo博客目录更新，你需要在新的电脑上克隆你的GitHub仓库，并安装必要的依赖。以下是详细的步骤：

### 1. 安装Node.js和Git
首先，确保新电脑上已经安装了Node.js和Git。你可以从以下链接下载并安装：

- Node.js: [https://nodejs.org/](https://nodejs.org/)
- Git: [https://git-scm.com/](https://git-scm.com/)

### 2. 克隆GitHub仓库
在新电脑上打开终端或命令提示符，导航到你希望存放博客项目的目录，然后使用以下命令克隆你的GitHub仓库：

```bash
git clone git@github.com:luojiannx/luojiannx.github.io.git
```

这会将你的Hexo博客项目克隆到当前目录下。

### 3. 安装Hexo
进入克隆下来的项目目录：

```bash
cd luojiannx.github.io
```

然后，安装Hexo及其依赖：

```bash
npm install hexo-cli -g
npm install
```

### 4. 安装Hexo插件
如果你的Hexo项目使用了任何插件，你需要确保这些插件也安装在新电脑上。通常，这些插件会在 `package.json` 文件中列出。你可以使用以下命令安装所有依赖：

```bash
npm install
```

### 5. 更新博客内容
如果你在原始电脑上更新了博客内容并推送到GitHub，你可以使用以下命令获取最新的更新：

```bash
git pull origin main
```

如果你的GitHub仓库使用的是 `master` 分支，请将 `main` 改为 `master`。

### 6. 生成和预览博客
在新的电脑上，你可以使用以下命令生成和预览博客：

```bash
hexo generate
hexo server
```

这会在本地启动一个服务器，你可以在浏览器中访问 `http://localhost:4000` 预览你的博客。

### 7. 部署博客（可选）
如果你需要在新电脑上部署博客到GitHub Pages，可以使用以下命令：

```bash
hexo deploy
```

### 总结
通过以上步骤，你可以在其他电脑上获取最新的Hexo博客目录更新，并继续开发和部署你的博客。确保每次更新后都推送到GitHub，这样其他电脑上都可以获取到最新的内容。
