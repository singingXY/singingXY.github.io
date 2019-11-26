---
title: 来用hexo和GitHub Pages做个个人博客吧
date: 2019-11-25 15:12:38
categories:
  - 小问题
tags:
  - hexo
  - blog
---

#### 为什么选 hexo

GitHub Pages 的配置页面里推荐了 Jekyll，本来打算就从 Jekyll 开始摸索的，去主页看了文档，需要 Ruby 和 RubyGems ，光是下载 Ruby 这一步就把我卡住了，下载速度为 0。行吧。
只能把目光转向了 hexo，一看环境只需要 node.js，用 npm 直接安装就可以，太方便了。

#### 开始安装

先把 hexo 装上

```bash
npm install -g hexo-cli
```

然后用 init 初始化

```bash
 hexo init <folder>
 cd <folder>
 npm install
```

别看就这么短短 3 句话，也有的折腾的。
init 这一步由于要下载一个默认的主题包，文件还不小，下了一会儿速度就变 0 了，继续等，结果直接超时了，报了一堆错，基本就是说下载失败什么的。只能重新开始又下了一遍，耐心等待，这回终于成功了。

`_config.yml`是配置文件，自定义的属性就在里面设置。

#### 部署到 GitHub Pages

到`_config.yml`文件里拉到最下面找到 deploy 配置：

```yaml
deploy:
  type: git
  repo: https://github.com/singingXY/singingXY.github.io.git
  branch: master
```

填上自己的仓库地址和分支名就可以使用了。

#### 发出第一篇文章

下面是几个常用的命令，步骤是：新建文章-生成-本地预览-部署到线上

```bash
hexo n "xxx" == hexo new  "xxx"   #新建文章
hexo g == hexo generate           #生成
hexo s == hexo server             #启动服务预览
hexo d == hexo deploy             #部署
```

除了上面的写法，我们在自动生成的`package.json`文件里可以看到如下配置，

```json
  "scripts": {
    "build": "hexo generate",
    "clean": "hexo clean",
    "deploy": "hexo deploy",
    "server": "hexo server"
  }
```

习惯 npm 的也可以用`npm run`的形式写。

#### 使用另一个分支保存源码

由于`master`分支里保存的是我们生成出来的文件，而源码是存在本地的，为了当我换一台电脑也能继续更新，我需要把源码存到 github 里，所以新建了一个`hexo`分支，把源码存在里面。这样当我源码有改动时也能同步更新了。

#### 开始写文章啦

当我们执行`hexo new`的命令后，会在 source 文件夹下看到我们新建的`.md`文件，顶端以`---`分隔的区域，叫做 Front-matter，我们可以在里面配置这篇文章的信息。
如果要给文章添加 tags 和分类，可以如下设置

```yaml
categories:
  - Diary
tags:
  - PS3
  - Games
```

Front-matter 的下面就可以开始用 markdown 的语法写文章了。

#### 使用本地图片插件 hexo-asset-image

先将`_config.yml`的`post_asset_folder`改为 true，然后运行以下命令：

```bash
npm install https://github.com/CodeFalling/hexo-asset-image --save
```

这样可以解决在使用本地图片时，本地图片和线上图片路径不一致的问题，本地预览时也可以显示出图片。
而且不用把分散的文章里的图片都放在一个总的 source 文件夹内，而是按照文章目录来放置，简单明了。
