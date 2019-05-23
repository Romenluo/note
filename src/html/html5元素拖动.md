---
layout: '[layout]'
title: html5元素拖动
date: 2019-05-23 14:59:36
categories: HTML
tags: HTML,拖动,draggable
---

### html5元素拖动

将元素在两个盒子中来回拖动
```
<body>
<!--两个div中来回拖放-->
<div class="root" id="div" ondrop="drop(event)" ondragover="allowDrop(event)">
    <img src="./Romen.jpg" id="image1" draggable="true" ondragstart="drag(event)">
</div>
<div class="root" id="div2" ondrop="drop(event)" ondragover="allowDrop(event)"></div>

<script>
    /**
     * 1. 首先设置元素是否可以拖动draggable="true"
     * 2.表示要拖动什么，ondragstart属性调用了一个函数，设置被拖数据的数据类型和值：
     *
     */
    function drag(ev) {
        ev.dataTransfer.setData('node', ev.target.id);
    }

    /**
     * 3.放到什么地方，ondragover 事件规定在何处放置被拖动的数据。
     */
    function allowDrop(ev) {
        ev.preventDefault();
    }

    /**
     * 4.进行放置，当放置被拖数据时，会发生drop事件。当该事件被触发时，在元素中添加一个被拖动的元素
     */
    function drop(ev) {
        ev.preventDefault();
        var data = ev.dataTransfer.getData('node');
        ev.target.appendChild(document.getElementById(data));
    }
</script>
</body>
```
