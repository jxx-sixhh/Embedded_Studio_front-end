//数组操作
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //添加
        var array1 = [1,2,3,4,5,6];
        console.log('添加前:',array1);
        var num1 = array1.unshift(99);
        var num2 = array1.push(100);
        console.log('添加后:',num1,num2,array1);
        //
        //删除
        var array2 = [1,2,3,4,5,6];
        var array22 =[];//数组为空的情况
        console.log('删除前:',array2);
        var num3 = array2.shift();
        var num4 = array2.pop();
        console.log('删除后:',num3,num4,array2);
        console.log(array22.shift());
        console.log(array22.pop());
        //过滤 array.filter()不会修改原数组 而是返回一个新的数组 需要用一个变量去接收
        console.log('过滤');
        var array3 = [1,2,3,4,5,6,23,5,23,1,66];
        var array33 = array3.filter((item,index,data)=>{
            return item > 5;
        })
        // console.log(array3); 打印结果为[1,2,3,4,5,6,23,5,23,1,66] 没有改变原数组
        console.log(array33);





        //sort()排序
        var arr = [2,9,5,4,7,1,-33,48,32];
        arr.sort((a,b)=>{
            return a-b;
        })
        console.log('sort()排序:',arr);
        //冒泡排序
        var arr1 = [2,9,5,6,11,-11,-33,48,32];
        for(var i = 0;i<arr1.length-1;i++){
            for(var j = 0;j<arr1.length-i-1;j++){
                if(arr1[j]>arr1[j+1]){
                    var temp = arr1[j];
                    arr1[j] = arr1[j+1];
                    arr1[j+1] = temp;
                }
            }
        }
        console.log('冒泡排序:',arr1);
        //选择排序
        var arr2 = [2,9,5,6,11,-11,-33,48,32];
        for(var i=0;i<arr2.length;i++){
            for(var j=i+1;j<arr2.length;j++){
                //如果第一个比第二个大，就交换他们两个位置
                if(arr2[i]>arr2[j]){
                    var temp = arr2[i];
                    arr2[i] = arr2[j];
                    arr2[j] = temp;
                }
            }
        }
        console.log('选择排序:',arr2); 
        //插入排序
        var arr3 = [2,9,5,6,11,-11,-33,48,32,999,-934];
        var preIndex, current;
        for(var i=1;i<arr3.length;i++){
            preIndex = i-1;
            current = arr3[i];
            while(preIndex>=0 && arr3[preIndex]>current) {
                arr3[preIndex+1] = arr3[preIndex];
                preIndex--;
            }
            arr3[preIndex+1] = current;
        }
        console.log('插入排序',arr3);
        //快速排序
        var arr3 = [2,9,5,6,11,-11,-33,48,32,999,-934];
        quickSort(0,arr3.length-1,arr3);
        function quickSort(left,right,arr){
            var k = arr[parseInt((left+right)/2)];
            var l = left;
            var r = right;
            while(l<=r){
                while(arr[l]<k){
                    l++;
                }
                while(arr[r]>k){
                    r--;
                }
                if(l<=r){
                    var temp = arr[l];
                    arr[l] = arr[r];
                    arr[r] = temp;
                    l++;
                    r--;
                }
            }
            if(l<=right){
                quickSort(l,right,arr);
            }
            if(r>=left){
                quickSort(left,r,arr);
            }
        }
        console.log('快速排序:',arr3);
    </script>
</body>
</html>
<!-- 
    数组添加元素
    1.array.unshift();将元素增加到最前 返回值为新数组的长度
    2.array.push();将元素增加到最后 返回值为新数组的长度
    数组删除元素 
    1.array.pop();删除元素第一项 返回删除的值 如果数组为空返回undefined
    2.array.shift();删除元素最后一项 返回删除的值 如果数组为空返回undefined
    数组排序
    1.sort()排序 2.选择排序 3.冒泡排序 4.插入排序 5.快速排序
-->
//数组去重
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //第一种
        var arr = [2,4,5,3,4,2,6,7,3,2];
        function qucong(arr) {
            newArray = [];
            for(var i = 0;i<arr.length;i++)
            {
                if(newArray.indexOf(arr[i]) === -1)
                {
                    newArray.push(arr[i]);
                }
            }
            return newArray;
        }
        console.log(qucong(arr));
        //第二种
        var arr1 = [2,4,5,3,4,2,6,7,3,2];
        function qucong2(arr) {
            var obj={}
            var newArry1=[]
            for (let i = 0; i < arr.length; i++) {
                if (!obj[arr[i]]) {
                    obj[arr[i]] = 1
                    newArry1.push(arr[i])
                }   
            }
            return newArry1;
        }
        console.log(qucong2(arr1));
        // var obj2 = {};
        // obj2[0]=1;
        // console.log(obj2);
        //第三种 includes() 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回 false。
        var arr2 = [2,4,5,3,4,2,6,7,3,2];
        function qucong3(arr){
            var newArry2 = [];
            for(var i = 0;i<arr2.length;i++){
                if(!newArry2.includes(arr2[i])){//如果 (! newArry2.includes(arr2[i]))判断为真 则表示没有该元素
                    newArry2.push(arr2[i]);
                }
            }
            return newArry2;
        }
        console.log(qucong3(arr2));
        // 第四种 Set数据结构，它类似于数组，其成员的值都是唯一的
        var arr3 = [2,4,5,3,4,2,6,7,3,2];
        function qucong4(arr) {
            return Array.from(new Set(arr)); //利用Array.from将Set结构转换成数组
        }
        console.log(qucong4(arr3));
        //第五种 filter 数组去重
        var arr4 = [2,4,5,3,4,2,6,7,3,2];
        var arr44 = arr4.filter((item,index,data)=>{
            var newIndex = data.indexOf(item); //data.indexOf(item)拿到该元素的第一次出现的索引
            return newIndex === index;//第一次出现的索引newIndex 与当前索引比较 如果相同就返回true（newIndex === index）反之就把它过滤掉
        }); 
        console.log(arr44);
        //第六种
        var arr5 = [2,4,5,3,4,2,6,7,3,2];
        function qucong5(arr) {
            var newArr = []
            newArr = arr.filter(function (item) {
                return newArr.includes(item) ? '' : newArr.push(item)//如果newArr.includes(item)返回真 说明已经在数组arr5里面已经存在了item 就返回‘’;反之将值push到新数组里面
            })
            return newArr
        }
        console.log(qucong5(arr5));
        //第七种
        var arr6 = [2,4,5,3,4,2,6,7,3,2];
        function qucong6(arr) {
            var res = [];
            for (var i = 0; i < arr.length; i++) {
                res.lastIndexOf(arr[i]) !== -1 ? '' : res.push(arr[i]);//lastIndexOf() 方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 fromIndex 处开始。
            }
            return res;
        }
        console.log(qucong6(arr6));
        // 结果是[1, 2, 3, 5, 6, 7, 4]


    </script>
</body>
</html>