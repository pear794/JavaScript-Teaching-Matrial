# 基本概念

## 语法
ECMAScript的语法大量借鉴了C以及其他C语言（如Java和Perl）的语法，因此，熟悉这些语言的开发人员在接受ECMAScript更加宽松的语法时，一定会有一种轻松自在的感觉。
#### 注释 {docsify-ignore}
ECMAScript使用C语言的注释，包括单行注释和块级注释。单行注释以两个斜杠开头，如下所示：
```js
//单行注释
``` 
块级注释以一个斜杠和一个(/\*)开头，以一个星号和一个斜杠(\*/)结尾，如下所示：
```js
/*
* 这是一个多行
* （块级）注释
*/
```
## 变量
#### ES6 声明变量的六种方法 {docsify-ignore}
ES5 只有两种声明变量的方法：`var`命令和`function`命令。ES6 除了添加`let`和`const`命令，后面章节还会提到，另外两种声明变量的方法：`import`命令和`class`命令。所以，ES6 一共有 6 种声明变量的方法。
```js
var message
```
这行代码定义了一个名为`message`的变量，该变量用来保存任何值（像这样未经初始化的变量，会保存一个特殊的值——`undefined`）。
ECMASript也支持直接初始化变量，因此在定义变量的同时就可以设置变量的值，如下所示：
```js
var message = 'hi'
```
#### let命令
ES6新增了`let`命令，用来声明变量。它的用法类似于`var`，但是声明的变量，只在`let`命令所在的代码块内有效
```js
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```
上面代码在代码块之中，分别用`let`和`var`声明了两个变量。然后在代码块之外调用这两个变量，结果`let`声明的变量报错，`var`声明的变量返回了正确的值。这表明，`let`声明的变量只在它所在的代码块有效。  
相比之下，`let`比`var`更加的合理和强大，以后声明变量使用`let`来替代`var`

#### const命令
`const`用来声明一个只读的常量。一旦声明，常量的值就不能改变
```js
const MAX = 10
console.log(MAX) //10
MAX = 11 //报错：TypeError: Assignment to constant variable.
```
上面的代码表明改变常量的值会报错
`const`和`let`一样具有块级作用域，只在声明内的块级作用域内有效
```js
if(true){
    const MAX = 10
}
console.log(MAX) // Uncaught ReferenceError: MAX is not defined
```
#### 总结
```js
//bad
var a = 10

//good
let a = 10

//best
const a = 10
```
在`let`和`const`之间，建议优先使用`const`,尤其是全局环境，不应该设置变量，只设置常量
## 数据类型
es5有5种基本的数据类型：`Undefined`、`Null`、`Boolean`、`Number`、`String`和一个复杂的数据类型`Object`  
es6新增了一个新的原始数据类型`Symbol`










