<h1>一些原生JavaScript的基础算法</h1>
<h2>不定时更新补充修改，如果有出错，望指导（281189459@qq.com）</h2>

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