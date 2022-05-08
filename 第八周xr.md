# 下周学习计划

你的答案

# 1. 类型介绍

## 1.1 Javascript数据类型有哪些？请按照基本数据类型和引用数据类型来分类

基本数据类型:Undefined,Null,String,Number,Boolean,Symbol<br/>
引用数据类型:Object(Object,Array,Date,RegExp,Function)

## 1.2 请介绍基本数据类型和引用数据类型的区别

1.基本数据类型的值是不可变的,不能给它添加属性和方法；引用数据类型可以拥有属性和方法，且值是可变的。<br/>
2.基本数据类型的变量是存放在栈里面的；引用数据类型的值是同时保存在栈内存和堆内存的对象。<br/>
3.基本数据类型的比较是值的比较，只有值相等的时候才是相等的；引用类型的比较是引用的比较。

# 2. 判断数据类型的方法有哪些？

1.typeof判断基本数据类型
```javascript
var str="123";
typeof str;//string
typeof function(){};//function
```
2.instanceof一般判断引用数据类型，判断一个实例是否属于某种类型
```javascript
let people=function(){};
let Mary=new people();
console.log(Mary instanceof people);//true
```
3.Object.prototype.toString()
```javascript
console.log(toString.call(123));//[object Number]
console.log(toString.call(true));//[object Boolean]
```
4.根据对象的constructor
```javascript
console.log([].constructor === Array);//true
var obj = new Object();
console.log(obj.constructor === Object);//true
console.log("string".constructor === String);//true
```

## 怎么判断一个变量arr是否为数组
```javascript
console.log(arr instanceof Array);//1
console.log(arr.constructor === Array);//2
console.log(Array.isArray(arr));//3
console.log(toString.call(arr) === '[object Array]');//4
console.log(arr._proto_ === Array.prototype);//5.判断对象原型
console.log(Object.getPrototypeOf(arr) === Array.prototype);//6
console.log(Array.prototype.isPrototypeOf(arr));//7
```

# 3. null和undefined有什么区别
1.null表示没有对象，即该处不应该有值<br/>
1） 作为函数的参数，表示该函数的参数不是对象.<br/>
2） 作为对象原型链的终点.<br/>
2.undefined表示缺少值，即此处应该有值，但没有定义.<br/>
1）定义了形参，没有传实参，显示undefined.<br/>
2）对象属性名不存在时，显示undefined.<br/>
3）函数没有写返回值，即没有写return，拿到的是undefined.<br/>
4）写了return，但没有赋值，拿到的是undefined.<br/>
3.null和undefined转换成number数据类型时，null 默认转成 0，undefined 默认转成 NaN

# 4. 请介绍深浅拷贝
浅拷贝拷贝的是地址,深拷贝拷贝的是内容.浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。
