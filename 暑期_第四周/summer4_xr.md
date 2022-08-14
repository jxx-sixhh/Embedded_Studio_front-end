# 下周计划

# 复习

## 1.

```js
let userInfo = {
 name:"jack.ma",
 age:13,
 sex:"male",
 updateInfo:function(){
  // 模拟 xmlhttprequest 请求延时
  setTimeout(function(){
   this.name="pony.ma"
   this.age = 39
   this.sex = female
  },100)
 }
} 
```

我想通过 updateInfo 来更新 userInfo 里面的数据信息，但是这段代码存在一些问题，你能修复这段代码吗？

至少写两种方法

法1：
```js
let userInfo = {
  name:"jack.ma",
  age:13,
  sex:'male',
  updateInfo:function(){
    // 模拟 xmlhttprequest 请求延时
    setTimeout(() => {
      this.name = "pony.ma"
      this.age = 39
      this.sex = female
    },100)
  }
}
```
法2：
```js
let userInfo = {
  name:"jack.ma",
  age:13,
  sex:'male',
  updateInfo:function(){
    let t = this;
    // 模拟 xmlhttprequest 请求延时
    setTimeout(function() {
      t.name = "pony.ma"
      t.age = 39
      t.sex = female
    },100)
  }
}
```
## 2. 

[第十三届蓝桥杯（Web 应用开发）线上模拟赛 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/contests/cup-s1/challenges/)

完成 ‘flex经典骰子布局’

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>骰子布局</title>
    <style>
        body {
            margin: 10px 0 0 0;
            display: flex;
            justify-content: space-around;
        }
        
        body>div {
            display: flex;
            width: 100px;
            height: 100px;
            border-radius: 4px;
            border: 2px solid red;
            box-sizing: border-box;
        }
        .div1 {
            justify-content: center;
            align-items: center;
        }
        .div2 {
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
        }
        .div3 {
            justify-content: space-around;
            align-items: center;
        }
        .div3 p:nth-child(1) {
            align-self: flex-start;
        }
        .div3 p:nth-child(2) {
            align-self: center;
        }
        .div3 p:nth-child(3) {
            align-self: flex-end;
        }
        
        .div4,
        .div8 {
            flex-direction: column;
            justify-content: space-around;
        }
        .div4 div,
        .div8 div {
            display: flex;
            justify-content: space-around;
        }

        .div8 div {
            justify-content: space-between;
        }

        p {
            width: 15px;
            height: 15px;
            background-color: black;
            border-radius: 50%;
            margin: 2px;
        }
        
        .div1 {
            justify-content: center;
            align-items: center;
        }
        /*todo:请补全剩余骰子布局代码*/
    </style>
</head>

<body>
    <!--骰子1-->
    <div class="div1">
        <p></p>
    </div>
    <!--骰子2-->
    <div class="div2">
        <p></p>
        <p></p>
    </div>
    <!--骰子3-->
    <div class="div3">
        <p></p>
        <p></p>
        <p></p>
    </div>
    <!--骰子4-->
    <div class="div4">
        <div>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
        </div>
    </div>
    <!--骰子5-->
    <div class="div4">
        <div>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
        </div>
    </div>
    <!--骰子6-->
    <div class="div4">
        <div>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
        </div>
    </div>
    <!--骰子7-->
    <div class="div4">
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
    </div>
    <!--骰子8-->
    <div class="div8">
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
    </div>
    <!--骰子9-->
    <div class="div4">
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
        <div>
            <p></p>
            <p></p>
            <p></p>
        </div>
    </div>
</body>

</html>
```

# React/Vue

#### 一. props的基本使用

​	设计两个组件，A组件通过props向B组件传递『商品名称，商品价格，商品库存』信息。

子组件
```Vue
<template>
    <div class="MyChild">
        <h1>{{val}}</h1>
    </div>
</template>
<script>
export default {
    name:'MyChild',
    props:['val']
}
</script>
```
父组件
```Vue
<template>
  <div id="app">
    <TheChild :val="value"></TheChild>
  </div>
</template>

<script>

import TheChild from './components/TheChild.vue'
export default {
  name: 'App',
  components: {
    TheChild
  },
  data(){
    return {
      value: "商品名称，商品价格，商品库存"
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```


#### 二.数据类型校验

​	通过prop-types对props中的值进行校验

子组件
```vue
<template>
    <div class="MyChild">
        <h1>{{val}}</h1>
    </div>
</template>
<script>
export default {
    name:'MyChild',
    props: {
        val: {
            type: String,
            required: true
        }
    }
}
</script>
```



# 算法题

这周都写了哪些算法题呢？😎

分割字符串的最大得分,盛最多水的容器，用户分组，在二叉树中增加一行，求解方程，函数的独占时间
