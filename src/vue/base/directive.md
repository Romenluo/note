### 自定义指令

#### 方法一
在vue中允许用户自己定义指令，只定义指令使用Vue.directive()创建，注意需要在实例初始化之前。指令不支持
驼峰式写法，需要使用全小写或‘-’、‘_’分隔。如创建一个指令改变字体颜色。
```js
        Vue.directive('color',function(el,binding,vnode){
            el.style = 'color:'+binding.value
        });
        var app = new Vue({
            el:'#app',
            data: {
                color:'#409EFF'
            }
        })
```
使用到的三个参数：

1. el: 指令所绑定的元素，可以用来直接操作DOM
2. binding: 一个对象，包含指令的很多信息
    * name: 指令名，不包括 v- 前缀
    * value： 指令绑定值
    * oldValue: 指令绑定的签一个值，仅在 update 和 componentUpdated 钩子中可用。无论值是否改变都可用。
    * expression:　字符形式的指令表达式，如v-my='1+1',表达式为1+1
    * arg: 传给指令的参数，可选
    * modifiers: 一个包含修饰符的对象，v-my-directive.foo.bar 中，修饰符对象为 { foo: true, bar: true }。
3. vnode: vue编译生成的虚拟节点

在标签中使用指令
```html
<div id='app'>
   <div v-color='color'>你好</div>
</div>
```

#### 方法二
