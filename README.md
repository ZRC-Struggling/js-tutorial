# js-tutorial
JavaScript入门'辅助'教程，力求通俗易懂。
适用读者：既适合“0编程基础的求学者”，也适合有初级编程基础的开发人员
（包括需要涉猎js的后台人员，以及初入前端的爱好者）

## JavaScript是什么
它出生于1995年，是一门动态的、解释性的脚本语言(scripting language)，可以跨平台（安卓、iOS等），也是唯一一门浏览器和服务器都支持的语言。它基于prototype(原型)，支持函数式和OOP(面向对象)两种编程范式，大小写敏感，容错性高。
## JavaScript的组成
- ECMAScript (发音为"ek-ma-script"，定义了语法标准)
- BOM (Browser Object Model, 浏览器对象模型，提供与浏览器交互的方法和接口)
- DOM (Document Object Model, 文档对象模型，提供访问和操作网页内容的方法和接口)

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
0/0都不会报错，它会返回NaN(Not a Number)，NaN不算是一种数据类型，姑且算它是number里面的异类吧，而且NaN连自己都不认识(NaN == NaN)，
用NaN来做运算，结果通常也是NaN，当然也有特例，那就是查看它的数据类型。
```javascript
3 / 2 // 1.5 在有些编程语言里，整数/整数，即使不能整除，也会返回一个整数，但是JS中则会返回具体值。
NaN + 1 // NaN
NaN - 1 // NaN
typeof NaN // number
```

将一个字符串转为数字有多种方式，可以用parseInt,parseFloat,Number，以及“+-*/”
```javascript
parseInt('1'); // 1
```

### string也很特别
JS中没有char类型，所以不管是字符，还是字符串，都被看做string，并且都可以用单引号或者双引号围起来
### null真奇怪
用typeof来查看null的数据类型，结果居然是'object'，有些人觉得“存在即合理”，但我觉得这算个设计缺陷，没带来什么好处。
### boolean挺正常
JS中boolean有两个值，一真(true)一假(false)。
在JS中，有5类假值(falsy：是false或者转布尔值后是false)，分别是：
```javascript
false
0(-0, 0n,-0n)、NaN
''(同"")
null
undefined
```
除了这些，其它值均为真值，所以，空对象{}, 空数组[]，都是真值。
要把其它类型的值转为布尔值，可以用Boolean()方法，也可以在其前加!!，例如：
```javascript
Boolean([]) // true
!!{} // true 前面加一个!，会触发自动转布尔型，并取非，再加一个!，再取非，可谓负负得正
```

