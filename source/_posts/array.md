---
title: 数组的常用方法
date: 2021-09-15 15:44:13
tags:
image: './image/seashell.jpg'
---

# JavaScript Array(数组) 对象
数组对象的作用是：使用单独的变量名来存储一系列的值，具有三个属性：
* constructor：返回创建数组对象的原型函数
* length：设置或返回数组元素的个数
* prototype：允许你向数组对象添加属性或方法

# 常用方法
## <font color="skyblue">concat</font>
**连接两个或更多的数组，并返回结果**

示例：
```
var hege = ["Cecilie", "Lone"];
var stale = ["Emil", "Tobias", "Linus"];
var kai = ["Robin"];
var children = hege.concat(stale,kai);
```
输出结果：
` Cecilie,Lone,Emil,Tobias,Linus,Robin `

## <font color="skyblue">copyWithin</font>
**从数组的指定位置拷贝元素到数组的另一个指定位置中**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.copyWithin(2, 0);
```
输出结果：
` Banana,Orange,Banana,Orange `

## <font color="skyblue">entries</font>
**返回数组的可迭代对象**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.entries();
```
输出结果：
``` 
[0, "Banana"]
[1, "Orange"]
[2, "Apple"]
[3, "Mango"] 
```

## <font color="skyblue">every</font>
**检测数值元素的每个元素是否都符合条件**

示例：
```
var ages = [32, 33, 16, 40];

function checkAdult(age) {
    return age >= 18;
}

function myFunction() {
    document.getElementById("demo").innerHTML = ages.every(checkAdult);
}
```
输出结果：
``` 
false
```

## <font color="skyblue">fill</font>
**使用一个固定值来填充数组**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.fill("kk");
```
输出结果：
``` 
kk,kk,kk,kk
```

## <font color="skyblue">filter</font>
**检测数值元素，并返回符合条件所有元素的数组**

示例：
```
var ages = [32, 33, 16, 40];

function checkAdult(age) {
    return age >= 18;
}

function myFunction() {
    document.getElementById("demo").innerHTML = ages.filter(checkAdult);
}
```
输出结果：
``` 
32,33,40
```

## <font color="skyblue">find</font>
**返回符合传入测试（函数）条件的数组元素**

示例：
```
var ages = [3, 10, 18, 20];
 
function checkAdult(age) {
    return age >= 18;
}
 
function myFunction() {
    document.getElementById("demo").innerHTML = ages.find(checkAdult);
}
```
输出结果：
``` 
18
```

## <font color="skyblue">findIndex</font>
**返回符合传入测试（函数）条件的数组元素索引**

示例：
```
var ages = [3, 10, 18, 20];
 
function checkAdult(age) {
    return age >= 18;
}
 
function myFunction() {
    document.getElementById("demo").innerHTML = ages.findIndex(checkAdult);
}
```
输出结果：
``` 
2
```

## <font color="skyblue">forEach</font>
**数组每个元素都执行一次回调函数**

示例：
```
<button onclick="numbers.forEach(myFunction)">点我</button>
<p id="demo"></p>
 
<script>
demoP = document.getElementById("demo");
var numbers = [4, 9, 16, 25];
 
function myFunction(item, index) {
    demoP.innerHTML = demoP.innerHTML + "index[" + index + "]: " + item + "<br>"; 
}
</script>
```
输出结果：
``` 
index[0]: 4
index[1]: 9
index[2]: 16
index[3]: 25
```

## <font color="skyblue">from</font>
**通过给定的对象中创建一个数组**

示例：
```
var myArr = Array.from("kk");
```
输出结果：
``` 
['kk']
```

## <font color="skyblue">includes</font>
**判断一个数组是否包含一个指定的值**

示例：
```
let site = ['runoob', 'google', 'taobao'];
 
site.includes('runoob'); 
// true 
 
site.includes('baidu'); 
// false
```
输出结果：
``` 
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

