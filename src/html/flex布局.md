---
layout: '[layout]'
title: flex布局
date: 2019-05-21 15:28:36
categories: HTML
tags: HTML,flex,css
---

### flex布局
flex布局是Flexible Box 模型，通常被称为 flexbox，即 “弹性布局”。是一种一维的布局模型。
flexbox 一次只能处理一个维度上的元素布局，一行或者一列。

#### 定义
定义一个flex布局，使用display:flex,如果是一个行内flex布局为 display:inline-flex。
如：

```
<!--heml代码-->
 <div class="flex-demo1"></div>
 
 <!--css定义,使上面布局为flex布局-->
 <style>
    .flex-demo1{
        display:flex;
    }
 </style>
  
```
如果要使用行内flex布局，将 display:flex 变为 display:inline-flex即可;

【注】如果涉及到兼容性，一般需要做兼容处理

```
display: -webkit-box;   /* OLD - iOS 6-, Safari 3.1-6 */
display: -moz-box;  /* OLD - Firefox 19- H5不用考虑 */
display: -mz-flexbox; /* TWEENER IE 10 */
display: flex; /* NEW, Spec - Opera 12.1, Firefox 20+ */
```

#### flex布局容器的属性

1. flex-direction 属性
此属性决定主轴的方向，内部元素是横向排列还是纵向排列，有四个值 row 、 row-reverse 、 column 、 column-reverse;将flex-direction设置为row或row-reverse ，表示主轴方向显示，即水平方向排列，值为column或column-reverse，表示交叉轴，即垂直方向排列。

* flex-direction值为row,表示从左到右排列为一行。以下代码表示flex-demo1中的子元素为从左到右排列，如果子元素超过父元素的总宽，不会折行显示，只显示为一行。
如果要换行需要设置flex-wrap的属性。

html

```html
  <div class="flex-demo1">
    <span>1</span>
    <span>2</span>
    <span>3</span>
  </div>
```

css

```css
    .flex-demo1{
      display: flex;
      flex-direction: row;
      border: 1px solid #FF0000;
    }
    .flex-demo1 span{
      display: block;
      width: 60px;
      height: 60px;
      background-color: #aaaaaa;
      margin: 5px 10px;
    }
```
显示效果

![row](flex布局/flex-row.png)

* flex-direction值为 row-reverse ：主轴为水平方向，起点在右端

![row-reverse](flex布局/flex-row-reverse.png)

* flex-direction值为 column ：主轴为垂直方向，起点在上方

![row-reverse](flex布局/flex-column.png)

* flex-direction值为 column-reverse ：主轴为垂直方向，起点在下方

![row-reverse](flex布局/flex-column-reverse.png)

2. flex-wrap属性，有三个值可选 nowrap、wrap、wrap-reverse; nowrap表示不换行，wrap表示第一行在上面，wrap-reverse表示第一行在下面。

* flex-wrap值为 nowrap 不换行

![nowrap](flex布局/flex-nowrap.png)

* flex-wrap值为 wrap，第一行在上面

![wrap](flex布局/flex-wrap.png)

* flex-wrap值为 wrap-reverse ，第一行在下面

![wrap-reverse](flex布局/flex-wrap-reverse.png)

【注】：当flex-direction值为column或column-reverse时，此属性不能显示出效果，如果没有设置flex-direction，默认为水平排列，此属性有效果。

3. flex-flow属性是flex-direction和flex-wrap的简写，默认值为 row nowrap ，赋值时先写flex-direction的值，再写flex-wrap的值。

```
flex-flow: row wrap;
```

4. justify-content属性，表示在水平方向的对齐方式。
>1. flex-start（默认值）：左对齐

![左对齐方式](flex布局/flex-row.png)

>2. flex-end：右对齐

![左对齐方式](flex布局/flex-end.png)

>3. center： 居中

![居中](flex布局/flex-center.png)

>4. space-between：两端对齐，项目之间的间隔都相等。

![两端对齐](flex布局/flex-space-between.png)

>5. space-around：每个项目盒子的间隔相等。

![间隔相等](flex布局/flex-space-around.png)

5. align-items属性,表示设置交叉轴上的对齐方式，垂直方向对齐方式

>1. flex-start：交叉轴的起点对齐。

![flex-start](flex布局/align-items-start.png)

>2. flex-end：交叉轴的终点对齐。

![flex-end](flex布局/align-items-end.png)

>3. center：交叉轴的中点对齐。

![center](flex布局/align-item-center.png)

>4. baseline: 项目的第一行文字的基线对齐。

![baseline](flex布局/align-items-baseline.png)

>5. stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

![stretch](flex布局/flex-row.png)

6. align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用,将设置 flex-wrap: wrap;

>1. flex-start：与交叉轴的起点对齐(从上到下依次排列)。

![stretch](flex布局/flex-align-content.png)

>2. flex-end：与交叉轴的终点对齐(最下方开始排列)。

![stretch](flex布局/flex-align-end.png)

>3. center：与交叉轴的中点对齐。

![stretch](flex布局/align-content-center.png)

>4. space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。

![stretch](flex布局/align-content-space-between.png)

>5. space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

![stretch](flex布局/align-conten-space-around.png)

>6. stretch（默认值）：轴线占满整个交叉轴。将box高设置为auto

![stretch](flex布局/align-conten-stretch.png)

#### 设置在flex布局直接子元素上的属性

1. order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。如果值是一样，则安照先后顺序排列

![order](flex布局/order.png)

2. flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大，如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。从现象上可以看出此属性按比例切分父组件。
3. flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
4. flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。
5. flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
6. align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

[参考文章](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
