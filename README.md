# 全局安装Babel-cli
npm install -g babel-cli

# 本地安装babel-preset-es2015和babel-cli
npm install --save-dev babel-preset-es2015 babel-cli

# 新建.babelrc
```js
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
```
# ES6转ES5命令
babel src/index.js -o dist/index.js

# 简化转化命令
```js
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
}

// npm run build 进行打包
```

# 三种声明方式
- var：它是variable的简写，可以理解成变量的意思。var 是全局声明的意思
- let：它在英文中是“让”的意思，也可以理解为一种声明的意思。 let 只在区块内起作用，外部不可调用
- const：它在英文中也是常量的意思，在ES6也是用来声明常量的，常量你可以简单理解为不变的量。

# 变量的解构赋值
