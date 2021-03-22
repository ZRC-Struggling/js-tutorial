# js-tutorial
JavaScript入门'辅助'教程，力求通俗易懂。
适用读者：有初级编程基础的开发人员，包括需要涉猎js的后台人员，以及初入前端的爱好者。

## JavaScript是怎样的
它是一门动态的、解释性的脚本语言，也是唯一一门浏览器和服务器都支持的语言。它基于prototype(原型)，支持函数式和OOP(面向对象)两种编程范式，大小写敏感，容错性高。
## JavaScript的组成
- ECMAScript (语法标准)
- BOM (浏览器对象模型)
- DOM (文档对象模型)

## 回顾编程基础
在中文文章中，最基础的单元是字，字是能保持语义的最小单元，然后通过字，我们能够造出词，接着可以连词成句，
又通过一个个句子，写出了段落，最终完成了一篇文章。
类比一下，一个程序，它可以分成多个基础结构（段落），这些基础结构可以分离为语句，语句又可以拆分为词，我们
将之称为表达式，而表达式又可以拆分为变量和运算符。所以要写代码（造句），我们先要了解变量（这就涉及了数据类型），
然后学点运算符，就可以写个表达式了，通过表达式，我们能写出语句。然后再通过多个基础结构（顺序结构、分支结构、循环结构）来组织语句，就可以构建一个完整的程序。

## 数据类型
跟大多数编程语言一样，JS中有数字(number)，字符串(string)，布尔值(boolean)，null这几种常见的类型，也有数组和对象。
### number很特别
但是JS数字这种类型最初的时候是不支持细分的，其它编程语言的int、long，对应到JS中都是number类型。JS很“宽容”，
0/0都不会报错，它会返回NaN，NaN不算是一种数据类型，姑且算它是number里面的异类吧，而且NaN连自己都不认识(NaN == NaN)，
用NaN来做运算，结果通常也是NaN，当然也有特例，那就是查看它的数据类型。
```javascript
NaN + 1 // NaN
NaN - 1 // NaN
typeof NaN // number
```
### string也很特别
JS中没有char类型，所以不管是字符，还是字符串，都被看做string，并且都可以用单引号或者双引号围起来
### null真奇怪
用typeof来查看null的数据类型，结果居然是'object'，有些人觉得“存在即合理”，但我觉得这算个设计缺陷，没带来什么好处。
### boolean挺正常
JS中boolean有两个值，一真(true)一假(false)。
在JS中，有6个假值(falsy：是false或者转布尔值后是false)，分别是：
```javascript
false
0
NaN
''(同"")
null
undefine
````
除了这6个值，其它值均为真值，所以，空对象{}, 空数组[]，都是真值。
要把其它类型的值转为布尔值，可以用Boolean()方法，也可以在其前加!!，例如：
```javascript
Boolean([]) // true
!!{} // true 前面加一个!，会触发自动转布尔型，并取非，再加一个!，再取非，可谓负负得正
````
### 数组
由于JS是动态类型语言，它很灵活，数组元素的数据类型可以是不同的，而且数组不会有溢出异常，这也体现了
它的高容错性。
eg:
```javascript
var arr = [
	true, 1, '人生还有多少个二十年',
	null, undefined, [], {},
	function () {}, new Date(), /\s+/
];
arr.length; // 10
arr[100]; // 数组当前只有10个元素，但是访问它的第101(100-0+1)个却不会报错，仅仅是返回undefined
```
### 对象
创建一个JS对象，非常简单，{}
## 标识符
为了引用变量，我们需要给它们起名字，这就是标识符。
关于标识符的基本命名限制，我造了个口诀：
	"字母数字下划线，数字不能在前面"，这也是很多编程语言命名规则之一，其次就是不能用语言自身的语法名。
	还有一点可以留意一下，美元符号$也可以作为命名的元素（或许是美国霸道？其实中文名称也可以用来起名）
eg:
```javascript
var 震惊 = '中文居然可以用来命名!!!';
console.log(震惊); // 中文居然可以用来命名!!!
````
## 运算符
基本的运算符就是`+-*/`，typeof也是一个运算符，用来获取变量的类型，例如:
```javascript
typeof true // 'boolean'
typeof 1 // 'number'
typeof 'str' // 'string'
typeof [] // 'object'
typeof {} // 'object'
typeof true // boolean
```
## 表达式

## 语句

## 顺序结构、分支结构、循环结构

## 参考链接
- [JavaScript 教程 - 网道](https://wangdoc.com/javascript/)
- [ECMAScript 6 简介 - ECMAScript 6入门](https://es6.ruanyifeng.com/#docs/intro)
- [JavaScript教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1022910821149312)