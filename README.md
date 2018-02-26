<h1>一些原生JavaScript的基础算法</h1>
<h2>不定时更新补充修改，如果有出错，望指导（281189459@qq.com）</h2>

```javascript
	var arr =  ['abc','abcd','sss','2','d','t','2','ss','f','22','d'];
			var n = [];
			//indexOf的方法
			for(var i = 0;i<arr.length;i++){
				if(n.indexOf(arr[i])==-1){
					n.push(arr[i]);
				}
			}
			//选择排序
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