## <font color="skyblue">indexOf</font>
**搜索数组中的元素，并返回它所在的位置**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
```
输出结果：
``` 
2
```

## <font color="skyblue">isArray</font>
**判断对象是否为数组**

示例：
```
function myFunction() {
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var x = document.getElementById("demo");
    x.innerHTML = Array.isArray(fruits);
}
```
输出结果：
``` 
true/false
```

## <font color="skyblue">join</font>
**把数组的所有元素放入一个字符串**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var energy = fruits.join();
```
输出结果：
``` 
Banana,Orange,Apple,Mango
```

## <font color="skyblue">keys</font>
**返回数组的可迭代对象，包含原始数组的键(key)**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.keys();
```

## <font color="skyblue">lastIndexOf</font>
**搜索数组中的元素，并返回它最后出现的位置**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.lastIndexOf("Apple");
```
输出结果：
``` 
2
```

## <font color="skyblue">map</font>
**通过指定函数处理数组的每个元素，并返回处理后的数组**

示例：
```
var numbers = [4, 9, 16, 25];

function myFunction() {
    x = document.getElementById("demo")
    x.innerHTML = numbers.map(Math.sqrt);
}
```
输出结果：
``` 
2,3,4,5
```

## <font color="skyblue">pop</font>
**删除数组的最后一个元素并返回删除的元素**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop();
```
输出结果：
``` 
Banana,Orange,Apple
```

## <font color="skyblue">push</font>
**向数组的末尾添加一个或更多元素，并返回新的长度**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi")
```
输出结果：
``` 
Banana,Orange,Apple,Mango,Kiwi
```

## <font color="skyblue">reduce</font>
**将数组元素计算为一个值（从左到右）**

示例：
```
var numbers = [65, 44, 12, 4];
 
function getSum(total, num) {
    return total + num;
}
function myFunction(item) {
    document.getElementById("demo").innerHTML = numbers.reduce(getSum);
}
```
输出结果：
``` 
125
```

## <font color="skyblue">reduceRight</font>
**将数组元素计算为一个值（从右到左）**

示例：
```
var numbers = [65, 44, 12, 4];
 
function getSum(total, num) {
    return total + num;
}
function myFunction(item) {
    document.getElementById("demo").innerHTML = numbers.reduceRight(getSum);
}
```
输出结果：
``` 
125
```

## <font color="skyblue">reverse</font>
**反转数组的元素顺序**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.reverse();
```
输出结果：
``` 
Mango,Apple,Orange,Banana
```

## <font color="skyblue">shift</font>
**删除并返回数组的第一个元素**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift()
```
输出结果：
``` 
Orange,Apple,Mango
```

## <font color="skyblue">slice</font>
**选取数组的一部分，并返回一个新数组**

示例：
```
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1,3);
```
输出结果：
``` 
Orange,Lemon
```

## <font color="skyblue">some</font>
**检测数组元素中是否有元素符合指定条件**

示例：
```
var ages = [3, 10, 18, 20];

function checkAdult(age) {
    return age >= 18;
}

function myFunction() {
    document.getElementById("demo").innerHTML = ages.some(checkAdult);
}
```
输出结果：
``` 
true
```

## <font color="skyblue">sort</font>
**对数组的元素进行排序**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
```
输出结果：
``` 
Apple,Banana,Mango,Orange
```

## <font color="skyblue">splice</font>
**从数组中添加或删除元素**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2,0,"Lemon","Kiwi");
```
输出结果：
``` 
Banana,Orange,Lemon,Kiwi,Apple,Mango
```

## <font color="skyblue">toString</font>
**把数组转换为字符串，并返回结果**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.toString();
```
输出结果：
``` 
Banana,Orange,Apple,Mango
```

## <font color="skyblue">unshift</font>
**向数组的开头添加一个或更多元素，并返回新的长度**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon","Pineapple");
```
输出结果：
``` 
Lemon,Pineapple,Banana,Orange,Apple,Mango
```

## <font color="skyblue">valueOf</font>
**返回数组对象的原始值**

示例：
```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var v=fruits.valueOf();
```
输出结果：
``` 
Banana,Orange,Apple,Mango
```