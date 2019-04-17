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
#### typeof操作符
鉴于ECMAScript是松散类型的，因此需要一种手段来检测给定变量的数据类型——typeof就是负责提供这方面的操作符。对一个值使用typeof操作符可能返回一下某个字符串
```js
'undefined' —— 如果这个值未定义
'boolean' —— 如果这个值是布尔值
'string' —— 如果这个值是字符串
`number` —— 如果这个值是数值
`object` —— 如果这个值是对象或者null
`function` —— 如果这个值是函数
`symbol` —— 如果这个值是`Symnol`类型
```
> 函数具有一些特殊的属性，因此通过typeof操作符来区分函数和其他对象是有必要的
#### Undefined类型
`Undefined`类型只有一个值，即特殊的`undefined`
```js
let a;
console.log(a); //undefined
console.log(typeof a); //undefined
```
>一般而言，不存在需要显式地把一个变量设置为`undefined`值的情况，字面值`undefined`的主要作用是用于比较  

```js
let message;
//下面这个变量并没有声明
//let name
console.log(typeof message) // undefined
console.log(message) // undefined
console.log(typeof name) //undefined
console.log(name) // Uncaught ReferenceError: name is not defined
```
>对于尚未声明过的变量，只能执行`typeof`操作符检测其数据类型，对未初始化和未声明的变量执行`typeof`操作符都返回了`undefined`值
#### Null类型
`Null`类型是第二个只有一个之值的数据类型，这个特殊的值是`null`。
`null`值表示一个空指针，用typeof操作符检测null会返回`object`
```js
let msg = null;
console.log(typeof msg) // "object"
```
>如果定义的变量是准备在将来用于保存对象，那么最好将变量初始化为`null`而不是其他值
#### Boolean类型
`Boolean`类型是ECMAScript中使用的最多的一种类型，该类型只有两个字面量：`true`和`false`  
需要注意的是，`Boolean`类型的字面值`true`和`false`是区分大小写的，也就是说`True`和`False`都不是`Boolean`值，只是标识符
```js
let message = "hello word"
if(message){
  console.log("你好，世界") //你好，世界
}
```
最后会打印出结果是因为字符串message被自动转换成了对应的`Boolean`值









