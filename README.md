# univer-vue3-ts

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

## [离线安装pm2](https://jingsam.github.io/2018/11/24/npm-package-offline-install.html)

### 使用`npm link`

使用`npm link`的方式是最常用的方法，具体做法是在联网机器上下载pm2的源码并安装好依赖，拷贝到离线服务器上，最后借助`npm link`将pm2链接到全局区域。

首先，将pm2的源代码克隆下来：

```
git clone https://github.com/Unitech/pm2.git
```

然后进入到pm2项目中，安装好所有的依赖：

```
cd pm2
npm install
```

将安装好依赖的pm2文件夹拷贝到目标服务器上，进入pm2目录链接到全局区域：

```
cd pm2
npm link
```

### 使用npm bundle

那有什么方法相比于上一种方法更干净呢？答案是使用npm-bundle工具将pm2的所有依赖打包，然后到目标服务器上使用`npm install <tarball file>`安装。

首先在联网机器上安装npm-bundle工具：

```
npm install -g npm-bundle
```

然后打包pm2：

```
npm-bundle pm2
```

上面的命令会生成一个tgz的包文件，复制到目标服务器上安装：

```
npm install -g ./pm2-3.2.2.tgz
```

备注：
我用第二种方式成功实现离线安装

特别鸣谢[jingsam](https://jingsam.github.io/2018/11/24/npm-package-offline-install.html)
