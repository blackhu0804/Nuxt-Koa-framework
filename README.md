# nuxt-learn

> Nuxt.js project

## Build Setup

``` bash
# install dependencies
$ npm install # Or yarn install*[see note below]

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm start

# generate static project
$ npm run generate
```

*Note: Due to a bug in yarn's engine version detection code if you are
using a prerelease version of Node (i.e. v7.6.0-rc.1) you will need to either:
  1. Use `npm install`
  2. Run `yarn` with a standard release of Node and then switch back

For detailed explanation on how things work, checkout the [Nuxt.js docs](https://github.com/nuxt/nuxt.js).

## 使用Vue-cli 搭建

参考链接：https://github.com/nuxt-community/koa-template

## npm run dev报错解决方法如下：

`npm run dev` 报错

- no babel-loader(node.js itself does not support es6 import)
- outdated dependencies 过时的依赖

- 解决办法：

> install babel-loader, upgrade eslint-loader

```bash
yarn remove eslint-loader
yarn add -D eslint-loader babel-loader
```
- edit backpack.config.js

```js
module.exports = {
  webpack: (config, options, webpack) => {
    config.entry.main = './server/index.js'
    config.module = {
      rules: [
        {
          test: /\.js$/,
          loader: "babel-loader",
          exclude: /(node_modules)/
        }
      ]
    }
    return config
  }
}
```