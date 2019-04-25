### 函数参数

#### 概念

* ECMAScript函数不介意传进来的参数是什么类型的。在调用函数时可以不传参数，也可以传多个参数。出现此情况时ECMAScript
内部参数是使用数组来表示，函数接收到的始终是一个数组，不关心数组中包含那些参数。在函数体内可以通过 arguments 对象来访问
这个参数，但是arguments并不是一个Array类型，只是与数组相似。使用length表示传进来多少个参数。如：
```js
    function fun() {
     console.log(arguments.length)// 2
    }
    fun('name',2) // 控制台输出2，表示传入两个参数
```
案例2： 计算传入参数的和
```js
    function fun2() {
        var sum = 0;
       for(var i in arguments){
           sum += arguments[i]
       }
       return sum;
    }
    console.log(fun2(5,6,8,9,4)) // 32
```
