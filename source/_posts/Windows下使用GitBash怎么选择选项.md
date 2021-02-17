---
title: Windows下使用GitBash运行vue/cli怎么选择选项
date: 2021-02-17 09:23:28
categories:
  - 小问题
tags:
  - vue/cli
  - GitBash
---

使用 Vue CLI 时，我们用`vue create hello-world`来创建一个新的 vue 项目。
但是如果在 Windows 下使用 Git Bash 来运行这个命令，是不能进行选择的。
这是文档上的警告，同时也是解决方法：

> 警告
> 如果你在 Windows 上通过 minTTY 使用 Git Bash，交互提示符并不工作。
> 你必须通过` winpty vue.cmd create hello-world` 启动这个命令。
> 不过，如果你仍想使用 `vue create hello-world`，则可以通过在 ~/.bashrc 文件中添加以下行来为命令添加别名。 alias vue='winpty vue.cmd' 你需要重新启动 Git Bash 终端会话以使更新后的 > bashrc 文件生效。

用 vue/cli 新建项目时需要注意一下。
