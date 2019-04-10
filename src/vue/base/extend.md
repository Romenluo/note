### vue.extend 扩展实例构造器

* Vue.extend返回一个扩展实例构造器，预设了部分选项的Vue实例构造器。
  其主要用来服务于Vue.component，用来生成组件。当在模板中遇到该组件名称作为标签的自定义元素时，
  会自动调用“扩展实例构造器”来生产组件实例，并挂载到自定义元素上。
  
 * 如我们在多个组件中需要使用到连接到github官网的连接，我们可以使用Vue.extend实现扩展实例
 ```
 var aa = Vue.extend({
         template:"<p><a :href='url'>{{name}}</a></p>",
         data: function () {
             return {
                 url: 'https://github.com',
                 name: 'gitHub'
             }
         }
     })
 ```
 * 将其挂载到自定义组件上
 ```
    new aa().$mount('aa')
 ```
 
* 使用自定义组件
````html
<aa></aa>
````
* 完整代码如下
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../lib/vue.min.js"></script>
</head>
<body>
<aa></aa>
<script>
    var aa = Vue.extend({
        template:"<p><a :href='url'>{{name}}</a></p>",
        data: function () {
            return {
                url: 'https://github.com',
                name: 'gitHub'
            }
        }
    })
    //挂载到自定义组件
   new aa().$mount('aa')
</script>
</body>
</html>
```
* 可以挂载到一个普通标签上面，可以使用标签选择器，
标签为：
```html
<p class="aa"></p>
<p id="=bb"></p>
```
* 挂载时使用选择器即可，挂载后会效果一样
```js
new aa().$mount('.aa');
new aa().$mount('#bb');
```
