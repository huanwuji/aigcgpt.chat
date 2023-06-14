# vue3升级到nuxt3全过程

再本网站构建时，前端使用vue3构建，后来被搜索引擎收录,从收录结果来看，只收录了首页，子页面并没有收录。
是由于vue动态建立网站不利于搜索引擎的收录，根据[官方推荐](https://vuejs.org/guide/scaling-up/ssr.html)尝试使用SSR技术。
官方推荐的SSR尝试了一下没有成功。由于网站代码不多，后改为nuxt重新构建。
本人为专业后端，业余前端，在修改过程中踩了很多坑，且在搜索处理过程中没有找到特别好的文档指导，官方文档写的文档也不详细，所以把整个过程技术下来，以供参考。

官方文档参考: [https://nuxt.com.cn/](https://nuxt.com.cn/)

## 基础脚手架生成

参考文档: https://nuxt.com.cn/docs/getting-started/installation
直接使用官方的`npx nuxi init <project-name>`生成基础的框架

## 配置layout

网站内容将展示在slot中

```javascript
<template>
    <div>
        <AppHeader/>
        <slot/>
    </div>
</template>
<script setup lang="ts">
    import AppHeader from "~/components/AppHeader.vue";
</script>
```

## 路由

路由文档： [https://nuxt.com.cn/docs/getting-started/routing](https://nuxt.com.cn/docs/getting-started/routing)

page文档: [https://nuxt.com.cn/docs/guide/directory-structure/pages](https://nuxt.com.cn/docs/guide/directory-structure/pages)
vue的路由文件基本可以废弃，虽然官方说了还可以继续用vue路由的方法但是没有测试成功。

```
-| pages/
---| index.vue
---| users-[group]/
-----| [id].vue
```

动态路由就是按照这种有中括号的方式进行构建。vue中component目录中的文件大多都要移入pages内。

接着修改`router-link`为`NuxtLink`，nuxt不需要一堆参数，直接拼接path

```html

<router-link :to="{ name: 'categories', params: {uri: uri, page: 1 }}"
             改为
<NuxtLink :to="'/category/' + navs.slice(0,index+1).join('.') +'/1'">
```

## 放弃了vue的标准写法

如这种，虽然迁移过程中能运行，但是总有一些加载时机问题，
不想调试了，主要nuxt官方也没有示例文档支持这种写法，
且pinia也弃了，也如上原因，没有详细的官方示例不知道如何入手。

```javascript
//vue3
data: () => {

},
    setup()
{

}
,
methods: {

}
//nuxt 全部改为
<script setup>
```

`computed`这些还是可以用的，其它没有一一试了，不太能搞清楚它的服务商生成，客户端也能生成的原理。
所以老老实实的按官方有的文档来。

网络层的axios库也没有用，安装不上，查了文档也没找到原因，弃了。
直接使用了官方的`useFetch`且把文件放入了composables目录中。

## 百度统计

nuxt.config.js中配置plugins, 并把百度统计代码放入plugins/baidu.js文件中。

```javascript
    plugins: [
    {src: "@/plugins/baidu", mode: "client"}
]
```

## 首页配置

由于nuxt中没有首页index文件了，所以全部在nuxt.config.js中配置出来。比如title这些

## 部署

这个坑了最久的。
官方部署文档: [https://nuxt.com.cn/docs/getting-started/deployment](https://nuxt.com.cn/docs/getting-started/deployment)
使用了pm2配置ecosystem.config.js进行部署。

### 证书配置

由于机器小，不想加nginx增加依赖，所以想把证书放在nuxt中。
NITRO_PORT可以生效，但NITRO_SSL_CERT死活不生效。
后来看到生成后的代码，直接将process.env.NITRO_SSL_CERT放到了node的createServer中，
也就是配置的不是路径，而是证书的内容，这个在ecosystem.config.js中完全无法配置。菜鸟也没优雅的办法进行绕过。
还是老老实实又加了一层nginx，证书配置到nginx中。

### 前后端baseurl配置

这个感觉很重要，但是又没有明确的文档说建议该怎么做。
因为SSR技术，服务端和客户端都可以生成页面，且有可能混用，
所以类似axios现在是useFetch有可能从服务端发起请求这样本机的localhost就可以访问，
而前端又需要配置成网站域名，如果是同一个完全访问不了。这一步也卡了好久。

### 环境配置

后来看到有一个.env的配置，然后如下配置

```json
//package.json  
{
  "name": "nuxt-app",
  "private": true,
  "scripts": {
    "build": "nuxt build",
    "dev": "nuxt dev --dotenv .env.local",
```

```
.env.local, 直接根目录下建立该文件，我开始建了个.env，这是错的, 服务端配置了跨域用于本地调度
NUXT_API_BASE = http://localhost:8090
NUXT_PUBLIC_API_BASE = http://localhost:8090
```

这个在开发环境可以完善解决，但是后来部署到正式就不行，看了[官方.evn](https://nuxt.com.cn/docs/guide/directory-structure/env)
构建时不能有些用法，需要其它方式注入，然后我就配置到`ecosystem.config.js`中，生效环境也生效了。

且请求时加了如下代码，主要利用了private变量只能服务器能读到，public服务器和客户端都能读到的原理，
和useFetch有一个baseURL参数进行替换。
此方法还没有解决浏览器请求时的http和https的区分，目前是nginx配置了强制跳转https

```javascript
export const getRecently = (uri, limit, onResponse) =>
    useFetch('/api/portal/recent', wrapOpts({
        query: {uri, limit},
        onResponse({response}) {
            response._data = onResponse(response._data)
        }
    }))

function wrapOpts(opts) {
    const config = useRuntimeConfig();
    opts.baseURL = config.apiBase || config.public.apiBase;
    return opts;
}
```

至此基本完成整体迁移，网站可以运行了。
附几个主要配置文件的详细配置.

```javascript
//nuxt.config.ts
export default defineNuxtConfig({
    css: [
        "@/assets/styles.scss"
    ],
    app: {
        head: {
            title: '天一心启',
            charset: 'utf-8',
            meta: [{name: 'viewport', content: 'width=device-width, initial-scale=1'}]
        }
    },
    runtimeConfig: {
        apiBase: '',
        public: {
            apiBase: ''
        }
    },
    devtools: {enabled: true},
    plugins: [
        {src: "@/plugins/baidu", mode: "client"}
    ]
})
```

```javascript
//ecosystem.config.js
module.exports = {
    apps: [
        {
            name: 'aigc8080',
            exec_mode: 'fork',
            instances: '1',
            script: './.output/server/index.mjs',
            env: {
                NITRO_PORT: 3000,
                NUXT_API_BASE: "http://localhost:8090",
                NUXT_PUBLIC_API_BASE: "https://aigcgpt.chat"
            },
            "error_file": "./logs/error8080.log",//错误输出日志
            "out_file": "./logs/out8080.log",  //日志
        }
    ]
}
```

```json
{
  "name": "nuxt-app",
  "private": true,
  "scripts": {
    "build": "nuxt build",
    "dev": "nuxt dev --dotenv .env.local",
    "generate": "nuxt generate",
    "preview": "nuxt preview",
    "postinstall": "nuxt prepare"
  },
  "devDependencies": {
    "@nuxt/devtools": "latest",
    "@types/node": "^18",
    "nuxt": "^3.5.2",
    "sass": "^1.63.3"
  },
  "dependencies": {
    "@pinia/nuxt": "^0.4.11",
    "bootstrap": "^5.3.0"
  }
}
```