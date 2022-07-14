#  下周计划
## 1.总结Set的属性和方法，方法用代码来解释
1.Set的属性Set.prototype.size 返回的是Set对象中元素的个数
2.Set的方法
```
const myset = new Set();
myset.add(1);
myset.add(2);
myset.add(3);
//add() 方法用来向一个 Set 对象的末尾添加一个指定的值。
//Set.prototype.add()
for(const item of myset){
    console.log(item);
}//1,2,3
//clear() 方法用来清空一个 Set 对象中的所有元素。
//Set.prototype.clear()
myset.clear();
console.log(myset.size===0)//true
//delete() 方法可以从一个 Set 对象中删除指定的元素。
//Set.prototype.delete()
myset.delete(1);
for(const item of myset){
    console.log(item);
}//2,3
//has() 方法返回一个布尔值来指示对应的值value是否存在Set对象中。
//Set.prototype.has()
console.log(myset.has(1))//true
console.log(myset.has(4))//false
//values() 方法按照元素插入顺序返回一个具有 Set 对象每个元素值的全新 Iterator 对象。
//Set.prototype.values()
const iterator1 = myset.values();
console.log(iterator1.next().value);//1
console.log(iterator1.next().value);//2
console.log(iterator1.next().value);//3
//forEach 方法会根据集合中元素的插入顺序，依次执行提供的回调函数。
//Set.prototype.forEach() mySet.forEach(callback[, thisArg])
//回调函数callback接收三个参数 currentValue  currentKey Set(可选)
myset.forEach(currentValue,currentKey){
   console.log(currentValue,currentKey);
}//1 1 2 2 3 3
```
## 总结Map的属性和方法，方法用代码来解释
1. Map的属性 Map.prototype.size 返回一个Map对象的成员数量。
2. Map的方法
```
const m = new Map();
//set() 方法为 Map 对象添加或更新一个指定了键（key）和值（value）的（新）键值对。
//Map.prototype.set();
m.set(1,11);
m.set(2,22);
//has()方法返回一个bool值，用来表明map 中是否存在指定元素.
//Map.prototype.has();
console.log(m.has(1))//true;
//keys() 返回一个引用的 Iterator 对象。它包含按照顺序插入 Map 对象中每个元素的key值
//Map.prototype.keys();
const keysIterator = m.keys();
conosle.log(keysIterator.next().value);//1
//values() 方法返回一个新的Iterator对象。它包含按顺序插入Map对象中每个元素的value值。
//Map.prototype.values();
const valuesIterator = m.values();
console.log(valuesIterator.next().value)//11
//get() 方法返回某个 Map 对象中的一个指定元素。通过已有的键来查找值
//Map.prototype.get();
console.log(m.get(2))//22
//forEach() 方法按照插入顺序依次对 Map 中每个键/值对执行一次给定的函数
//Map.prototype.forEach(callback)回调函数参数 value key Map对象
m.forEach(value,key,m){
console(m[key]===value)//m[1]===11 m[2]===22
}
//entries() 方法返回一个新的包含 [key, value] 对的 Iterator 对象，返回的迭代器的迭代顺序与 Map 对象的插入顺序相同。
//Map.prototype.entries()
const iterator = m.entries;
console.log([...iterator])//[[1,11],[2,22]];
//delete() 方法用于移除 Map 对象中指定的元素。
//Map.prototype.delete()
//console.log(m);//Map{1=>11,2=>22}
m.delete(1);
console.log(m);//Map{2=>22}
//clear()方法会移除Map对象中的所有元素。
//Map.prototype.clear()
m.clear();
console.log(m.size===0)//true
```
# 3.两个数组点的交集
```
//Set
var intersection = function(nums1, nums2) {
    return [...new Set(nums1)].filter(item => new Set(nums2).has(item));
};
//Map
var intersection = function(nums1, nums2) {
    const m = new Map();
    const res = [];
    nums1.forEach(item => {
        if(!m.has(item)){
            m.set(item,true);
        }
    })
    nums2.forEach(item => {
        if(m.get(item)){
            res.push(item);
            m.delete(item);
        }
    })
    return res;
};
```
# 复习数组的属性和方法，方法用代码解释
```
const arr = [1,2,3,4,5,6,4,3,2];
const arr1 = [11,22];
//属性：array.length
cnosole.log(arr.length);//9
//方法
//concat()拼接数组
console.log(arr.concat(arr1))//[1,2,3,4,5,6,4,3,2,11,22];
//every()检查每一个元素是否符合条件，返回boolean值
console.log(arr.every(item => item<30))//true
//filiter()过滤出满足的元素形成一个新的数组并返回
console.log(arr.filiter(item => item < 3))//[1,2,2];
//find()找到满足的第一个元素
console.log(arr.find(item => item >11))//22
///findindex()找到数组中第一个满足条件的元素并返回索引，没有找到返回-1
console.log(arr.findindex(item => item===1));//0
//forEach()//遍历所有的元素并执行回调函数
arr.forEach(item => {
    if(item>6){
    console.log(item)
}
}//11 22
)
//includes()判断给定的数组是否包含一个指定的值 返回boolean
console.log(arr.includes(-1))//false
//indexOf()返回给定元素第一次出现的索引 没有就返回-1
console.log(arr.indexOf(2))//1
//lastIndexOf()返回给定元素倒着第一次出现的索引 没有就返回-1
console.log(arr.indexOf(2))//8
//Array.isArray()//用来判断传递的值是否为一个数组
console.log(Array.isArray(arr))//true
//join()将一个数组转化为字符串，可以传递每个元素间的分割符号
console.log(arr.join(''))//1234564321122(字符串)
//map()通过原数组创建一个新数组 可以通过回调函数改变原数组传入的值后再传入新数组
console(arr.map(item => item*2)//[2,4,6,8,10,12,6,4]
//pop()移除数组的最后一个元素
console.log(arr.pop())//[1,2,3,4,5,6,4,3];
//push()向数组的最后一位添加一个新的元素
console.log(arr.push(222))//[1,2,3,4,5,6,4,3,222];
//reverse()数组反转 改变的是原数组
console.log(arr)//[3,4,6,5,4,3,2,1]
//shift()删除数组的第一个元素
console.log(arr.shift())//[2,3,4,5,6,4,3,2]
//sort()排序函数 但是需要写一个回调函数
arr.sort((a,b)=> a-b);//升序
console.log(arr)//[1,2,2,3,3,4,4,5,6]
//toString()返回一个字符串，表示指定的数组以及其元素
const array1 = [1, 2, 'a', '1a'];
console.log(array1.toString());// expected output: "1,2,a,1a"
//unshift()将多个元素添加到数组的开头并且返回新数组的长度
const array1 = [1, 2, 3];
console.log(array1.unshift(4, 5));//5
console.log(array1)//[4,5,1,2,3]
//values()返回一个 Array Iterator对象，该对象包括数组每个索引的值
const itertorArray = arr.values();
for(const value of itertorArray){
 console.log(value)//1,2,3,4,5,6,4,3,2
}
//some()测试数组是否有至少有一个元素通过了测试返回值是一个boolean
console.log(arr.some(item = item%2===0))//true
//of()创建一个具有可变参数的新数组实例
Array.of(4);//[4];

```
