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
## 7.1 JSON数组格式转换 Array.from()
```js
let json = {
    "0":"first",
    "1":"second",
    "2":"third",
    length:3
}
// TODO: 利用Array.from() 将上述样式的json数据转换成数组格式
console.log(Array.from(json));
```
## 7.2 文本或者变量转换成数组 Array.of()
```js
// 文本
let arr = Array.of(3,4,5,6);
console.log(arr); // [3,4,5,6]
// 字符串
let arr = Array.of('first','second','third','fourth');
console.log(arr); //['first','second','third','fourth']
```
## 查找数组元素 arr.find()
```js
let arr=[1,2,3,4,5,40,7,8,9];
console.log(arr.find(function(value,index,arr){
    return value > 5;
}))
// 输出为40

/** 
* find方法中的匿名函数的参数值
* value：当前查找的值
* index: 表示当前查找的数组索引
* arr: 表示当前数组
*/
```
# 8 数组处理②
## 8.1 数组填充 arr.fill()
```js
let arr = [1,2,4,5];
console.log(arr.fill(3,2,5));
// 输出为[1,2,3,3,3,4,5,]
// 将数组索引2到索引5的位置用3填充
```
## 8.2 数组遍历 

### 8.2.1 for...of循环
```js
let arr = ['first','second','third'];
for (let item of arr){
    console.log(item);
} 
// 输出为first second third
```
### 8.2.2 for...of数组索引
```js
let arr = ['first','second','third'];
for(let index of arr.keys()){
    console.log(index);
}
// 输出为0 1 2
```
### 8.2.3 同时输出数组的内容和索引
```js
let arr = ['first','second','third'];
for(let [index,val] of arr.entries()){
    console.log(index,val);
}
```
## 8.2 entries() 实例方法
entries()方法生成迭代（Iteration）形式的数组
```js
let arr = ['first','second','third'];
let list = arr.entries();
console.log(list.next().value); // [0,'first'];
console.log(list.next().value); // [1,'second'];
console.log(list.next().value); // [2,'third'];
```
# 9 箭头函数及拓展
# 9.1 主动抛出错误
ES6的函数中可设置默认参数
```js
function add(a,b=1){
   
    if(a == 0){
        throw new Error('This is error')
    }
     return a+b;
}
 
console.log(add(0));

```
## 9.2 函数中的严谨模式
```js
function add(a,b=1){
    'use strict'
    if(a == 0){
        throw new Error('This is error');
    }
     return a+b;
}
 
console.log(add(1));
```
## 9.3 获得传递参数个数
```js
function add(a,b=1){
    'use strict'
    if(a == 0){
        throw new Error("This is arror");
    }else{
        return a + b;
    }
}
// 获取传递参数个数
console.log(add.length); // => 2
// 去掉函数中的严谨模式后，获取参数个数为
console.log(add.length); // => 1
```
## 9.4 箭头函数
```js
// TODO: 如果单纯一个语句时，{}括号可以省略
var add = (a,b=1) => a+b;
console.log(add(1)) // 输出为2
// TODO: 方法体内如果是两句话，那就需要在方法体外边加上{}括号
var add = (a,b=1) => {
    console.log("箭头函数代码中两句话加括号");
    return a + b;
}
console.log(add(1));
```
# 10 函数解构和数组补漏
## 10.1 函数解构
### 10.1.1 对象的函数解构
```js
let json = {
    a : "first",
    b : "second"
}
// FIXME: 这里有一个坑！！！ 函数体中参数对象 用等于号
var fun = ({a,b="none"}) => console.log(a,b);
fun(json);
```
### 10.1.2 数组的函数解构
```js
let arr = ['first','second','third'];
var fun = (a,b,c) => {
    console.log(a,b,c);
}
fun(...arr);

```
## 10.2 in的用法
in是用来判断对象或者数组中是否存在某个值的。【键或索引】
### 10.2.1 对象判断
```js
let obj = {
    a:"first",
    b:"second"
}
console.log("a" in obj);  // true
console.log("c" in obj);  // false
```
### 10.2.2 数组判断
```js
let arr=[,,,,,];
console.log(0 in arr); //false
 
let arr1=['first','second'];
console.log(0 in arr1);  // true
```
## 10.3 数组的遍历方法
- forEach()
```js
let arr = ['first','second','third'];
arr.forEach((val,index) => console.log(index,val));
// forEach循环的特点是会自动省略为空的数组元素
```
- filter()
```js
let arr = ['first','second','third'];
arr.filter(val => console.log(val));
```
- some()
```js
let arr = ['first','second','third'];
arr.some(val => console.log(val));
```
- map()
```js
let arr = ['first','second','third'];
arr.map(val => console.log(val));
// map还有替换的功能
arr.map(val => "none"); 
// 将数组全部替换成none
```
## 10.4 数组转换成字符串
- join()
```js
let arr = ['first','second','third'];
console.log(arr.join("|"));
// join() 方法就是在数组元素中间，加一些间隔
```
- toString()
```js
let arr = ['first','second','third'];
console.log(arr.toString());
```
# 11 ES6中的对象
## 11.1 对象赋值
```js
let name = "name";
let skill = "skill";
var obj = {name,skill};
console.log(obj);
```
## 11.2 对象Key值构建
```js
let key = "skill";
var obj = {
    [key]:"web"
}
console.log(obj.skill);
// TODO: 我们在后台取了一个key值，然后可以用[ ]的形式，进行对象的构建
```
## 11.3 自定义对象方法
```js
var obj = {
    add:(a,b)=>a+b
}
console.log(obj.add(1,2)); //3
```
## 11.4 对象比较 Object.is()
```js
var obj1 = {name:'jspang'};
var obj2 = {name:'jspang'};
console.log(obj1.name === obj2.name);//true
console.log(Object.is(obj1.name,obj2.name)); //true
// TODO: * ===表示同值相等，is()为严格相等
```
## 11.5 合并对象 Object.assign()
```js
let a = {a:'first'};
let b = {b:'second'};
let c = {c:'third'};
console.log(Object.assign(a,b,c));
```
# 12 Symbol在对象中的作用
## 12.1 声明Symbol()
```js
var a = Symbol();
console.log(typeof(a)); // 数据类型为undefined
```
## 12.2 Symbol的打印
```js
var g = Symbol('pony');
console.log(g); // 输出为红色的 Symbol('pony')
console.log(g.toString()); // 输出为黑色的 Symbol('pony')
```
## 12.3 Symbol在对象中的应用
```js
var pony = Symbol();
var obj = {
    [pony]:"Pony"
}
console.log(obj[pony]); // 输出为Pony
obj[pony]= "Super";
console.log(obj[pony]); // 输出为Super                                                                
```
## 12.4 Symbol对象元素的保护作用
在对象中有很多值，但是循环输出时，并不希望全部输出，那就可以使用Symbol进行保护
```js
// TODO: 没有进行保护的写法
var obj = {
    name:"Pony",
    skill:"WEB",
    age:18
}
for(let item in obj){
    console.log(obj[item]);
}
// 依次输出为Pony WEB 18 没有进行SymBol保护
// TODO: 使用Symbol进行循环保护的写法
var obj = {
    name: "Pony",
    skill:"WEB"
}
let age = Symbal();
obj[age] = 18;
for(let item in obj){
    console.log(obj[item]); // 依次输出为Pony、 WEB 对于进行保护的值不予循环输出
}
console.log(obj);  // 输出为 {name:"Pony",skill:"WEB",age:18}
```
# 13 Set和WeakSet数据结构
Set的数据结构是以数组的形式构建的
## 13.1 Set的声明
```js
let setArr = new Set(['pony','web',18]);
console.log(setArr); // Set(3) {"pony","web",18} 
```
* Set 和 Array 的区别在于Set不允许内部有重复的值，如果有只显示一个，相当于去重。
* 虽然Set很像数组，但是他们不是数组
## 13.2 Set值的增删改查
- 追加add
```js
let setArr = new Set(['pony','web',18]);
console.log(setArr);
 
setArr.add('前端职场');
console.log(setArr);
```
- 删除delete 
```js
let setArr = new Set(['pony','web',18]);
console.log(setArr);
 
setArr.add('前端职场');
console.log(setArr);

setArr.delete('前端职场');
console.log(setArr);
```
- 查找has  

