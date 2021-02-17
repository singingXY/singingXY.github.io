---
title: 使用ssh连接Git仓库(Github\GitLab\CODING\码云等)
date: 2019-12-23 08:22:16
categories:
  - 笔记
tags:
  - ssh
  - Git
  - Github
---

总的说主要操作是在本地生成 ssh Key，然后把 ssh Key 添加到 Github/GitLab 的账户上，完成连接。

<!--more-->

### 检查现有 ssh 密钥

打开 Git Bash 终端。

输入 `ls -al ~/.ssh` 查看是否已经存在 ssh 密钥：

```bash
\$ ls -al ~/.ssh
```

如果提示不存在此目录那么就来生成新 ssh 密钥

如果已经存在 ssh 密匙文件应该是长下面这个样子：

> id_rsa.pub
> id_ecdsa.pub
> id_ed25519.pub
> 就可以跳过创建 SSH 密钥这一步啦。

### 生成新 ssh 密钥

打开 Git Bash 终端输入`ssh-keygen -t rsa -C <your_email@example.com>`( 你的邮箱)

```bash
ssh-keygen -t rsa -b 4096 -C <your_email@example.com>
# Creates a new ssh key, using the provided email as a label
# Generating public/private rsa key pair.
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]  //enter使用默认地址， 如果需要使用多个Git仓库可以重命名
Enter passphrase (empty for no passphrase):   //这里点击 Enter 键即可，也可以填写密码，填写密码后每次使用 ssh 方式推送代码时都会要求输入密码
```

成功之后显示如下信息：

```bash
Your identification has been saved in /Users/you/.ssh/id_rsa.
# Your public key has been saved in /Users/you/.ssh/id_rsa.pub.
# The key fingerprint is:
# 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
```

### 给账户添加 ssh

到路径`/Users/用户名/.ssh/`下，使用编辑器打开刚刚创建的`id_rsa.pub`文件，复制下整段内容。
打开 Github\GitLab\CODING\码云 的账户设置，找到设置 ssh 的选项，点击新增 ssh 密钥。由于各网站的设置位置都有不同，就不一一详说了。
把刚刚复制的 Key 粘贴进去，可以起一个方便你分辨的名字。
然后会提示你输入密码，输入完毕后 ssh Key 就添加成功了。

### 测试 ssh 连接

在 Git Bash 里使用命令`ssh -T git@github.com`测试 ssh 连接，如果是 GitLab 则是`ssh -T git@gitlab.com`，其他账户同理。

```bash
ssh -T git@github.com
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
> Are you sure you want to continue connecting (yes/no)? //输入 yes
> Hi username! You've successfully authenticated, but GitHub does not
> provide shell access.
```

收到欢迎消息说明连接成功。

### 使用 VS Code 尝试同步

把要用的仓库 clone 到本地，放进 vscode 工作区，修改一些内容，可以看到改动的内容被识别出来了。
push 一下试试，输入用户名密码，成功。
如果密码输错了可以修改凭据

### 如何修改本地提交时记录的密码

控制面板-用户账户-管理 Windows 凭据-找到要修改的那一个，点编辑就可以修改密码了。
