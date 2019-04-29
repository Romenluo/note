### 类型检查

####　判断js数据类型的方法
* 判断js的数据类型有四种，分别是typeof、instanceof、constructor、toString。
##### typeof 方法
* typeof 可以检查以下7种类型number、boolean、string、object、undefined、function、symbol。此方法返回的事
被检测的类型名称。
```js
    // 检查字符串
    var str = 'str';
    console.log(typeof str) // string

    // 检查数字
    var num = 3;
    console.log(typeof num); // number

    // 检查 boolean 类型
    var bool = false;
    console.log(typeof bool); // boolean

    // 检查 undefined 类型
    var un;
    console.log(typeof un); // undefined

    // 检查 null 类型
    console.log(typeof null); // object

    // 检查 object 类型
    var obj = new Object();
    console.log(typeof obj); // object
    
    // 检查 function 类型
    var fun = function () {};
    console.log(typeof fun); // function
    
    // 检查 Symbol 类型
    let s = Symbol();
    console.log(typeof s); // Symbol
```
【注】
* 对于基本类型number、boolean、string、null、undefined 只有null返回object，其他返回类型正常。
* 对于引用类型，除 function 以外，一律返回 object 类型。

对于null返回object是因为null的直属类型是object，返回了处于其原型链最顶端的 Object 类型

#### instanceof 方法

* instanceof 是判断a是否为b的实例，使用表达式 a instanceof b ,返回true和false，如果a属于b
返回true，不属于就返回false。检查的是原型。
```js
    // instanceof 检查
    var dd = new Date();
    console.log(dd instanceof Date)// true

    console.log(null instanceof Object) // true

    var str = '';
    console.log(str instanceof Number) // false
```

#### constructor

* 当一个函数被定义时，JS引擎会为此函数添加 prototype 原型，然后再在 prototype上添加一个 constructor 属性，
并让其指向这个函数的引用。
```js
    function Fun() {
       console.log('hello world')
    }
    var f = new Fun();
    console.log(f.constructor == Fun) // true
```
【注】null 和 undefined 是无效的对象，因此是不会有 constructor 存在的。一般用来检查自定义的函数。
当使用 prototype 重写后，原有的 constructor 引用会丢失，constructor 会默认为 Object

####　toString
使用toString判断 Object 对象，直接调用 toString()  就能返回 [object Object] 。
而对于其他对象，则需要通过 call / apply 来调用才能返回正确的类型信息。
```js
    var obj = {};
    console.log(obj.toString())// [object Object]
    console.log(Object.prototype.toString.call('')) // [object String]
    console.log(Object.prototype.toString.call(2)) // [object Number]
    var array = [];
    console.log(Object.prototype.toString.call(array)) // [object Array]
```
