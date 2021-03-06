### this的使用

访问对象中的存储的信息来完成其工作，为了访问该对象，方法中可以使用 this 关键字。

JS 里的 this

* 在 function 内部被创建
* 指向调用时所在函数所绑定的对象
* this 不能被赋值，但可以被 call/apply  改变

可能使用到的地方
>1. this 和构造器
>2. this 和对象
>3. this 和函数(this 和独立的函数放在一起是没有意义的)
>4. 全局环境的 this(浏览器环境中是 window[ 严格模式下 ]， node 环境中是 global)
>5. this 和 DOM/事件
>6. this 可以被 call/apply 改变
>7. me/self/that/_this 暂存 this
>8. ES5 中新增的 bind 和 this
>9. ES6 箭头函数(arrow function) 和 this

判断 this 指向谁，看执行时而非定义时，只要函数(function)没有绑定在对象上调用，它的 this 就是 window

错误的访问对象中属性的方法
```js
let person = {
  name: 'Romenluo',
  age: 20,
  hello(){
    console.log(name)//想访问person中的name属性
  }
}
person.hello();// 控制台却什么也没有输出
```

能访问对象中的属性方法

```js
let person = {
  name: 'Romenluo',
  age: 20,
  hello(){
    console.log(this.name)//想访问person中的name属性
  }
}
person.hello();// 控制台输出 Romenluo
```

可以使用person代替this，通过外部变量名来引用，但是这样是不可靠的。如果将person赋给其他变量，会导致错误

```js
let person = {
  name: 'Romenluo',
  age: 20,
  hello(){
    console.log(person.name)//想访问person中的name属性
  }
}
person.hello();// 控制台输出 Romenluo
```

如果person赋给其他变量后将其设置为null,将会报错，如下

```js
let person = {
    name: 'luomen',
    age: 25,
    hello() {
      console.log(person.name);//使用person调用name
    }
  }
  let user = person;
  person = null; // 将person设置为null
  user.hello(); // 运行后报错，提示Cannot read property 'name' of null at Object.hello
```

#### this使用范围

this关键字不受限制，可以使用在任何函数中。运行时求值的，它可以是任何值。如使用不同对象调用同一个函数时。

```js
  let user1 = {
    name: '一号前端'
  }
  let user2 = {
    name: '二号前端'
  }

  function fun() {
    console.log(this.name)
  }

  user1.f = fun; // [注] 此处不能写成user1.f = fun()。因为fun表示的是一个变量，不是调用，
  user2.f = fun;

  user1.f();//输出 ‘一号前端’，表示user1调用的函数，函数中的this表示user1

  user2.f(); // 输出 ‘二号前端’ 表示user2调用的函数，函数中的this表示user2
```

由上面的代码可以看出，函数中的this表示谁调用就是谁。

在没有任何对象的情况下调用包含有this的函数。在严格模式下返回的是一个undefined，在非严格模式下返回的事window对象。
```js
function fun1() {
    console.log(this)
  }
  fun1();
```


####　this 可以被 call/apply 改变

```js
var m1 = {
    message: 'This is A'
} 
var m2 = {
    message: 'This is B'
}  
 
function showMsg() {
    alert(this.message)
}
 
showMsg() // undefined
showMsg.call(m1) // 'This is A'
showMsg.call(m2) // 'This is B'
```
