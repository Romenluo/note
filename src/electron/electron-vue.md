### electron-vue 项目入门

#### electron-vue 安装

```
# 安装全局vue-cli
npm install -g vue-cli
# 使用vue-cli来安装electron-vue的模板
vue init simulatedgreg/electron-vue my-project

# 安装依赖
npm i
# 进入开发模式，运行调试结果
npm run dev

```
### 自定义titleBar
1. 隐藏原始的titleBar ,在主线程文件index.js文件中修改
```js
 mainWindow = new BrowserWindow({
    height: 563,
    useContentSize: true,
    width: 1000,
    // titleBarStyle: 'hidden'
    frame: false /* 隐藏标题栏 */
  })
```

2. 自定义窗口的min,max,close

屏蔽掉原始的标题栏后窗口不能拖动。需要设置可拖动的区域。样式上面添加 -webkit-app-region: drag;

先在界面上放三个按钮，如下vue文件
```vue
<template>
    <div class="title-right">
        <div class="min" @click="goIpc('min')"></div>
        <div class="max" @click="goIpc('max')"></div>
        <div class="close" @click="goIpc('close')"></div>
    </div>
</template>

<script>
  const {ipcRenderer: ipc} = require('electron')
  export default {
    name: 'title-box',
    methods: {
      goIpc (item) {
        console.log(item)
        ipc.send(item)
      }
    }
  }
</script>

<style lang="scss" scoped>
    .title-right{
        display: flex;
        width: 150px;
        height: 60px;
        -webkit-app-region: no-drag;
        background-color: aquamarine;
        justify-content: flex-end;
        align-items: center;
        div{
            width: 20px;
            height: 20px;
            margin-right: 20px;
        }
        .min{
            background-color: #2b16fa;
        }
        .max{
            background-color: #fa28de;
        }
        .close{
            background-color: antiquewhite;
        }
    }
</style>

```
[注： -webkit-app-region: no-drag;需要设置，否则点击没有效果]

需要在主线程index.js文件上面添加点击事件

```js
import { app, BrowserWindow, ipcMain } from 'electron'
/* 窗口标题栏的点击 */
// 登录窗口最小化
ipcMain.on('min', function () {
  mainWindow.minimize()
})
// 登录窗口最大化
ipcMain.on('max', function () {
  if (mainWindow.isMaximized()) {
    mainWindow.restore()
  } else {
    mainWindow.maximize()
  }
})
// 关闭窗口
ipcMain.on('close', function () {
  mainWindow.close()
})
```