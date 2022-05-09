1. 学习剩余的JS高级内容
2. 开始学习ES6-11的内容
#  1.类型介绍
## 1.1 javascript数据类型有哪些？请按照基本数据类型和引用数据类型分类。
基本数据类型:1.字符串(String) 2.数字(Number) 3.布尔(Boolean) 4.空(null) 5.未定义(undefined)  6.Symbol
引用数据类型:1.对象(Object) 2.数组(Array) 3.函数(Function) 4. 正则(RegExp) 5.日期(Date)
## 1.2 请介绍基本数据类型和引用数据类型的区别？  
基本数据类型直接按值存在栈中,基础数据类型赋值时给值
引用数据类型的数据存储在堆内存中，但是数据指针储存在栈内存中，访问引用数据时，先从栈内存中获取指针，通过指针在堆内存中找到数据，引用数据类型赋值时是赋值的地址
# 判断数据类型的方法有哪些?
1.typeof 返回一个表示数据类型的字符串，返回结果包括：number、boolean、string、symbol、object、undefined、function等7种数据类型，但不能判断null、array等
2.instanceof
用来判断A是否为B的实例，A instanceof B， 返回 boolean 值。instanceof 用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性，但它不能检测 null 和 undefined
3.Object.prototype.toString.call()
可以通过 toString() 来获取每个对象的类型。为了每个对象都能通过 Object.prototype.toString() 来检测，需要以 Function.prototype.call() 或者 Function.prototype.apply() 的形式来调用，传递要检查的对象作为第一个参数，称为 thisArg
4.调用jquery中判断数据类型的方法
jQuery.isArray();jQuery.isEmptyObject();jQuery.isFunction(),jQuery.isNumberic(),jQuery.isPlainObject()等
5.根据对象的contructor判断
console.log('数据类型判断' -  constructor);console.log(arr.constructor === Array); //trueconsole.log(date.constructor === Date); //true console.log(fn.constructor === Function); //true
## 怎么判断一个变量arr为数组
typeof arr 是否为 Array
Array.isArray(arr)是否为true
Object.prototype.toString.call(arr)是否为[Object Array]
console.log(arr.constructor === Array)是否为true
# null和undefined有什么区别？
undefined表示一个变量自然的、最原始的状态值，而null则表示一个变量被人为的设置为空对象，而不是原始状态。所以，在实际使用过程中，为了保证变量所代表的语义，不要对一个变量显式的赋值 undefined，当需要释放一个对象时，直接赋值为 null 即可。
undefined:1.声明一个变量但是没有赋值。2.访问对象上不存在的属性或者未定义的量。3.函数定义了形参，但没有传递实参 。4.使用void对表达式求值---在使用立即执行的函数表达式时，可以利用 void 运算符让 JavaScript 引擎把一个function关键字识别成函数表达式而不是函数声明（语句）
null:当我们使用typeof操作符检测null值，我们理所应当地认为应该返"Null"类型呀，但是事实返回的类型却是"object"
# 请介绍深浅拷贝
浅拷贝就是对值的一种拷贝，作用于基本数据类型的值与对象中的值（第一层）（第二层相互引用（地址））的赋值（拷贝），被赋值的对象与原对象没有联系，只是单单的值相同。深拷贝递归每层引用类型，遇到对象/数组，创建一个新的，把基础的值复制过来

