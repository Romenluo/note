### 对象

#### 创建对象

创建对象可以使用new或花括号{}来创建对象。对象由属性和{}组成，属性是一个键值对，即属性名和值。
```js
//创建对象的方法，下面是创建两个空对象
let obj = new Object(); //构造函数的创建方法

let obj1 = {} //'字面量的创建方法'
```
在创建对象时可以同时添加属性,属性之间必须使用‘,’隔开。

```js
// 创建属性可以是基本类型和引用类型，还可以是function
let obj = {
  name: 'Romenluo',
  list: [1,2,3],
  obj: {},
  "one day":'1234',// 以用多字词语来作为属性名，但是他们必须加上引号.使用是用obj['one day']获取属性值
  fun: function() {
    console.log('属性是一个function')
  }
}
```

对对像里的属性赋值或者获取属性值使用‘.’操作符
```js
// 给name重新赋值
obj.name = 'men'

//获取name 的值
let name = obj.name
//可以使用[]，如
let name1 = obj[name]

```
创建完对象后再添加属性

```js
//为obj对象添加一个age属性
obj.age = 20
```

删除一个属性
```js
// 删除obj中的name属性
delete obj.name
```
使用[]调用属性，在上面定义了一个"one day"属性，此属性不能使用obj.one day的方法，点操作需要的键是一个有效的标识符，不能有空格和其他的一些限制。因此只能使用[]的形式调用属性。

```js
//使用"one day"属性
obj["one day"] //1234

//删除属性时也是一样使用[]
delete obj["one day"]
```

#### 属性简写

在某些地方我们可以使用属性简写的形式。如

```js

function fun(name,age) {
  return {
    name: name,
    age: age
  }
}

let f = fun('Romenluo',20)
console.log(f.name)
```

可以简写为以下代码

```js

function fun(name,age) {
  return {
    name,
    age
  }
}

let f = fun('Romenluo',20)
console.log(f.name)
```

当然可以两种形式可以混用。

```js
function fun(name,age) {
  return {
    name,
    age:age,
    sex: 'man'
  }
}

let f = fun('Romenluo',20)
console.log(f.name)
```

#### 属性检查

使用 ‘in’ 检查，可以检查出自身存在的属性和继承的属性。"key" in object in 的左边必须是属性名。通常是一个字符串，如果不用字符串，那就是一个字符串变量。

```js
console.log('name' in obj) // true
console.log('na' in obj) // false
```

使用 undefined 判断，如果这个属性名没有值也不会有错误。访问一个不存在的属性会返回 undefined

```js
console.log(obj.na === undefined) //返回true表示这个属性不存在
console.log(obj.name === undefined) // 返回false表示这儿属性存在
```

使用对象的hasOwnProperty()方法，此方法只能判断自身的属性，不能检查出继承的属性。参数是字符串

```js
console.log(obj.hasOwnProperty('name'))// true
console.log(obj.hasOwnProperty('one')) //false
```

#### 遍历对象的属性

变量对象的属性可以使用for...in...循环遍历

```js
for(let key in obj){
  console.log('key:'+key);// key表示键值对，即属性
  console.log('value:'+obj[key]) // 表示属性值
}
```
