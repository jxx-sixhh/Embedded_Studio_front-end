# 1. 下周计划

继续学vue+刷力扣

# 2. 复习

## 1.解释 JS 中的函数提升

只有函数声明形式才能被提升，函数提升就是将整个函数声明代码块提升到当前作用域的顶部，所有使用function声明的函数，都会整体提升，只要在当前的作用域声明了函数，在任何位置都可以用

# 3. react

实现一个 多级组件 并且实现props数据的向下传递 (内容任意)


父组件

```html
<template>
  <div id="app">
    <HelloWorld :msg="text"></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  data() {
    return {
      text:'我是父组件向下传递的信息'
    }
  },
  components: {
    HelloWorld
  }
}
</script>
```

子组件

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: ['msg'],
  data () {
    return {
      message:"hello world"
    }
  },
  mounted(){
  	console.log(this.msg)
  }
}
</script>
```
