# 下周计划
听青训营直播课·整理笔记+继续学习Vue+刷题


# 复习

## 1. var、let、const的区别

1.var声明的变量属于函数作用域，let和const声明的变量属于块级作用域。

2.var存在变量提升现象，而let和const不存在，变量只能在声明后使用，否则报错。

3.var变量可以重复声明（后面覆盖前面的），而在同一块级作用域，let变量不能重新声明，const变量不能修改。

4.let、const有暂时性死区，即在声明变量之前，该变量都是不可用的。var没有。

5.在变量声明时，var和let不用设置初始值，而const声明变量必须设置初始值。

6.let创建的变量可更改指针指向（可重新赋值），而const声明的变量不允许改变指针的指向。

7.var声明的变量为全局变量，并会将该变量添加为全局对象的属性，但let和const不会。
## 2. ajax

### 2.1 Ajax是啥？它的优点和缺点是啥

Ajax是"Asynchronous JavaScript and XML"的缩写即异步的Ajax和XML。是指一种创建交互式网页应用的网页开发技术，在不需要将整个网页进行重新加载的情况下，就能够更新部分网页的技术。

##### 优点
1.使用异步方式与服务器通信，具有更加迅速的响应能力。

2.可以无需刷新页面而与服务器端进行通信。

3.可以把以前一些服务器负担的工作转嫁到客户端，利用客户端闲置的能力来处理，减轻服务器和宽带的负担，节约空间和宽带租用成本。ajax原则是"按需取数据"，可以最大程度减少冗余请求和响应服务器造成的负担。

4.基于标准化的并被广泛支持的技术，不需要下载插件或者小程序。
##### 缺点
1.没有浏览历史，不能回退

2.暴露与服务器交互的细节

3.对搜索引擎的支持比较弱

4.破坏了程序的异常机制

5.不容易调试

### 2.2 如何创建一个Ajax？

1. 创建XMLHttpRequest对象

2. 设置请求信息

3. 发送请求

4.接收响应

### 2.3

请求http://www.liulongbin.top:3006/api/getbooks 并用表格来显示请求结果

贴出代码和展示结果
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        table caption {
            font-size: 2em;
            font-weight: bold;
            margin: 1em 0;
        }
        
        th,
        td {
            border: 1px solid #999;
            text-align: center;
            padding: 20px 0;
        }
        
        table thead tr {
            background-color: #008c8c;
            color: #fff;
        }
        
        table tbody tr:nth-child(odd) {
            background-color: #eee;
        }
        
        table tfoot tr td {
            text-align: right;
            padding-right: 20px;
        }
    </style>
</head>

<body>
    <button id="btn1">获取</button>

    <div id="div1"></div>
</body>
<script>
    var btn1 = document.getElementById('btn1');

    btn1.onclick = function() {
        var xhr = new XMLHttpRequest()

        xhr.open('GET', "http://www.liulongbin.top:3006/api/getbooks");

        xhr.send();

        xhr.onreadystatechange = function() {
            if (xhr.readyState === 4 && xhr.status === 200) {
                var data1 = JSON.parse(xhr.responseText);

                var list = data1.data;
                // console.log(xhr.responseText);

                var rows = [];
                for (var i = 0; i < list.length; i++) {
                    var str = '<tr><th>' + list[i].id + '</th><td>' + list[i].bookname +
                        '</td><td>' + list[i].author + '</td><td>' + list[i].publisher + '</td></tr>'
                    rows.push(str);
                }

                var div1 = document.getElementById("div1");
                div1.innerHTML = '<table><thead><tr><th>编号</th><th>书名</th><th>作者</th><th>出版社</th></tr></thead><tbody>' +
                    rows.join("") + '</tbody></table>';
            }
        }
    };
</script>
</body>

