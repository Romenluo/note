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
