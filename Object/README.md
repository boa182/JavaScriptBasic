<h2>Object</h2>
- {}是一种无序的集合数据类型，它由若干键值对组成。

* <h3>基本操作</h3>

- 1.添加删除

```js
var xiaoming = {
    name: '小明'
};
xiaoming.age; // undefined
xiaoming.age = 18; // 新增一个age属性
xiaoming.age; // 18
delete xiaoming.age; // 删除age属性
xiaoming.age; // undefined

```

- 2.判断对象是否包含某属性,in

```js
var xiaoming = {
    name: '小明',
    height: 1.70
};
'name' in xiaoming; // true
'grade' in xiaoming; // false

/*不过要小心，如果in判断一个属性存在，这个属性不一定是xiaoming的
  它可能是xiaoming继承得到的：*/
'toString' in xiaoming; // true
```

- 3.要判断一个属性是否自身拥有的，而不是继承得到的hasOwnProperty()

```js
var xiaoming = {
    name: '小明'
};
xiaoming.hasOwnProperty('name'); // true
xiaoming.hasOwnProperty('toString'); // false
```

- 4.访问属性是通过.操作符完成的，但这要求属性名必须是一个有效的变量名。如果属性名包含特殊字符，就必须用['']括起来：

```js
var xiaohong = {
    name: '小红',
    'middle-school': 'No.1 Middle School'
};
xiaohong['middle-school']; // 'No.1 Middle School'
xiaohong['name']; // '小红'
xiaohong.name; // '小红'
```