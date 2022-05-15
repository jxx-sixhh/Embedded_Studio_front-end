# 下周计划
继续学ES6+js数据结构与算法.

# 1. let和var有什么区别？

## 1.1 分析区别
1.被let声明的变量不会作为全局对象window的属性，而被var声明的变量却可以。<br/>
2.可以用let定义块级作用域变量，但{}限定不了var声明变量的访问范围。如 let只在for()循环中可用，而 var是对于包围for循环的整个函数可用。<br/>
3.var允许在同一作用域中声明同名的变量（会被新的值替代），而let不可以。<br/>
4.用let声明的变量，不存在变量提升。而且要求必须等let声明语句执行完之后，变量才能使用，不然会报Uncaught ReferenceError错误，在代码块内，使用let命令声明变量之前，该变量都是不可用的。


## 1.2 分析代码剖析原因

### 1.2.1


```js
function sayHi(){
    console.log(name);
    console.log(age);
    var name = 'Lily';
    let age = 21;
}
sayHi()
```

A. Lily 和 undefined

B. Lily 和 ReferenceError

C. ReferenceError 和 21

D. undefined 和 ReferenceError

答案是什么？并解释一下为什么

D.name在创建阶段被提升了，默认值是undefined,而此时还没有执行到使用它的行，也就是还没给它赋值，所以还是undefined;在用let声明age变量前，它都处于"暂时死区",不可访问，会报Uncaught ReferenceError错误。

### 1.2.2

```js
var name = 'Matt'; 
console.log(window.name); 
let age = 26; 
console.log(window.age);  
```
答案：Matt 和 undefined<br/>
因为被let声明的变量不会作为全局对象window的属性，而被var声明的变量却可以。

### 1.2.3

```js
for (var i = 0; i < 5; ++i) { 
 // 循环逻辑 
} 
console.log(i); 

for (let i = 0; i < 5; ++i) { 
 // 循环逻辑
} 
console.log(i); 
```
答案： 5 和 Uncaught ReferenceError<br/>
因为let只在for()循环中可用，而 var是对于包围for循环的整个函数可用。

### 1.2.4

```js
for (var i = 0; i < 5; ++i) { 
 setTimeout(() => console.log(i), 0) 
} 
for (let i = 0; i < 5; ++i) { 
 setTimeout(() => console.log(i), 0) 
}
```
答案：5 5 5 5 5 和 0 1 2 3 4<br/>
1).var声明的i在全局都有效，而循环里的setTimeout都是在循环结束后执行，所以是5个5。<br/>
2).let声明的变量有块作用域，只在本轮循环有效，所以每次循环的i都是一个新的变量，即setTimeout中的i不是同一个变量。


# 2. 箭头函数

## 2.1 箭头函数有哪些特点？

1  this是静态的，this始终指向函数声明时所在作用域下的this的值。

2.不能构造实例化对象。

3.不能使用arguments变量

## 2.2 分析代码

```js
const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius
};
console.log(shape.diameter());
console.log(shape.perimeter());

```
答案：20 和 NaN。<br/>
this始终指向函数声明时所在作用域下的this的值，此处指向window,window中没有radius这个属性。

# 3.请用代码解释解构赋值
1.数组的解构赋值
```js
const arr=['喜羊羊','美羊羊','懒羊羊','沸羊羊'];
let [xi,mei,lan,fei]=arr;
console.log(xi);
console.log(mei);
console.log(lan);
console.log(fei);
```
2.对象的解构赋值
```js
const lin={
  name: '林俊杰';
  age: 41;
  songs: function(){
    console.log("编号89757~");
  }
};
let {name,age,songs}=lin;
console.log(name);
console.log(age);
console.log(songs);
```