</html>
```


### 2.4 总结一下HTTP状态码
#### 概念
HTTP 状态码是用来表示网页服务器 HTTP 协议响应状态的 3 位数字代码。所有状态码的第一个数字代表了响应的五种状态之一。
#### 分类
##### 1xx	信息，服务器收到请求，需要请求者继续执行操作
- 100	Continue	继续。客户端应继续其请求
- 101	Switching Protocols	切换协议。服务器根据客户端的请求切换协议。只能切换到更高级的协议，例如，切换到HTTP的新版本协议

##### 2xx	成功，操作被成功接收并处理
- 200	OK	请求成功。一般用于GET与POST请求
- 201	Created	已创建。成功请求并创建了新的资源
- 202	Accepted	已接受。已经接受请求，但未处理完成
- 203	Non-Authoritative Information	非授权信息。请求成功。但返回的meta信息不在原始的服务器，而是一个副本
- 204	No Content	无内容。服务器成功处理，但未返回内容。在未更新网页的情况下，可确保浏览器继续显示当前文档
- 205	Reset Content	重置内容。服务器处理成功，用户终端（例如：浏览器）应重置文档视图。可通过此返回码清除浏览器的表单域
- 206	Partial Content	部分内容。服务器成功处理了部分GET请求
##### 3xx	重定向，需要进一步的操作以完成请求
- 300	Multiple Choices	多种选择。请求的资源可包括多个位置，相应可返回一个资源特征与地址的列表用于用户终端（例如：浏览器）选择
- 301	Moved Permanently	永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替
- 302	Found	临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI
- 303	See Other	查看其它地址。与301类似。使用GET和POST请求查看
- 304	Not Modified	未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望- 只返回在指定日期之后修改的资源
- 305	Use Proxy	使用代理。所请求的资源必须通过代理访问
- 306	Unused	已经被废弃的HTTP状态码
- 307	Temporary Redirect	临时重定向。与302类似。使用GET请求重定向
##### 4xx	客户端错误，请求包含语法错误或无法完成请求
- 400	Bad Request	客户端请求的语法错误，服务器无法理解
- 401	Unauthorized	请求要求用户的身份认证
- 402	Payment Required	保留，将来使用
- 403	Forbidden	服务器理解请求客户端的请求，但是拒绝执行此请求
- 404	Not Found	服务器无法根据客户端的请求找到资源（网页）。通过此代码，网站设计人员可设置"您所请求的资源无法找到"的个性页面
- 405	Method Not Allowed	客户端请求中的方法被禁止
- 406	Not Acceptable	服务器无法根据客户端请求的内容特性完成请求
- 407	Proxy Authentication Required	请求要求代理的身份认证，与401类似，但请求者应当使用代理进行授权
- 408	Request Time-out	服务器等待客户端发送的请求时间过长，超时
- 409	Conflict	服务器完成客户端的 PUT 请求时可能返回此代码，服务器处理请求时发生了冲突
- 410	Gone	客户端请求的资源已经不存在。410不同于404，如果资源以前有现在被永久删除了可使用410代码，网站设计人员可通过301代码指定资源的新位置
- 411	Length Required	服务器无法处理客户端发送的不带Content-Length的请求信息
- 412	Precondition Failed	客户端请求信息的先决条件错误
- 413	Request Entity Too Large	由于请求的实体过大，服务器无法处理，因此拒绝请求。为防止客户端的连续请求，服务器可能会关闭连接。如果只是服务器暂时无法- 处理，则会包含一个Retry-After的响应信息
- 414	Request-URI Too Large	请求的URI过长（URI通常为网址），服务器无法处理
- 415	Unsupported Media Type	服务器无法处理请求附带的媒体格式
- 416	Requested range not satisfiable	客户端请求的范围无效
- 417	Expectation Failed	服务器无法满足Expect的请求头信息
##### 5xx	服务器错误，服务器在处理请求的过程中发生了错误
- 500	Internal Server Error	服务器内部错误，无法完成请求
- 501	Not Implemented	服务器不支持请求的功能，无法完成请求
- 502	Bad Gateway	作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应
- 503	Service Unavailable	由于超载或系统维护，服务器暂时的无法处理客户端的请求。延时的长度可包含在服务器的Retry-After头信息中
- 504	Gateway Time-out	充当网关或代理的服务器，未及时从远端服务器获取请求
- 505	HTTP Version not supported	服务器不支持请求的HTTP协议的版本，无法完成处理
#### 常见的HTTP状态码
- 200-请求成功
- 301-资源（网页等）被永久转移到其他URL
- 404-请求的资源（网页等）不存在
- 500 - 内部服务器错误



# React/Vue

## 1. 提交一个渲染年月日 时间实时更新 的界面
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>当前时间</title>
    <script type="text/javascript" src="js/vue.js"></script>
    <style>
        span {
            display: block;
            width: 300px;
            height: 50px;
            background-color: rgb(241, 154, 169);
            color: white;
            line-height: 50px;
            text-align: center;
            border-radius: 25px;
            margin: auto;
        }
    </style>
</head>

<body>
    <div id="root">
        <span>{{nowDateTime}}</span>
    </div>
    <script>
        new Vue({
            el: '#root',
            data: {
                nowDateTime: '', //当前日期时间
                newTimer: ''
            },
            methods: {
                getTime() {
                    let yy = new Date().getFullYear();
                    let mm = new Date().getMonth() + 1;
                    let dd = new Date().getDate();
                    let hh = new Date().getHours() < 10 ? '0' + new Date().getHours() : new Date().getHours();
                    let mf = new Date().getMinutes() < 10 ? '0' + new Date().getMinutes() : new Date().getMinutes();
                    let ss = new Date().getSeconds() < 10 ? '0' + new Date().getSeconds() : new Date().getSeconds();
                    this.nowDateTime = yy + '年 ' + mm + '月' + dd + '日 ' + hh + ':' + mf + ':' + ss;
                }
            },
            mounted() {
                this.getTime()
                clearInterval(this.newTimer)
                this.newTimer = setInterval(this.getTime, 500)
            },
            beforeDestory() {
                clearInterval(this.newTimer)
            }
        })
    </script>
</body>

</html>
```
## 2.实现按钮在登录与注册之间的相互切换，且渲染不同的标题。

