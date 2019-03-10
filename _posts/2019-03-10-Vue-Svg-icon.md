---
layout:     post
title:      Vue-Svg-icon
subtitle:   Vue-Svg-icon
date:       2019-03-10
author:     z9961
header-img: https://bing.ioliu.cn/v1?d=2&w=1280&h=320
catalog: true
tags: Vue
---





在vue.config中配置

```
const path = require('path');

function resolve(dir) {
    return path.join(__dirname, dir)
}

module.exports = {
     chainWebpack: config => {
        config.module
            .rule('svg')
            .uses.clear();
        config.module
            .rule('svg1')
            .test(/\.svg$/)
            .use('svg-sprite')
            .loader('svg-sprite-loader')
            .options({
                symbolId: 'icon-[name]'
            })
            .end()
            .include
            .add(resolve('src/components/icon/svg'))
            .end()
    }
};

```



遇到的坑:

在main.js中

```
import './components/icon'
```

这里如果是

```
import './components/icon/index.js'
```

会出现图标不显示的问题



参考:

https://www.jianshu.com/p/1150876dfa04