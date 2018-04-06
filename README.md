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
	//方法一：indexOf的方法
	for(var i = 0;i<arr.length;i++){
		if(n.indexOf(arr[i])==-1){
			n.push(arr[i]);
		}
	}
	//方法二：选择排序
	for(var j = 0;j<arr.length;j++){
		for (var y = j+1;y<arr.length;y++){
			if(arr[j]==arr[y]){
				arr.splice(y,1)
				y--
			}
		}
	}
	console.log(n,arr);
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
