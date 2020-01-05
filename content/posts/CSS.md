---
title: CSS总结
date: 2019-12-17T13:43:05+08:00
lastmod: 2019-12-17T13:43:05+08:00
author: FFreshman
cover: /img/awesome.jpg
categories: ["CSS"]
tags: ["CSS"]
# showcase: true
draft: false
---

**对CSS的布局、层叠、动画做一个总结**

<!--more-->

# 一、CSS布局
**其实页面本身的默认布局是依靠文档流来实现的，简单来说就是块级元素``display:block``独占一行，行内元素``display:inline``按从左到右依次排列，如果我们要去实现自己想要的布局就得用以下3种布局方式。**

**首先我们要知道如何去选择一个布局**

![](/images/choose.png)
## **(1) float**
**float布局大多用在ie浏览器上，那么float布局怎么使用呢**
### **1、在浮动元素的父元素上加上````class=clearfix````**
````css
.clearfix:after{	
  content："";
  display:block;
  clear:both;
}
````
**注意在这个里面不要写除上面代码以外的样式，否则还是不能包裹，可以给父元素再加一个class以写入其他样式**

### **2、 在子元素中写上**
````css
float:left|right
````
**在[盒模型](https://ffreshman.github.io/posts/css-box/)那篇博客里有写到如果元素使用了float，则不会出现margin合并,这里还有个ie6/7的一个双倍margin的bug存在，可以选择在父元素上加上``display:inline-block``**

**再介绍一个垂直对齐属性：``vertical-align``**
````css
vertical-align:middle;
````
**可以实现元素在垂直方向上的居中，具体用法可以参考[vertical-align](https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align)**

**Tip1 outline**

当使用``outline：1px solid red;``的时候，border-box的width这时候会把border排除在外，outline的意思就是宽度实际上在盒子的外边，而不计入width

**而且这时候会出现margin重叠现象**

**Tip2 关于负margin**

**margin:left和margin:top的参考对象是相邻元素，如果为负，则会使得自己向上或向左移动**

**margin:right和margin:bottom的参考对象是自己，如果为负，则会使得相邻元素向自己靠近**

eg：[最后一行有负margin的使用](http://js.jirengu.com/qawin/2/edit?html,css)

## **(2) flex**（一般用于一维布局）
**首先flex布局分为容器container和内容items两部分**
## **container**
### **1、 ``display:flex``**
````css
.container{
    display:flex|inline-flex;
    }
````
区别跟block和inline-block差不多，可以使一个元素变为flex布局
### **2、 改变item的流动方向**
````css
.container{
Flex-direction:row(default)|row-reverse|column|column-reverse
}
````
可以让items按行或者逆行，列或者逆列排列

![](/images/css/row.png)
### **3、 是否换行**
````css
.container{
    Flex-wrap:nowrap|wrap|wrap-reverse;
    }
````
nowrap为默认属性，不换行的话会使得元素的width变小挤在，wrap-reverse一般不用
### **4、 主轴对齐方式（默认是x轴）**
````css
.container{
    justify-content:center;
    }
````
![](/images/css/just.png)

**``space-around``和``space-evenly``的区别是，前者是元素两边空间一样大，后者是4个空隙大小一样大**
### **5、 垂直主轴方向对齐**
````css
.container{
    Align-items:center|flex-start|flex-end|stretch
    }
````
![](/images/css/items.png)
### **6、 多行内容对齐方式**
````css
.container{
    Align-content:center|flex-start|flex-end|stretch
    }
````
## **items**
### **1、 ``order``**
````css
.items{
    order:1
}
````
order默认为0，可以为负，从小到大依次决定items在container中的排列顺序
### **2、 ``Flex-grow``、``flex-shrink``**
````css
.items{
    flex-grow:1
}
````
``flex-grow``默认是0，是用来分配多余空间的，当页面被拉升时，数字大的会占据更多比例的多余空间
````css
.items{
   flex-shrink:1
}
````
``flex-shrink``默认是1，用来决定当空间不够时，哪个元素给出的空间更多，数字越大当缩小的越快，flex-shrink=0的时候就是铁公鸡，一毛不拔

### **3、 ``basis``**
**跟width属性差不多，可以相互代替**
>当``grow``、``shrink``、``basis``一起写的时候可以用``flex``
````css
.items{
   flex:1 1 30px;
}
````
**注：如果要写shrink则一定要写basis**

**最后推荐一个flex布局练习小游戏[flexfroggy](https://flexboxfroggy.com/)**

## **(3) grid**（一般用于二维布局）

### **grid和flex一样也分为container和items**
## **container**
### **1、 成为container**
````css
.container{
    display:grid|inline-grid;
}
````
### **2、 设置gird的行和列**
````css
.container{
    grid-template-row:40px 50px auto 50px 40px;
    grid-template-column:25% 100px auto;
}
````
![](/images/css/gird.png)

**这个步骤是把一个元素用横竖两种线划分为一个个区域**

你甚至可以给每条线取名字
````css
.container{
    grid-template-row:[first]40px [lin2]50px [line3]auto [line4]50px [last]40px;
    grid-template-column:25% 100px auto;
}
````
### **还有一种划分区域划分单位是<abbr title=free-space>fr</abbr>**
````css
.container{
    grid-template-row:1fr 1fr 1fr
    grid-template-column:25% 100px auto;
}
````
### **3、 gap**
````css
.container{
    gird-row-gap:10px;
    grid-column-gap:20px;
}
````
![](/images/css/gap.png)

**可以设置块之间的间隙是多少**
**Tips**

````css
.container{
    grid-template-row:30px repeat(3,20px)
    grid-template-column:25% 100px auto 30px;
}
````
``repeat``可以重复相同数值的区域
## **items**
**当我们把区域划分好以后只需把内容指定区域就可以实现布局了**
## **items**
````css
.items{
    grid-column-start:2;
    grid-column-end:5;
    grid-row-start:3;
    grid-row-start:4;
}
````
**就可以将这个元素放到相应范围的gird空间里**

**Tips**
````css
.items{
    gird-row:4/5;
    gird-column:2/3;
}
````
**这是上面写法的简化**

## **``grid-template-area``**
### 接下来介绍一种更好用的grid分区方式
![](/images/css/area.png)

**把每个方格都取名，之后只要把相应的items放入其中即可，而不用再写横着从那条线到那条线，竖着从哪条到那条**

**Tips**
````css
.container{
    gird-area:1/3/4/5;
}
````
**``grid-area``是按``gird-row-start``、``gird-column-start``、``gird-row-end``、``grid-column-end``的顺序的简写**

**最后推荐一个gird布局练习小游戏[gird-garden](https://cssgridgarden.com/#zh-cn)**

# 二、 浏览器渲染原理
## **（1） 什么叫渲染**
**浏览器的渲染简单来说就是把html文件，css文件和JavaScript文件组合起来并解析成浏览器上你能看到的东西，整个过程非常复杂，主要分为以下几步**

1. 根据HTML构建HTML树（DOM）
2. 根据CSS构建CSSDOM
3. 将两棵树合并为render tree
4. Layout布局根据文档流和盒模型计算大小和位置
5. paint绘制（把边框文字阴影等颜色绘制出来）
6. compose合成（根据层叠关系展示画面）

![](/images/css/tree.png)
## **（2） 更新样式**
**当我们使用js的时候，网页的显示内容会发生改变，这时候发生了什么呢，其实就是浏览器重新渲染的过程，但是浏览器也不傻，他会选最省资源的方式去更新样式，所以就有了3种样式更新的路径**

![](/images/css/render.png)

**不同的属性改变会使用不同的路径进行样式更新，但是css的行为你永远无法预测，所以我们可以用穷举法去测试，有一个[参考网站](https://csstriggers.com/)**

# 三、 CSS动画
**这里简单介绍一下用``animation``和``transform``做动画，之后再js篇在重新整理**

## **1、 [transform](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform)** 

**transform有许多功能，这里只介绍常用的4个**

**Tips**
>inline 元素不支持transform，需要先设置``display：block``
### **(1) translate(位移)**
#### 1.X轴方向
````css
    .items{
        transform:translateX(<length-percentage>)
    }
````
#### 2.Y轴方向
````css
    .items{
        transform:translateY(<length-percentage>)
    }
````
#### 3.Z轴方向
````css
    .items{
        transform:translateZ(<length-percentage>)
    }
````
**Tips**

>**1.** Z轴的平移需要在其父元素上加上perspective，也就是3维坐标系原点，这个点位于屏幕内部，比如
````css
.father{
    perspective:100px;
}
````

>**2.** 3个坐标可以写在一起
````css
.element{
    transform:translate(x,y,z);
}
````
**同样需要指定原点坐标**

### **(2) scale(缩放)**
````css
.element{
    transform:scaleX(<number>);
    transform:scaleY(<number>);
    transform:scale(<number>,<number>?)
}
````

### **(3) rotate(旋转)**
````css
.element{
    transform:rotateX(20deg);
}
````
**也分为X,Y,Z轴正角度是顺时针旋转,Z轴旋转是在平面上的投影
一般用于制作loading图标**

### **(4) skew(倾斜)**
**语法与旋转大同小异，正角度默认倾斜是逆时针**

**多重效果可以写在一个transform里**
````css
.element{
transform:translate(x,y) scale(30deg);
}
````


## **2、 transition(过渡)**
**``transition``可以设置动画初始和结束状态中间的补帧，其属性值有**
1. 属性名：可以单独设置某个属性的过渡，也可以设置为All，即所有属性过渡
2. 时长：过渡时长
3. 过渡方方式：ease|ease-in|ease-out|linear|steps等
4. 延迟：过几秒以后触发动画
   
**Tips**
>``display:none``到block是无法过渡的，要实现从有到无建议使用``visibility:hidden``属性实现

## **3、 animation**
### **animation包括两部分，``@keyframes``和``animation``**

## (1)[``@keyframes``](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)
**``@keyframes``可以定义多个transform动作，并设置他们的时间范围

````css
@keyframes identifier {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  68%, 72% { left: 50px; }
  100% { top: 100px; left: 100%; }
}
````
## (2) [``animation``](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)

**``animation``的属性分以下几种**

1. **animation-name**:指定由@keyframes描述的关键帧名称
2. **animation-duration**:设置动画一个周期的时长
3. **animation-timing-function**:设置动画速度， 即通过建立加速度曲线，设置动画在关键帧之间是如何变化
4. **animation-delay**:设置延时，即从元素加载完成之后到动画序列开始执行的这段时间
5. **animation-iteration-count**:设置动画重复次数， 可以指定infinite无限次重复动画infinite(无限次)
6. **animation-direction**:设置动画在每次运行完后是反向运行还是重新回到开始位置重复运行alternate(往返)|normal|reserver|
7. **animation-fill-mode**:指定动画执行前后如何为目标元素应用样式 forward（可以让动画停在最后一帧）
8. **animation-play-state**:允许暂停和恢复动画


# **oooooooooooooooooooooooook,这个博客写了我一天！！！！！！！！！！！！！！最后一颗小红心献给你[❤](http://js.jirengu.com/necet/2/edit?html,css,output)**

