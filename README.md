# 1 Babel-cli的安装
## 1.1 全局安装Babel-cli
```js
npm install -g babel-cli
```

## 1.2 本地安装babel-preset-es2015和babel-cli
```js
npm install --save-dev babel-preset-es2015 babel-cli
```

## 1.3 新建.babelrc文件
```js
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
```
## 1.4 ES6转ES5命令
```js
babel src/index.js -o dist/index.js
```

## 1.5 简化转化命令
```js
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
}

// npm run build 进行打包
```

# 2 变量三种声明方式
- var：它是variable的简写，可以理解成变量的意思。var 是全局声明的意思
- let：它在英文中是“让”的意思，也可以理解为一种声明的意思。 let 只在区块内起作用，外部不可调用
- const：它在英文中也是常量的意思，在ES6也是用来声明常量的，常量你可以简单理解为不变的量。

# 3 变量的解构赋值
## 3.1 数组的解构赋值
```js
let [a,b,c] = [1,2,3];
let [a,[b,c],d] = [1,[2,3],4];
```
## 3.2 数组解构的默认值
```js
let [a,b="JSPang"]=['技术胖']
console.log(a+b); //控制台显示“技术胖JSPang”
// 解构赋值中undefined相当于什么都没有，null是表示有值，值为null
```
## 3.3 对象的解构赋值
```js
let {foo,bar} = {foo:"foo",bar:"bar"};
// TODO: 如果在解构之前已经进行定义,要在解构的语句外加一个圆括号
let foo;
({foo} ={foo:'foo'});
console.log(foo); //控制台输出foo
```
## 3.4 字符串的解构赋值
```js
const [a,b,c,d]="Pony";
console.log(a);
console.log(b);
console.log(c);
console.log(d);
// 依次输出P o n y
```

# 4 扩展运算符和rest运算符
## 4.1 拓展运算符
```js
function pony(...arg){
    console.log(arg[0]);
    console.log(arg[1]);
    console.log(arg[2]);
    console.log(arg[3]);
}
pony(1,2,3);
// 利用拓展运算符解决内存堆栈的引用
let arr1=['www','pony','com'];
//let arr2=arr1;
let arr2=[...arr1];
console.log(arr2);
arr2.push('some');
console.log(arr2);
console.log(arr1);
```
## 4.2 rest运算符
```js
function pony(first,...arg){
    console.log(arg.length);
}

pony(0,1,2,3,4,5,6,7);
// 输出为7
function pony(first,...arg){
    // 用for of循环输出arg参数中的值
    for(let var of arg){
        console.log(var);
    }
    // TODO: for...of的循环可以避免我们开拓内存空间，增加代码运行效率。
}
    
```
# 5 字符串模板
## 5.1 字符串模板的使用
```js
let pony= "小马驹";
let nickName = `我的QQ昵称是${pony}`;  // 用连接符 ` 
console.log(nickName); //输出是我的QQ昵称是小马驹
// NOTE: 支持运算
let [a,b]="12";
console.log(`${a+b}`); //输出12
```
## 5.2 字符串查找【includes】
```js
let pony = "大熊猫";
let desc = "我国的国宝是大熊猫";
console.log(desc.includes(pony));
// 判断开头是否存在
desc.startsWith(pony);
// 判断结尾是否存在
desc.endsWith(pony);
```
## 5.3 复制字符串
```js
console.log("pony|".repeat(3)); // 将字符串"pony|"重复三次
```
# 6 ES6数字操作
## 6.1 二进制和八进制
```js
// NOTE: 二进制，以0b或者0B开头
let ejz = 0B0101011;
console.log(ejz); //输出二进制对应的十进制数
// NOTE: 八进制，以0o或者0O开头
let bjz = 0o666;
console.log(bjz); //输出八进制对应的十进制数
```
## 6.2 数字判断和转换
- 数字验证 Number.isFinite(x);
- NaN验证 Number.isNaN(NaN);
- 判断是否为整数 Number.isInteger(x);
- 整数转换 Number.parseInt(x);
- 浮点型转换 Number.parseFloat(x);
## 6.3 数字取值范围
- 最大安全整数 Number.MAX_SAFE_INTEGER
- 最小安全整数 Number.MIN_SAFE_INTEGER
- 安全整数判断 Number.isSafeInteger(x); 【不在安全整数范围输出false】

# 7 数组处理①
## 7.1 数组