用has进行值的查找，返回的是true或者false
```js
let setArr = new Set(['pony','web',18]);
console.log(setArr.has('pony')); // true
```
- 删除clear
```js
let setArr = new Set(['pony','web',18]);
console.log(setArr);
setArr.clear();
console.log(setArr); // 输出为Set(0) Set总的内容已清空 
```
## 13.3 Set的循环
```js
// TODO: for...of 循环
let setArr = new Set(['pony','web',18]);
for(let item of setArr){
    console.log(item);
}
// TODO: size 属性
console.log(setArr.size);  // size 属性可以获得Set值的数量
// TODO: forEach循环
setArr.forEach((value) => console.log(value)); // forEach循环
```
## 13.4 WeakSet的声明
```js
let weakObj = new WeakSet();
let obj = {name:"pony",sex:"male"};
weakObj.add(obj);
console.log(weakObj);
```
- 如果直接在new的时候就放入值，会报错
- WeakSet里的值同样不允许重复
- WeakSet的传入值必须是对象
# 14 map数据结构
## 14.1 JSON 和 Map 格式的对比
```js
// TODO: JSON 数据格式
let json = {
    name:'pony',
    sex:'male'
}
console.log(json.name);
// Map 数据格式
var map = new Map();
map.set(json,'iam');
// FIXME: Map数据格式是一种特殊的键值对，key可以为数组对象字符串，value同样可以为数组对象或者字符串
```