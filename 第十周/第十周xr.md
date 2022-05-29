# 下周计划
做项目、学数据结构与算法
# 1. 总结Set的属性和方法，方法用代码来解释
1.元素个数
```js
let s = new Set(['喜羊羊','美羊羊','懒羊羊','沸羊羊','喜羊羊']);//Set(4){"喜羊羊","美羊羊","懒羊羊","沸羊羊"}
console.log(s.size);
```

2.添加新元素 add()
```js
s.add('慢羊羊')；
```

3.删除元素 delete()
```js
s.delete('沸羊羊');
```

4.检测元素是否存在 has()
```js
console.log(s.has('美羊羊'))；
```

5.清空
```js
s.clear();
console.log(s)//Set(0){}
```

6.遍历
```js
for(let v of s){
    console.log(v);
}
```

7.数组去重
```js
let arr = [1,1,2,2,3,3,4,5,4];
let res = [...new Set(arr)];
console.log(res);
```

8.取交集
```js
let arr2 = [2,2,3,4,3,6,6,7];
let res = [...new Set(arr)].filter(item => new Set(arr2).has(item));
console.log(res);
```

9.取并集
```js
let union = [...new Set([...arr,...arr2])];
console.log(union);
```

10.差集
```js
let diff = [...new Set(arr).filter(item => !(new Set(arr2).has(item)))];
console.log(diff);
```

# 2. 总结Map的属性和方法，方法用代码来解释
1.set添加元素
```js
let m = new Map();
m.set('name','唔西迪西');
m.set('gender','女');
let key = {
    hobby: 'Sing';
};
m.set(key,['啦啦啦','啊啊啊']);
```

2.size 元素个数
```js
console.log(m.size);//3
```

3.delete 删除
```js
m.delete('gender');
```

4.has检测元素是否存在
```js
console.log(m.has('name'));//true
```

5.get 获取
```js
console.log(m.get('name'));
console.log(m.get(key));
```

6.遍历
```js
for(let v of m){
    console.log(v);
}
```

7.clear 清空
```js
m.clear();
```

# 3. 分别用set和map来解决这道题

[leetcode349. 两个数组的交集] (https://leetcode.cn/problems/intersection-of-two-arrays/)

1.set
```js
var intersection = function(nums1, nums2) {
    let res = [...new Set(nums1)].filter(item => new Set(nums2).has(item));
    return res;
};
```
2.map
```js
var intersection = function(nums1,nums2){
    const m = new Map();
    nums1.forEach(x =>{
        m.set(x,true);
    });
    const res = [];
    nums2.forEach(x =>{
        if(m.get(x)){
            res.push(x);
            m.delete(x);
        }
    });
    return res;

}
```

# 4. 复习数组的属性和方法，方法用代码来解释
1.concat合并数组
```js
let arr = [1,2,3,4,5];
let arr2 = arr.concat(1,2,3);
console.log(arr2);//1,2,3,4,5,1,2,3
```

2.push 添加到数组尾部，返回值为新数组的长度
```js
arr.push(10,20);
console.log(arr);//1,2,3,4,5,10,20
```

3.pop删除数组最后一项，返回被删除的元素
```js
arr.pop();
console.log(arr);//1,2,3,4,5,10
```

4.shift删除第一项，返回被删除的元素
```js
arr.shift();
console.log(arr);//2,3,4,5,10
```

5.unshift 在数组头部添加元素，返回新数组长度
```js
arr.unshift(1);
console.log(arr);//1,2,3,4,5,10
```

6.splice删除，替换，返回被替换掉的元素组成的数组
```js
let arr1 = arr.splice(0,3,30);
console.log(arr1);//30,4,5,10
```

7.indexOf 从前向后查找数组中是否有某一项，有返回下标，无返回-1
```js
let index = arr.indexOf(1,4);
console.log(index);//1
```
8.lastIndexOf 从后向前查找元素位置
```js
var index1 = arr.lastIndexOf(5);
console.log(index1);//2
```

9.slice复制数组的数据
```js
let arr3 = arr.slice(0,2);
console.log(arr3);
```

10.reverse 倒序数组
```js
let arr4 = arr.reverse();
console.log(arr4);//10,5,4,30
```

11.join将数组转换成用规定字符分割的字符串
```js
let arr5 = arr.join('+');
console.log(arr5);//30+4+5+10
```

12.filter筛选
```js
let arr = [1,2,3,4,5,6,7,8,9];
let arr1 = arr.filter(item => {
    if(item > 5){
        return item > 5;
    }
})
console.log(arr1);//6,7,8,9
```

13.flat 将多维数组转化为低维数组
```js
const arr = [1,2,3,4,[5,6]];
console.log(arr.flat());//1,2,3,4,5,6

const arr1 = [1,2,3,[4,5,[6,7,8]]];
console.log(arr.flat(2));//1,2,3,4,5,6,7,8
```

14.map
```js
const arr = [1,2,3,4];
const res = arr.map(item => item * 10);
console.log(res);//10,20,30,40
```

15.flatMap
```js
const arr = [1,2,3,4];
const res = arr.flatMap(item => [item * 10]);
console.log(res);//10,20,30,40
```

16.forEach
```js
const arr = ['a', 'b', 'c'];
arr.forEach(element => console.log(element));
```



