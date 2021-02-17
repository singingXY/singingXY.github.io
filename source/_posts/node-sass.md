---
title: 安装 node-sass 失败的解决方法
date: 2020-03-25 13:04:06
categories:
  - 小问题
tags:
  - sass
---

如果已经安装失败了，先卸载

```bash
npm uninstall node-sass
```

<!-- more -->

设置变量 sass_binary_site，指向淘宝镜像地址。示例：

```
npm i node-sass --sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
```

或者设置全局镜像源：

```
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
```

之后再涉及到 node-sass 的安装时就会从淘宝镜像下载。

按理说直接用 cnpm 来安装是可以的，但是不知道怎么的我用 cnpm 命令没有反应。
