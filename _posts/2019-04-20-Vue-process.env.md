---
layout:     post
title:      Vue-process.env
subtitle:   Vue-process.env
date:       2019-04-20
author:     z9961
header-img: https://bing.ioliu.cn/v1/rand?w=1280&h=320
catalog: true
tags: Vue

---
Vue-cli3会对process.env做限制

想要添加自定义变量需要创建.env文件

```
VUE_APP_LOGINTYPE = 'vue'
```

变量需要以VUE_APP_开头



--------

.env				# 在所有的环境中被载入
.env.modename	  # 只在指定的模式中被载入

指定模式需要在package.json 中添加 --mode modename

例如 "serve": "vue-cli-service serve  --mode modename",