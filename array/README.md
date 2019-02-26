<h2 id="es5Aarray">Array</h2>

<h3>基础</h3>
* 数组：一系列数据的集合

一.**创建方式**

```javascript
	//字面量
	var arr = [];
	var arr = [1,2,3];
	//构造函数创建方式
	var arr = new Array();
	var arr = new Array (10,20,30)
```
二.**基础操作**

1.**访问与写入**

```javascript
	var arr = ['html5','css3','javascript'];
	//索引（下标）：从0开始
	//访问
	arr[0]; //=> 'html5'
	arr[2]; //=> 'javascript'
	
	//写入
	arr[3] = 'web前端';
	console.log(arr[3])//['html5','css3','javascript','web前端']
```
2.**加、删、改**
- 加
```javascript
arr.unshift() // 在第一个增加
arr.push() // 在最后一个加
```
- 删
```javascript
arr.shift() // 删除第一个
arr.pop() // 删除最后一个
```
- 改
```javascript
arr.splice(start从哪里开始,deleteNum删除多少个,items什么项目)
/*
 eg：减arr.splice(2,1)从索引2开始，删除1个
    加arr.splice(2,0,1,2,3)从索引2开始，删除0个，多了1,2,3
    替换arr.splice（3,1,2）先删除再增加
*/
```

<h3>Array方法详解</h3>
1.**forEach()**
- 遍历所有元素，for循环没有太大差别，比for循环方便，但是不能随意退出循环。

```javascript
let personList = [
	{name:'小猪佩奇',level:1},
	{name:'大猪菊花',level:2},
	{name:'小脏菊菊',level:2},
	{name:'小猪佩奇1',level:1},
	{name:'大猪菊花1',level:9},
	{name:'小脏菊菊1',level:9}
]
personList.forEach((item) => {
	if (item.level < 2) {
	  item.Word = item.name + '是我们的高级会员'
	} else {
	  item.Word = item.name + '是我们的普通会员'
	}
})
```

2. **map()**
- 返回每次函数调用的结果，组成一个数组，返回的是一个数量相等的新数组，返回的内容是什么取决于在fn中返回的值

```javascript
// 常用的拼接数据
let str = personList.map((item) => {
  return `<li>${item.Word}</li>`
}).join()
let ul = document.createElement('ul')
ul.innerHTML = str
let box = document.querySelector('.box')
box.appendChild(ul)

// 一般的数据处理
let arr = [1,2,3]
arr.map((item) => {
	return item*2
}) // 2，4，6

arr.map(String) // ['1','2','3']
```

3.**reduce()**

- Array的reduce()把结果继续和序列的下一个元素做累积计算，其效果就是：
[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)

```javascript
var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25

function proudct() {
	return arr.reduce((x,y)=>{return x*y})
}
product([1,2,3,4]) // 24
```

4.**filter()**
- 过滤，指数组filter后，返回过滤后的新数组。

```javascript
// 在一个Array中，删掉偶数，只保留奇数，可以这么写：
var arr = [1, 2, 4, 5, 6, 9, 10, 15];
var r = arr.filter(function (x) {
    return x % 2 !== 0;
});
r; // [1, 5, 9, 15]

//filter()接收的回调函数，其实可以有多个参数。
//回调函数还可以接收另外两个参数，表示元素的位置和数组本身：
var arr = ['A', 'B', 'C'];
var r = arr.filter(function (element, index, self) {
    console.log(element); // 'A', 'B', 'C'
    console.log(index); // 0, 1, 2
    console.log(self); // self就是变量arr
    return true;
});

//利用filter，可以巧妙地去除Array的重复元素：
 arr = ['apple', 'strawberry', 'banana', 'pear', 'apple', 'orange', 'orange', 'strawberry'];
 r = arr.filter(function (element, index, self) {
    return self.indexOf(element) === index;
}); //  ["apple", "strawberry", "banana", "pear", "orange"]

//去除重复元素依靠的是indexOf总是返回第一个元素的位置，后续的重复元素位置与indexOf返回的位置不相等，因此被filter滤掉了。
```
