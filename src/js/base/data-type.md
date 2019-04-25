### 数据类型

* ECMAScript有5种基本数据类型：Undefined、Null、Boolean、Number、String。
object属于复杂数据类型，因此js有六种数据类型。

+ 检测数据类型：使用 typeof 检查一个变量的数据类型。
    - 检查有一个变量没有赋值时，数据类型为 undefined。
    ```js
    // 当变量不赋值时，自动赋值为undefined
    var aa ;
    console.log(typeof aa);//undefined
    ```
    - 使用 typeof 检查 null 时无效，因为 null 属于 object 类型。因此一般在判断中不适用 typeof null
    ```js
    var bb = null;
    console.log(typeof bb);//object
    ```
##### undefined 类型 

* undefined类型只是一个值，使用var声明一个变量时没有初始化时的值。
##### null 类型
* null类型是只有一个值的类型。值为null,从逻辑上来看null值表示一个空对像指针，也是 typeof 检查 null 值
会返回object的原因。如果一个变量要用来保存一个对象初始化就可以是null,而不是其他类型。
#####
 boolean 类型
 * 该类型只有两个值，true和false。【注：true不一定等于1，false不一定等于0】,将其他类型的变量转为boolean类型
```js
    //将一个变量转为boolean类型
    var b1 = 'hello',b2,b3 = 1,b4 = 0;
    var bb1 = Boolean(b1);
    var bb2 = Boolean(b2);
    var bb3 = Boolean(b3);
    var bb4 = Boolean(b4);
    console.log(bb1)// true
    console.log(bb2)// false
    console.log(bb3)// true
    console.log(bb4)// false
```
数据类型|转换为true的值|转换位false的值
:----:|:-----:|:-----:
Boolean|true|false
String|任何非空字符|""（空字符串）
number|任何非零数字|0和NaN
object|任何对象|null
undefined|不适用|undefined

##### number类型
* number 使用IEEE754表示整数和浮点数。
* 数值转换：可以使用Number(),parseInt(),ParseFloat()进行转换。第一个可以转换任何类型的数据，有两种是转换字符串类型。

##### String 类型
* string 类型用于表示0或多个unicode字符组成的字符序列。
* 将其他类型的转换位string类型，可以使用toString()方法，但是null和undefined没有toString()方法，只能使用String(null)
返回得到字符串'null'。数字类型转为string可以加一个空字符串''。

#### object 类型
* 其实是一组数据和功能的集合。可以使用 new 来创建一个对象。var o = new Object();
+ 主要函数
    - constructor 保存着用于创建当前对象的函数，即构造函数。
    - hasOwnProperty(propertyName) 检查给定的属性名是否在当前对象中。参数必须是字符串。
    - isPrototypeOf(object) 检查传入的对象是否是当前对象的的原型。
    - propertyIsEnumerable(propertyName) 检查给定属性是否可以使用for-in语句来枚举。
    - toLocaleString() 返回对象的字符串表示。
    - toString() 返回对象的字符串表示。
    - valueOf() 返回对象的字符串、数组或布尔值表示。
