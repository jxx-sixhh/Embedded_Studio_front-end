## 1,解释JS中的函数提升

在Js中，预编译的时候先会进行变量提升，就是先讲声明的变量提升到全局执行上下文GO中，再进行函数提升，函数提升只会对函数声明进行提升，而不会对函数表达式进行提升，一同放入GO中   

## 2,哪些操作会造成内存泄漏 

1),在函数内部定义了一个未声明的变量，例如function(){ a = 1; }

2),在函数内部形成了闭包，例如 function(){ var a = 1 function b(){ a += 1; } return b; }

3),没有清除DOM元素引用

4),被遗忘的定时器或者回调

5),子元素存在引起的内存泄漏

## 3，简述JavaScript中this的指向

1),如果创建了一个对象，则该对象属性与方法中的this指向对象本省

2),如果构造可实例化的函数，那么里面的this指向的是实例化的对象本身，而不是该函数

3),在对DOM元素添加事件的时候addEventLister时，回调函数里面的this指向被添加事件的元素

4),全局环境下的this指向window

5),箭头函数中的this，箭头函数中没有 this， 它会绑定最近的非箭头函数作用域中的this。首先从它的父级作用域找，如果父级作用域还是箭头函数，就再往上找，一层一层的直到直到this的指向。

## 4，[476. 数字的补数](https://leetcode-cn.com/problems/number-complement/)（二进制）

```javascript
```

var findComplement = function(num) {

​    var binary = num.toString(2);

​    let res = '';

​    for(let i = 0 ;i<binary.length;i++){

​        res += binary[i] ^ 1;

​    }

​    return parseInt(res,2);

};