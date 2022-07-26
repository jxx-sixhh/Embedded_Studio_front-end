# 下周计划
###学习react 复习一些旧知识
# 复习
## 1. var let const 的区别
1.var声明的范围为函数作用域 let和const声明的为块级作用域
2.var有变量提升 let和const没有
3.var允许重复声明同一个变量，但是let和const不可以
4.在全局作用域下可以通过window.访问var声明的变量 但是let和const不可以
5.var和let声明的变量可以不用初始化，但是const声明的变量必须要初始化
## 2. ajax
### 2.1 Ajax是啥？它的优点和缺点是什么？
Q1:依赖浏览器提供的 XMLHttpRequest 对象发出 HTTP 请求和接收 HTTP响应；实现了在页面不刷新的情况下和服务器进行数据交互。
Q2:优点:1.实现了异步交互，提高了用户体验
2.无需加载整个网页，只需要与服务器进行少量的数据交换，就能够实现对网页中一些数据的部分更新，从而减少了带宽的占用
3. AJAX是在客户端运行的，它承载了一部分本来由服务器承担的工作，减少了大用户量下的服务器负载。
缺点:1.安全性问题，大量的使用ajax暴露了服务器交互的细节
2.不容易调试
3.对搜索引擎的支持比较弱
### 2.2 如何创建一个Ajax？
    const xhr = new XMLHttpRequest();
    xhr.open("方式（get or post）","端口");
    xhr.send();
    xhr.onreadystatechange = function(){
    if (xhr.readyState === 4) {
        if (xhr.status >= 200 && xhr.status <= 300) {
            result.innerHTML = xhr.response;
        }
    }
### 2.3 请求http://www.liulongbin.top:3006/api/getbooks 并用表格来显示请求结果
    import React, { useState } from 'react';
    import './App.css';
    const App = () => {
        const [dataList, setData] = useState([]);
        fetch('http://www.liulongbin.top:3006/api/getbooks')
            .then((response) => response.json())
            .then((data) => {
                const newdata = [...data.data];
                setData(newdata);
            })
            .catch((e) => console.log('错误:', e));
        // console.log(dataList);
        const list = dataList.map((item) => (
            <tr key={item.id}>
                <td>{item.bookname}</td>
                <td>{item.author}</td>
                <td>{item.publisher}</td>
            </tr>
        ));
        return (
            <table className='t'>
                <thead>
                    <tr>
                        <th>书名</th>
                        <th>作者</th>
                        <th>出版社</th>
                    </tr>
                </thead>
                <tbody>{list}</tbody>
            </table>
        );
    };
    export default App;
### http状态码
1.200 : 成功，表示访问成功，正常状态。

2.301 : 永久移动，表示本网页已经永久性的移动到一个新的地址，在客户端自动将请求地址改为服务器返回的新地址。

3.302 : 临时重定向，表示网页暂时性的转移到一的新的地址，客户端在以后可以继续向本地址发起请求。

4.303 : 表示必须临时重定向，并且必须使用GET方式请求。

5.304 : 重定向至浏览器本身，当浏览器多次发起同一请求，且内容未更改时，使用浏览器缓存，这样可以减少网络开销。

6.401 : 表示协议格式出错，可能是此IP地址被禁止访问该资源，与403类似。

7.403 : 表示没有权限，服务器拒绝访问请求。

8.404 : 这是最常见的错误，表示找不到系统资源，但是只是暂时性地。

9.500 : 表示服务器程序错误，一个通用的错误信息。

10.503 : 表示服务器繁忙，或者服务器负载，通常这只是一个临时状态。
# react
## 1渲染时间
    <!DOCTYPE html>
    <html lang="zh-Ch">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
        <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        </head>
    <body>
        <div id="root"></div>
        <script type="text/babel">
            const root = ReactDOM.createRoot(document.getElementById('root'));
            const ShowTime = () => {
                const newtime = new Date();
                const Time =  <h2>{newtime.toLocaleTimeString()}</h2>
                root.render(Time);
            }
            setInterval(()=>{ShowTime()},1000);
        </script>
    </body>
## 切换状态
    //组件长这个样子
    import React, { useState } from 'react';
    const App = () => {
        const [judeglog, setJudeglog] = useState(false);
        const Den = () => {
            return (
                <>
                    <h1>Please sign up!</h1>
                    <button onClick={onChange}>login</button>
                </>
            );
        };
        const Tui = () => {
            return (
                <>
                    <h1>Welecom back!</h1>
                    <button onClick={onChange}>logout</button>
                </>
            );
        };
        const onChange = () => {
            setJudeglog((preState) => !preState);
        };
        return <div>{judeglog ? <Den /> : <Tui />}</div>;
    };
    export default App;

