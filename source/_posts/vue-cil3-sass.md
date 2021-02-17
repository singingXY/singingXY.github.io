---
title: Vue CLI 3 自动化导入，配置sass全局变量
date: 2020-03-25 13:30:17
categories:
  - 小问题
tags:
  - vue-cil3
  - sass
---

使用 sass\less\Stylus 等预处理器时要定义一些全局变量、mixin，组件内使用是需要 import 进去的，每个文件都 import 一次很麻烦，所以需要使用自动化导入来帮我们处理。

<!-- more -->

在[官方文档关于自动化导入的介绍](https://cli.vuejs.org/zh/guide/css.html#%E8%87%AA%E5%8A%A8%E5%8C%96%E5%AF%BC%E5%85%A5)中，看到可以使用`style-resources-loader`，支持`css, sass, scss, less, stylus`。

也可以使用`vue-cli-plugin-style-resources-loader`插件的方式来安装。

运行`vue add style-resources-loader`后选择一个预处理器，这里我选 scss，然后它帮我在根目录生成了`vue.config.js`文件，里面有这样一段内容

```JavaScript
module.exports = {
  pluginOptions: {
    'style-resources-loader': {
      preProcessor: 'scss',
      patterns: []
    }
  }
}
```

然后在 patterns 中填入路径

```JavaScript
const path = require('path')

module.exports = {
  pluginOptions: {
    'style-resources-loader': {
      preProcessor: 'scss',
      patterns: [
        path.resolve(__dirname, './src/assets/css/_themes.scss'),
      ]
    }
  }
}
```

重新启动`npm run serve`，已经生效了。
