#  下周学习计划
1.通过学习react视频 写里面的案例
#  解释JS中的函数提升
1.以**函数声明**的方式
    console.log(add(1,2));//5
    function add (a,b){
    return a+b;
    }
提升函数的整体 覆盖之前的相同函数名的函数声明
例如
    function play (){
        console.log(111)
    }
    play();//222
    function play (){
        console.log(222)
    }
    play();//222
2.以**函数表达式**的方式
    var game=function (){
      console.log('玩英雄联盟')
    }
    game()//玩英雄联盟
    var game=function (){
      console.log('玩CSGO')
    }
    game()//玩CSGO
**过程
    var game
    var game
    game=function (){
      console.log('玩英雄联盟')
    }
    game()
    game=function (){
      console.log('玩CSGO')
    }
    game()**
*特殊情况*
    console.log(drink)
    function drink(){
      console.log('酒')
    }
    var drink='饮料'
**过程
    var drink=function drink(){
      console.log('酒')
    };
    console.log(drink);//*f()*
    var drink='饮料';**
# react多级组件
    <!DOCTYPE html>
    <html lang="zh-Ch">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
        <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        </head>
    <body>
        <div id="root"></div>
        <script type="text/babel">
            const Alt = (props)=>{
                // console.log(props);
                const list = props.data.map(item => <li key={item.id}>姓名:{item.name} 年龄:{item.age} 性别:{item.gender}</li>)
                return <ul>{list}</ul>
            }
            const App = () => {
            const data = [
                {
                    id:'01',
                    name: 'xiaotian',
                    age: 18,
                    gender: '男',
                },
                {
                    id:'02',
                    name: 'xiaomei',
                    age: 19,
                    gender: '女',
                },
                {
                    id:'03',
                    name: 'xiaolu',
                    age: 17,
                    gender: '男',
                },
            ];
            return <Alt data={data}/>
        };
            const root = ReactDOM.createRoot(document.getElementById('root'));
            root.render(<App/>);
        </script>
    </body>



