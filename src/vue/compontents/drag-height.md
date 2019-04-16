### 通过拖拉改变容器高度

* 需求：通过拖拉div底部改变div高度

代码
```html
<template>
  <div>
    <div class="drag">
      <div class="main"></div>
      <div class="foot" @mousedown="mouseDown($event)"></div>
    </div>
  </div>
</template>
```

js部分

```js
  export default {
    name: 'drag',
    data () {
      return {}
    },
    methods: {
      mouseDown (e) {
        let drag = document.querySelector('.main')
        let dragHeight = drag.offsetHeight
        let oldY = e.pageY
        /**
         * 移动鼠标是发生的事件，改变需要改变容器的高度，最小高度为150px
         * @param e
         */
        document.onmousemove = function (e) {
          let newY = e.pageY - oldY
          drag.style.height = ((newY + parseInt(dragHeight) >= 150 ? (newY + parseInt(dragHeight)) : '150') + 'px')
        }
        document.onmouseup = function () {
          document.onmousemove = document.onmouseup = null
        }
        e.stopPropagation()
      }
    }
  }
```

css

```css
.main {
    width: 200px;
    height: 400px;
    border: 1px solid #dedede;
    border-radius: 5px;
  }
  .foot{
    width: 200px;
    height: 3px;
    background-color: dodgerblue;
  }
  .foot:hover{
    cursor: s-resize;
  }
```
