---
layout:     post
title:      Electron-Vue
subtitle:   Electron-Vue
date:       2019-04-18
author:     z9961
header-img: https://bing.ioliu.cn/v1/rand?w=1280&h=320
catalog: true
tags: Vue
---


官方文档：https://simulatedgreg.gitbooks.io/electron-vue/content/cn/

### 1.svg图标

移植到electron需要把vue.config.js中的

```
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
```

改为在webpack.renderer.config.js文件的rendererConfig:module:rules中添加：

```
{
                test: /\.svg$/,
                loader: 'svg-sprite-loader',
                options: {
                    symbolId: 'icon-[name]'
                },
                include: [path.join(__dirname, '../src/renderer/components/icon/svg')]
}
```

在

```
test: /\.(png|jpe?g|gif|svg)(\?.*)?$/
```

中添加

```
exclude: [path.join(__dirname, '../src/renderer/components/icon/svg')],
```



### 2.cdn

如果原项目引入了cdn而现在不需要cdn了要把main.js中删除的

```
Vue.use(Vuex);
Vue.use(Router)；
```

添加回来



### 3.icon

build文件夹中的icons要保证存在



### 4.莫名其妙的问题

莫名其妙报

```
Invalid or unexpected token
```

```
Uncaught SyntaxError: Unexpected token <
```

```
at eval (external "vue-schart"?c2f1:1)
```

```
Failed to resolve async component default:
```

删了项目重新从git上clone一遍就没了，应该是有包在下载的时候出错了