### 数组
由于JS是动态类型语言，它很灵活，数组元素的数据类型可以是不同的，而且数组不会有溢出异常，这也体现
它的高容错性。
eg:
```javascript
const arr = [
	true,
	1,
	'人生还有多少个二十年',
	null,
	undefined,
	[],
	{},
	function () {},
	new Date(),
	/\s+/,
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
const 震惊 = '中文居然可以用来命名!!!';
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
表达式由数据和运算符组成，并返回一个运算结果。单纯的表达式没有太大意义，因为没有改变状态。
eg:
```javascript
1 + 1 // 返回了一个值2，但是不会对程序逻辑产生任何影响。
```
## 语句
表达式可以组成语句，一个语句通常包含一个或多个表达式，执行变量声明、赋值等职能。
## 顺序结构、分支结构、循环结构
- 顺序结构是常规流，语句是从上到下按顺序执行的
- 分支结构是多路径流，根据条件，决定走哪一条路
- 循环结构是循环流，通常是改变某个状态，重复执行某个或者某些操作。

## 常用api
### 数组
实例方法
```javascript
const arr = [];
// 往数组推入元素，返回数组元素的长度
// 此处返回3，arr的值为[1, 2, 3]
arr.push(1, 2, 3);
// 从数组末尾移除元素，返回移除的元素
// 此处返回3，arr的值为[1, 2]
arr.pop(); 
// 往数组开头推入元素，返回数组的长度
// 此处返回3，arr的值为["a", 1, 2]
arr.unshift('a'); 
// 从数组开头移除元素，返回移除的元素
// 此处返回'a'，arr的值为[1, 2]
arr.shift(); 
// 做数组合并操作，返回一个新数组，原数组保持不变
// 此处返回[1, 2, 10, 11, 12]，arr的值为[1, 2]
arr.concat([10, 11, 12]);
// 从数组某个索引开始，删除若干个元素，再插入若干个新元素，返回删除的元素组成的数组
// 此处返回[]，arr的值为[1, 2, 10]
arr.splice(2, 0, 10);
// 数组排序，默认按字符序来排，会将原数组排序后返回，原数组会改变
// 此处返回[1, 10, 2]，arr的值为[1, 10, 2]
arr.sort(); 
// 截取起始索引和结束索引之间的元素，返回一个新数组，原数组保持不变
// 此处返回[1]，arr的值为[1, 10, 2]
arr.slice(0, 1);
```

静态方法
```javascript
// Array.isArray用来判断给定值是否为数组，这里返回false
Array.isArray(document.querySelectorAll('div'));
// Array.from可把类数组转为数组，这里返回true
Array.isArray(Array.from(document.querySelectorAll('div')))
```

### 对象
实例方法
```javascript
// hasOwnProperty用来判断对象自身（排除从原型上继承的属性）是否有该属性
({
    name: 'Bob',
    age: 100,
}).hasOwnProperty('name')
```
静态方法
```javascript
// Object.assign用来合并对象
// {a: "a", b: 2, c: {c1: "cc"}}
Object.assign(
	{},
	{
		a: 1,
		b: 2,
		c: {
			c1: 33
		}
	},
	{
		a: 'a',
		c: {
			c1: 'cc'
		}
	}
);
const obj1 = {};
// Object.defineProperty通常用来指定对象属性的特性
Object.defineProperty(obj1, 'a', {
    value: '1',
});
// Object.getOwnPropertyDescriptors会返回对象属性的特性 
// {a: {value: "1", writable: false, enumerable: false, configurable: false}}
Object.getOwnPropertyDescriptors(obj1);
const obj2 = {
    a: '2'
};
// Object.seal可用于“密封”对象，使得它的属性不能被增/删，但可被修改
Object.seal(obj2);
Object.getOwnPropertyDescriptors(obj2);
// {a: {value: "2", writable: true, enumerable: true, configurable: false}}
const obj3 = {
    a: '3'
};
// Object.freeze用来“冻结”对象，使得它的属性不能增/删/改，仅仅支持枚举
Object.freeze(obj3);
Object.getOwnPropertyDescriptors(obj3);
// {a: {value: "3", writable: false, enumerable: true, configurable: false}}

```

### 函数
实例方法
```javascript
// `=>`用于指示这是一个函数，用它代替function关键字，并且当函数主体是一个返回值时，还可省略`{}`
// 与常规函数相比，这样显得更简洁。
const foo = (a, b, c) => console.log(a, b, c);
// 函数的call、apply、bind都可以改变函数的上下文（即函数内this的指向）
// call、apply会使用给定的参数，调用函数，而bind仅仅为函数绑定上下文或实参，它返回的是一个函数
// call传实参，是逐个传递，而apply则接收类数组（length属性为正整数）
foo.call(this, 1, 2, 3); // 1 2 3
foo.apply(this, [1, 2, 3]); // 1 2 3
(foo.bind(this, 1, 2, 3))(); // 1 2 3
// 函数的length数组会返回函数的形参个数
foo.length // 3
foo.bind(this, 1, 2, 3).length // 0
```

## 术语解释
脚本语言：是为了缩短传统的编写-编译-链接-运行（edit-compile-link-run）过程而创建的计算机编程语言。

## 参考链接
- [JavaScript 教程 - 网道](https://wangdoc.com/javascript/)
- [ECMAScript 6 简介 - ECMAScript 6入门](https://es6.ruanyifeng.com/#docs/intro)
- [JavaScript教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1022910821149312)