在未登录时：标题显示Please sign up. 下面按钮显示login

点击按钮实现登录，标题切换为Welcome back!

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script type="text/javascript" src="js/vue.js"></script>
    <style>
        .box {
            width: 350px;
            height: 300px;
            text-align: center;
            margin: auto;
            background: linear-gradient(90deg, pink, skyblue);
            border: black 3px solid;
            padding-top: 10px;
        }
        
        h2 {
            display: block;
            height: 50px;
        }
        
        .putin {
            width: 350px;
            height: 40px;
            margin: 10px 0;
        }
        
        .putin label {
            display: inline-block;
            width: 100px;
            margin-right: 10px;
            text-align: right;
            font-weight: 700;
        }
        
        .putin input {
            margin-right: 10px;
            width: 200px;
            height: 20px;
        }
        
        .login {
            margin: 20px;
            width: 70px;
            height: 40px;
            font-size: 16px;
            font-weight: 700;
            background-color: rgb(242, 121, 121);
        }
        
        .box1 {
            width: 300px;
            height: 100px;
            text-align: center;
            margin: auto;
            background: linear-gradient(90deg, pink, skyblue);
            border: black 3px solid;
            padding-top: 10px;
        }
        
        .box1 .after {
            margin: auto;
            line-height: 100px;
        }
    </style>
</head>

<body>
    <div id="app">
        <div class="box" v-if="isUser">
            <h2>Please sign up.</h2>
            <div class="putin">
                <label for="username">Account</label>
                <input type="text" id="username" placeholder="account" key="username"></input>
            </div>
            <div class="putin">
                <label for="psw">Password</label>
                <input type="password" id="psw" placeholder="password" key="psw"></input>
            </div>
            <button class="login" v-on:click="change">Login</button>
        </div>

        <div class="box1" v-else>
            <h2 class="after">Welcome back!</h2>
        </div>
    </div>
</body>
<script>
    const app = new Vue({
        el: '#app',
        data: {
            isUser: true
        },
        methods: {
            change() {
                this.isUser = !this.isUser
            }
        }
    })
</script>

</html>
```


# 算法题

这周都写了哪些算法题呢？

搜索旋转排序数组 I、II，旋转图像，矩阵置零
