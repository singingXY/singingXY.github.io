---
title: 使用vue-cli构建项目 eslint报Expected linebreaks to be 'LF' but found 'CRLF'错误
date: 2019-12-07 10:47:53
categories:
  - 小问题
tags:
  - VS Code
  - vue-cli
  - eslint
---

使用 vue-cli 构建项目 eslint 报 Expected linebreaks to be 'LF' but found 'CRLF'错误。
解决方法：
进入`.eslintrc.js`文件，`rules`里添加`"linebreak-style": [0, "error", "windows"]`,如下

```json
rules: {
    "linebreak-style": [0, "error", "windows"]
  }
```
