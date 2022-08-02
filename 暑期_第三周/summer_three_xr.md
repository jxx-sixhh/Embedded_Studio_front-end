# 下周计划
做项目+听直播课+学vue+刷题

# 复习

## 1. 怎么设置执行上下文中的this指向其他对象？

1.通过call/bind/apply 改变 this

2.通过对象调用方法设置。

3.通过构造函数中设置

## 2. 代码中出现相同的变量，JavaScript引擎是如何选择的？

通过作用域链查找变量。如果在当前的变量环境中没有查找到，那么 JavaScript 引擎会继续在 outer 所指向的执行上下文中查找

```js
function bar() {
  console.log(myName)
}

function foo() {
  var myName = "test"
  bar()
}
var myName = "123"
foo()
```

这段代码的运行结果是什么？怎么解释？

结果是123

作用域链由词法作用域决定，foo 和 bar 的上级作用域都是全局作用域，所以如果 foo 或者 bar 函数使用了一个它们没有定义的变量，会到全局作用域去查找。

# React/Vue

## 1. 提供两个input框，分别为用户名和密码，在点击登陆时弹出输入的用户名和密码信息

写两种 受控组件和不受控组件

```Vue
<template>
        <div class="box">
            <h2>Please sign up.</h2>
            <div class="putin">
                <label for="username">Account</label>
                <input type="text" id="username" placeholder="account" key="username" v-model="account">
            </div>
            <div class="putin">
                <label for="psw">Password</label>
                <input type="password" id="psw" placeholder="password" key="psw" v-model="psw">
            </div>
            <button class="login" v-on:click="change">Login</button>
        </div>
</template>
<script>
export default {
    name:'LoginBox',
    data(){
        return {
            account:'',
            psw:''
        }
    },
    methods:{
        change(){
            alert('account = ' + this.account +
                    '\npassword = ' + this.psw)
        }
    }
}
</script>
<style lang="less">
    .box {
        width: 350px;
        height: 300px;
        text-align: center;
        margin: auto;
        background: linear-gradient(90deg, pink, skyblue);
        border: black 3px solid;
        padding-top: 10px;
        h2 {
            display: block;
            height: 50px;
        }
        .putin {
            width: 350px;
            height: 40px;
            margin: 10px 0;
            label {
                display: inline-block;
                width: 100px;
                margin-right: 10px;
                text-align: right;
                font-weight: 700;
            }
            input {
                margin-right: 10px;
                width: 200px;
                height: 20px;
            }
        }
        .login {
            margin: 20px;
            width: 70px;
            height: 40px;
            font-size: 16px;
            font-weight: 700;
            background-color: rgb(242, 121, 121);
            &:hover {
                cursor: pointer;
            }
        }
    }
</style>
```
ps.vue里我没学到受控组件和不受控组件的区分概念，查了下发现网上好像基本没有讲的，所以我就按自己会的方法写啦

# 算法题

这周都写了哪些算法题呢？😎

电话号码的字母组合，字母异位词分组，验证二叉搜索树，复原IP地址
