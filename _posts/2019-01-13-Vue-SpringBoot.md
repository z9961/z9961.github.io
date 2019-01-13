---
layout:     post
title:      Vue-SpringBoot
subtitle:   Vue-SpringBoot
date:       2019-01-13
author:     z9961
header-img: https://bing.ioliu.cn/v1?d=2&w=1280&h=320
catalog: true
tags: Vue
---





### 前后端分离后数据通信的问题

1.在Vue中使用axios来post和get

​	*npm* *install* --*save* axios

​	然后在main.js中添加

```vue
import axios from 'axios';
```

```vue
Vue.prototype.$axios = axios;
```

​	在new Vue(){

​	    }

​	中添加

```vue
	axios,
```

2.在要使用请求的vue中添加methods

```
  testaxios() {
                this.$axios
                    .get('http://192.168.1.231:8888/users/getall')
                    .then(response => (this.info = response))
            }
```

​	这里的info是template中的{{info}}

3.跨域问题

​	前端地址为localhost:8080

​	后端地址为localhost:8888

​	浏览器默认禁止跨域请求，有多种解决方式

​	

​	对于Spring Boot项目

​	新建一个类即可

```java
@Configuration
public class CORSConf {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")//匹配所有的请求
                        .allowedHeaders("*")    //请求头
                        .allowedMethods("*")    //post,get
                        .allowedOrigins("*")    //允许所有来源
                        .allowCredentials(true); //携带cookie
            }
        };
    }
}


```





