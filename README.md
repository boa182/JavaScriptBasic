<h1>JavaScript的知识总结以及小案例</h1>
<h2>记得多少写多少 囧</h2>

<h3>数组：一系列数据的集合</h3>

一.**创建方式**

```javascript
	//字面量
	var arr = [];
	var arr = [1,2,3];
	//构造函数创建方式
	var arr = new Array();
	var arr = new Array (10,20,30)
```
二.**数组的操作**

1.**数组的访问与写入**

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

length:表示数组的长度

<h3>JavaScript基础算法：</h3>
1.**数组去重**

```javascript
	var arr =  ['abc','abcd','sss','2','d','t','2','ss','f','22','d'];
	var n = [];
	
	// 方法一：indexOf的方法
	for(var i = 0;i<arr.length;i++){
		if(n.indexOf(arr[i])==-1){
			n.push(arr[i]);
		}
	}
	
	// 方法二：选择排序
	for(var j = 0;j<arr.length;j++){
		for (var y = j+1;y<arr.length;y++){
			if(arr[j]==arr[y]){
				arr.splice(y,1)
				y--
			}
		}
	}
	
	// 方法三：es6 Set
	// 原理：集合（Set）对象允许你存储任意类型的唯一值（不能重复），无论它是原始值或者是对象引用。
	var set = new Set(arr)//{'abc','abcd','sss','2','d','t','ss','f','22','d'}
	var newArr = Array.from(set)//再把set转变成array
	
	// 利用es6的拓展运算符...可以再简化如下：
	arr = new Set(arr)
	arr = [...arr]
```

2.**数组的深拷贝**

```javascript
	var arr = [1,'str','abc',{name:'laoxie'},123,321];
	var n1 = [];
	//1、遍历循环复制
	for(var i = 0;i<arr.length;i++){
		n1.push(arr[i]);
	}
	
	//2、arrayObject.slice(start,end)
	//返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
	//该方法并不会修改数组，而是返回一个子数组。如果想删除数组中的一段元素，应该使用方法 Array.splice()
	var n2 = arr.slice(0);
```

3.**字符串翻转输出**
<p>回顾    增： arr.unshift()在第一个增加  ；    arr.push（）在最后一个增加</p>
<p>回顾    删：arr.pop()删除最后一个  ；arr.shift（）删除第一个</p>

```javascript
	var	str = "helloWorld";
	//方法一，将字符串转化为数组，用数组的方法reverse翻转后，再转化为字符串
	var reverse1 = str.split("").reverse().join('');
	
	//方法二，先将字符串转化为数组a，遍历循环数组a
	//让数组rs2在每次循环的过程中最后面增加，数组a最后一个删除的元素
	var a = str.split("");
	var rs2 = [];
	while(a.length){
		rs2.push(a.pop());
	}
	var reverse2 = rs2.join("");
	
	console.log(reverse1,reverse2)//dlroWolleh;
```

4.**原生ajax请求**
- 创建异步请求对象
- 建立与服务器的连接
- 向服务器发送请求
- 处理数据（demo 04）

5.**吸顶效果** <br />
<a href="http://htmlpreview.github.com/?https://github.com/boa182/JavaScriptBasic/blob/master/demo/05%E5%90%B8%E9%A1%B6%E6%95%88%E6%9E%9C.html">吸顶demo</a>

6.**es7的两个新功能**
```javascript
//功能一：Array.prototype.includes() 确定一个元素是否在数组中存在，返回布尔值
		const life = ['mon','dad','brother','sister']
		console.log(life.includes('mon'))//true
		console.log(life.includes('boyfirend'))//false
		/*
			深入标准：Array.prototype.includes ( searchElement [ , fromIndex ] )
			1、searchElement —— 要查找的元素。
				(1)搜索按升序进行
				    Array(10000000).concat(4).includes(4)  true # [Time] 500 miliseconds 耗时 500ms
 				    [4].concat(Array(10000000)).includes(4) true # [Time] 90 miliseconds 耗时 90ms
				(2) 在任何位置找到都会返回 true，否则返回 false
				(3) 将数组中缺失的元素视为 undefined
				 [1, , 3].indexOf(undefined) -1
				 [1, , 3].includes(undefined) true
		*/
		
		 //2、fromIndex （可选的） — 开始查询的起始索引。默认值为0，意味整个数组都会被搜索
		 //当 fromIndex 大于数组长度时，.includes() 立即返回 false。
		 console.log(life.includes('mon',10))
		 // 如果为负数，则被用作偏移
		 console.log(life.includes('sister',-3))
		 
		 
/*
	功能二：指数运算符
		x ** y (aka Math.pow(x,y))
*/
		 console.log(2**2,2**3,2**4)
		 //4 , 8 ,16
```

7.**数组求最大，最小值**
```javascript
const arr = [54,65,43,21,12,66,45,58,97,24]
    
// 方法一：数组排序sort
let arr1 = arr.slice(0).sort(function(a,b){
	return a<b;
})
let arr1Max = arr1[0]
let arr1Min = arr1[arr.length-1]

// 方法二：扩展运算符+Math.max()
//原理：扩展运算符（ spread ）是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。
let arr2 = arr.slice(0)
let arr2Max = Math.max(...arr2)
let arr2Min = Math.min(...arr2)
  
// 方法三：选择排序(臃肿)
let arr3 = arr.slice(0)
let leng = arr3.length
let arr3Max = null
let arr3Min = null
for(let i = 0; i<leng ; i++) {
	for(let j = i+1;j<leng ; j++) {
		if(arr3[i]<arr3[j]){
			arr3Max = arr3[j]
			arr3[j] = arr3[i]
			arr3[i] = arr3Max
		}
	}
}
arr3Max = arr3[0]
arr3Min = arr3[arr3.length-1]
```

8.**拓展运算符的使用**
- 原理：
```javascript
const child1 = [
  {name:'child1-1'},
  {name:'child1-2'}
]
const child2 = [
  {name:'child2-1'},
  {name:'child2-2'}
]
const father = [
 {
    name:'father1',
    age: '32',
    children: [...child1,...child2] //[{},{},{},{}]
 },
 {
    name:'father2',
    age: '22',
    children: [child1,child2]  // [[{},{}],[{},{}]]
 }
]
```
- 实际应用：vue的嵌套路由
- 假设你的代码是这样：
```javascript
const router = new Router({
  routers: [
	{
	  path: '/', 
	  name: home,
	  component: () => import('components/home.vue'),
	  children: [{},{},{}......] // 假设你有N多个子路由，然后N多个子路由里面又嵌套N多个子路由，画面太长不忍直视
	}
  ]
})
```
- 改善一下：
在childRouter.js里面这样：
```javascript
export const child1  = [
   {
      path: '/child1',
      name: child1,
      component: () => import('components/child1.vue'),
      children: [{},{},{}...]
    }
]
```
- 在index.js里面这样：
```javascript
import child1 from './module/childRouter.js'
import child2 from './module/childRouter.js'
import child3 from './module/childRouter.js'

const router = new Router({
    routers: [
	{
	    path: '/', 
	    name: home,
	    component: () => import('components/home.vue'),
	    children: [...child1,...child2,...child3] 
	  }
	]
})
```
- 这样是不是既美观，又方便维护叻？
