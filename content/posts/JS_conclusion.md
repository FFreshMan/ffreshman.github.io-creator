---
title: JS_conclusion
date: 2020-01-05T18:28:58+08:00
lastmod: 2020-01-05T18:28:58+08:00
author: FFreshman
cover: /img/cover.jpg
categories: ["JavaScript"]
tags: [ "JavaScript"]
# showcase: true

---

JS难点总结

<!--more-->

## **这里我们先总结一下3条公式，等下会一一解释**
## LAW(1) 
![](/images/js/js1/jsf/11.png)
## [LAW(2)]()
![](/images/js/js1/jsf/22.png)
## LAW(3) 
![](/images/js/js1/jsf/33.png)

## **接下来我们从0开始构建一个JS世界**

### (1)我们需要创建一个根对象，他是所有对象的祖先[[#268](JavaScript:;)]
![](/images/js/js1/jsf/1/1.png)
### (2)接下来创建的是函数的原型对象[[#306](JavaScript:;)]和数组的原型对象[[#146](JavaScript:;)]
![](/images/js/js1/jsf/1/2.png) ![](/images/js/js1/jsf/1/3.png)
### (3)有了基本的原型对象以后，我们需要创建一个所有函数的构造者``Function``[[#66](JavaScript:;)]
![](/images/js/js1/jsf/1/4.png)
### 这个函数的构造函数``Function``是以函数对象[[#306](JavaScript:;)]为原型创建的，所以，他的_proto_属性就是[[#306](JavaScript:;)]
### 当这个构造函数去创建另一个函数f1()的时候，他会把所创建的函数的原型也就是``f1._proto_``指向函数的原型[[#306](JavaScript:;)]
### 其实每个函数都拥有一个prototype属性，他的意思是我会把我创建的对象的原型指向哪，所以此时``Function.prototype``就等于函数的原型对象[[#306](JavaScript:;)]
### 这时候就得出了LAW(2)，此时你会发现``Function._proto_``和``Function.prototype``的值是相等的
![](/images/js/js1/jsf/1/5.png)
### 那么带入[公式2]()，我们是不是就可以得出``Function``的构造者就是他自己呢，但是其实``Function``是一开始由JS构造的，他都不存在又如何能构造自己呢，只不过被构造出来之后，被赋予了使命去构造其他的所有函数，这就有了[LAW(2)]()，但是为了统一成[LAW(3)]()，就指定了``Function``的构造者就是他自己

### (4)现在我们有了所有函数的构造函数``Function``，就可以去创建其他的函数了，比如构造对象的函数``Object``[[#24](JavaScript:;)]和构造数组的函数``Array``[[#58](JavaScript:;)]
![](/images/js/js1/jsf/1/7.png) ![](/images/js/js1/jsf/1/6.png)

### 由于他们都是由``Function``以函数的原型[[#306](JavaScript:;)](``Function.prototype``)构造出来的，所以他们的``_proto_``属性都是[[#306](JavaScript:;)]，由于他们俩都是构造函数，是用来构建其他对象的函数
### 他们以对象的原型对象[[#268](JavaScript:;)]和数组的原型对象[[#146](JavaScript:;)]作为他们创建的子对象的原型，所以他们的``Object.prototype``属性和``Array.prototype``属性就存储着他们将要创建子对象的原型

## 自此我们基本上就把整个JS世界构建完成了
![](/images/js/js1/jsf/1/777.png)

## 这里要说明一点，那就是JS在创建一个对象的时候是不会给予他名字的，我们上面所提到的函数，原型等都只是一个储存在内存里的一块区域而已，他们没有名字，只是拥有一个地址来寻址而已
## 这时候我们引入了一个浏览器所提供的window，然后把上面的对象挂在到window对象上，这样就得到了其他对象的名字
### 比如 ``window.Object.prototyp``e指的就是我们上面提到的根对象[[#268](JavaScript:;)]，由于所有的对象都有其原型``_proto_``，根对象也不例外，但是他已经是根对象了，所以认为的规定了他的原型``_proto_===null``
