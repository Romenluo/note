### vue实现拖动容器组件

```
<template>
  <div class="contain" ref="dragContain">
    <div class="control" v-drag="contain">
      <div style="line-height:30px;background:#409EFF;cursor:move;color:#fff;text-indent:15px;">
        控制面板
      </div>
      <div style="padding:7px;" >
        <slot></slot>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'vue-drag-infinite',
    data () {
      return {
        //外层容器的宽高 数值不带px单位
        contain: {
          xx: 500,
          yy: 500
        }
      }
    },
    mounted () {
      this.contain.xx = this.$refs.dragContain.offsetWidth
      this.contain.yy = this.$refs.dragContain.offsetHeight
    },
    methods: {
    },
    computed: {},
    directives: {
      drag: {
        bind: function (el, binding, vnode) {
          el.onmousedown = function (e) {//鼠标按下事件
            var disx = e.clientX - el.offsetLeft
            var disy = e.clientY - el.offsetTop//获取鼠标相对与元素的位置
            document.onmousemove = function (e) {
              let left = e.clientX - disx
              let top = e.clientY - disy
              if (left < 0) {
                left = 0
              }
              if (top < 0) {
                top = 0
              }
              if (left > binding.value.xx - el.offsetWidth) {
                left = binding.value.xx - el.offsetWidth
              }
              if (top > binding.value.yy - el.offsetHeight) {
                top = binding.value.yy - el.offsetHeight
              }
              el.style.left = left + 'px'
              el.style.top = top + 'px'
            }
            document.onmouseup = function () {
              document.onmousemove = document.onmouseup = null
            }
          }
        }
      }
    }

  }

</script>
<style lang='scss' scoped>
  .contain {
    height: 580px;
    background: #ddd;
    position: relative;
    user-select: none;
  }
  .control {
    width: 250px;
    height: 500px;
    border-radius: 5px;
    overflow: auto;
    background-color: #B3C0D1;
    position: fixed;
    z-index: 999;
    right: 20px;
    top: 15px;
  }

</style>
```
