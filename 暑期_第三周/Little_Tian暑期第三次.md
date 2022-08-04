# 1. 怎么设置执行上下文中的this指向其他对象？
1. call 方法
语法：函数名.call(调用者, 参数1, …)
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者
2. apply方法
语法：函数名.apply(调用者, [参数，...])
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者
3. bind方法
语法：函数名.bind(调用者, 参数, …)
作用：函数被借用时，不会立即执行，而是返回一个新的函数。需要自己手动调用新的函数来改变this指向
# 2. 代码中出现相同的变量，JavaScript引擎是如何选择的？
    function bar() {
      console.log(myName)
    }

    function foo() {
      var myName = "test"
      bar()
    }
    var myName = "123"
    foo()
    //“123” 优先选择当前作用域的变量，就近原则。
    
#  react
## 1. 提供两个input框，分别为用户名和密码，在点击登陆时弹出输入的用户名和密码信息
###1.1不受控
    import React, { useState } from 'react';
    import './App.css';
    const App = () => {
        // 1.不受控组件
        const ref1 = React.createRef();
        const ref2 = React.createRef();
        const onChange = (e) => {
            e.preventDefault();
            if (
                ref1.current.value.trim() === '' ||
                ref2.current.value.trim() === ''
            ) {
                return;
            }
            alert(
                '用户名:' + ref1.current.value + ' ' + '密码' + ref2.current.value,
            );
            ref1.current.value = '';
            ref2.current.value = '';
        };
        const check = () => {
            if (ref1.current.value === '' && ref2.current.value === '') {
                return;
            }
        };
        return (
            <form onSubmit={onChange}>
                用户名: <input ref={ref1} type='text' />
                <br />
                密码:
                <input ref={ref2} type='password' />
                <br />
                <button>提交</button>
            </form>
        );
    };
    export default App;
###1.2 受控
//2.受控组件
    import React, { useState } from 'react';
    import './App.css';
    const App = () => {
        const [userName, setUserName] = useState('');
        const [passWord, setPassWorld] = useState('');
        const userNameChangeHandler = (e) => {
            setUserName(e.target.value);
        };
        const passWorldChangeHandler = (e) => {
            setPassWorld(e.target.value);
        };
        const onFormChange = (e) => {
            e.preventDefault();
            if (userName.trim() === '' || passWord.trim() === '') {
                return;
            }
            alert('用户名:' + userName + ' ' + '密码:' + passWord);
        };
        return (
            <form onSubmit={onFormChange}>
                用户名:
                <input
                    type='text'
                    value={userName}
                    onChange={userNameChangeHandler}
                />
                <br />
                密码:
                <input
                    type='password'
                    value={passWord}
                    onChange={passWorldChangeHandler}
                />
                <br />
                <button>提交</button>
            </form>
        );
    };
    export default App;

# 算法题
找出数组的最大公约数 三个数的最大乘积 将找到的值乘以2 找出数组排序后的目标下标
