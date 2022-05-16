# 下周计划


# 1. let和var有什么区别？  
1.相同:使用let与var分别声明两个变量后均未赋值的话console.log()均输出undefined.
2. 不同: （1）使用未声明的变量 表现不相同 下列let未声明是由于let定义的变量不会有变量提升
             （2）重复声明同一个变量时 var 声明的变量的值会被覆盖 但是let声明了两个相同的变量名时会报错SyntaxError: Identifier '变量名' has already been declared;
             （3）变量的作用范围不同 let声明的变量只能在当前的块级作用域下使用 但是 var 声明的是全局的变量
             （4）let创建的全局变量没有给window设置对应的属性
             （5）let能解决typeof检测时出现的暂时性死区问题（let比var更严谨）PS:typeof存在暂时性死区，当检测一个未被声明过的变量时，不会报错，结果是undefined

## 1.1 分析区别



## 1.2 分析代码剖析原因

### 1.2.1


```js
function sayHi(){
    console.log(name);
    console.log(age);
    var name = 'Lily';
    let age = 21;
}
```

A. Lily 和 undefined

B. Lily 和 ReferenceError

C. ReferenceError 和 21

D. undefined 和 ReferenceError

答案是什么？并解释一下为什么
答案为D 在function执行后产生sayHi本身的AO = { var a:undefined }因为let声明的变量不会有变量提升所以开始执行函数
所以第一个打印的就是undefined，又由于let的原因所以此时age没有初始化不能被打印  ReferenceError: Cannot access 'age' before initialization
### 1.2.2

```js
var name = 'Matt'; 
console.log(window.name); 
let age = 26; 
console.log(window.age);  
```

第一个打印的应该是 'Matt' 第二个打印undefined 因为在window现象里面找不到age let声明的变量没有给window设置属性

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
两个打印的都是6 var i声明的是全局变量 而下面let i声明的是在for的块级作用域的一个变量 全局无法访问 所以第二个console.log(i)的i应该是 var i;
### 1.2.4

```js
for (var i = 0; i < 5; ++i) { 
 setTimeout(() => console.log(i), 0) 
} 
for (let i = 0; i < 5; ++i) { 
 setTimeout(() => console.log(i), 0) 
}
```
第一个for循环打印了五个5 第二个for循环打印的是0 1 2 3 4 5 我的理解是第一个for循环由于是 var i 当他开始循环的时候定时器里面的回调函数会进入异步进程里面去等待执行 由于此时的i是全局变量 所以异步进程里面的i在循环结束后全部都变成了5 所以打印出来全是5 但是第二个for循环是let i 每一次循环开始的时候都会有一个自己的块级作用域产生 所以定时器回调函数里面的i都不会相同
# 2. 箭头函数

## 2.1 箭头函数有哪些特点？( )=>{ }
1. 箭头函数使用=>连接参数列表和函数体
2. 当参数只有一个的时候，括号可以省略；但是没有参数的时候，括号不可以省略
3. 箭头函数的函数体有两种形式，一种只包含了一个表达式,省略掉了{}和return，这个时候返回的要么是表达式的值，要么是表达式的真假
还有一种可以包含多条语句，但是这个就不能省略reutrn了 如果返回的只有一个语句但是这个语句是对象的话必须在对象的外层套上一个括号
4. 箭头函数内部的this是词法作用域，由上下文决定（词法作用域就是定义在词法阶段的作用域。换句话说，词法作用域是由你在写代码时将变量和块作用域写在哪里来决定的，因此当词法分析器处理代码时会保持作用域不变 。）

## 2.2 分析代码

```js
const shape = {
    radius : 10,
    diameter(){
        return this.radius * 2；
    },
  	perimeter: ()=> 2* Math.PI * this.radius
};
console.log(shape.diameter());
console.log(shape.perimeter());
```
第一个打印20 第二个打印NaN 因为shape是一个对象 在perimeter的箭头函数中 this的指向为window 但是window里没有radius这个属性，所以当一个常数*undefined时就是NaN。
# 3.请用代码解释解构赋值
只要某种数据结构具有 Iterator 接口，都可以采用数组形式的解构赋值
## 数组的解构赋值
简单的数组的解构
```
{
    let a,b;
    [a,b]=[1,2];
    console.log(a,b) //输出 a=1  b=2;
}
```
含有扩展运算符(…)的解构
```
{
    let a,b,c;
    [a,b,...c]=[1,2,3,4,5,6];
    console.log(a,b,c) //输出 a=1  b=2  c=[3,4,5,6];
}
```
当解构不成功或者解构不完全的时候  
```
{
    let a,b,c;
    [a,b,c]=[1,2];
    console.log(a,b,c);//输出 a=1  b=2  c=undefined;
}
{
    let a,b;
    [a,b]=[1,2,3];
    console.log(a,b);//输出  a=1  b=2;
}
```
解构赋值是允许设定默认值的，但是只有undefined才会触发使用默认值。
```
{
    let foo;
    [foo=12]=[];
    console.log(foo)  //输出 12;
}
{
    let[x,y="b"]=["a",undefined]// x="a" ,y="b"
}
{
    let a=2;
    [a]=["undefined"];
    console.log(a); //输出  a="undefined"
}
```
解构顺序
```
{
    let[x=1,y=x]=[2]
    console.log(x,y) //  x=2  y=2
}    
```
## 对象的解构赋值
对象的解构赋值与数组有一个重要的不同。数组的元素是按顺序进行排列的，变量的取值是由它的位置决定的，而对象的属性是没有次序的，变量必须与属性同名，而且等号两边的结构和格式是一模一样的，这样才能取到正确的值。
```
{
    let {bar,foo}={foo:"aaa",bar:"bbb"}
    console.log(foo,bar); //输出  foo="aaa"  bar="bbb"
}
{
    let {baz}={foo:"aaa",bar:"bbb"};
    console.log(baz);//输出 undefined
}
{
    let{x,y,z=1,a:q}={a:100,b:200,y:300}//这里的是先找到了a 实际上是把a赋值给了q 这个时候q才是属性名
    console.log(x,y,z,q);// x=undefined  y=300 z=1 q=100
}
```
对象的解构赋值的内部机制是先找到相同属性名的，然后进行赋值给对应的变量，其实真正被赋值的是后者，而不是前者。
```
{
    let{foo:baz}={foo:"aaa",bar:"bbb"};
    console.log(baz);//输出 baz="aaa"
    console.log(foo);//输出 将会报错  error:foo is not defined
}    //foo是一个属性名而不是一个变量，赋值是baz被赋值“aaa”。
```
## 字符串的解构赋
```
{
    let[a,b,c,d,e]="hello";
    console.log(a,b,c,d,e); //输出 a="h" b="e" c="l" d="l" e="o"
}
```
类似数组的对象都有一个length属性，同时还可以对这个属性进行解构。
```
{
    let{length:len}="hello";
    console.log(len); //输出 len=5
}
```



    




