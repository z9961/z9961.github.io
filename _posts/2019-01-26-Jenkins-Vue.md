---
layout:     post
title:      Jenkins-Vue
subtitle:   Jenkins-Vue
date:       2019-01-26
author:     z9961
header-img: https://bing.ioliu.cn/v1?d=2&w=1280&h=320
catalog: true
tags: Jenkins
---

Jenkins持续集成部署Vue项目

jenkins+git+Webhooks

环境：windows server 2008



#### 步骤

1.打开系统管理-全局工具配置，添加node.js的配置

2.打开系统管理-插件管理-Available，安装[NodeJS Plugin](http://wiki.jenkins-ci.org/display/JENKINS/NodeJS+Plugin)

3.创建一个自由风格的job

4.![mark](http://img.aloli.cn/github/20190126/meFoegrxauUb.png)

![mark](http://img.aloli.cn/github/20190126/EzoPSIW9eFyX.png)

类似于之前的	[Jenkins-Springboot](http://github.aloli.cn/2019/01/22/Springboot/)

```CMD
set BUILD_ID=dontKillMe
start npm run serve
exit 0
```

这里的start是异步执行，不然构建超时

---

如果出现访问网站提示

```
Invalid Host header
```

在vue目录下创建vue.config.js

```vue
module.exports = {
    devServer: {
        disableHostCheck: true,
    }
}
```

