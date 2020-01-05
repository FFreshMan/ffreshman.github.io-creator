---
title: JavaScript
date: 2019-12-20T18:54:53+08:00
lastmod: 2019-12-20T18:54:53+08:00
author: FFreshman
cover: /img/js.png
categories: ["JavaScript"]
tags: ["JavaScript"]
# showcase: true
draft: true
---

# <font color=#FF0000>JavaScript 的诞生</font>

<!--more-->

## 一、 JavaScript

**JavaScript 因为互联网而生，紧随着浏览器的出现而问世。回顾它的历史，就要从浏览器的历史讲起。**

**1990 年底，欧洲核能研究组织（CERN）科学家 Tim Berners-Lee，在全世界最大的电脑网络——互联网的基础上，发明了万维网（World Wide Web），从此可以在网上浏览网页文件。最早的网页只能在操作系统的终端里浏览，也就是说只能使用命令行操作，网页都是在字符窗口中显示，这当然非常不方便。**

**1992 年底，美国国家超级电脑应用中心（NCSA）开始开发一个独立的浏览器，叫做 Mosaic。这是人类历史上第一个浏览器，从此网页可以在图形界面的窗口浏览。**

![](http://www.chuanboxue.org/uploads/05/1274974813B7jpRDJw.jpg)

**1994 年 10 月，NCSA 的一个主要程序员 Marc Andreessen 联合风险投资家 Jim Clark，成立了 Mosaic 通信公司（Mosaic Communications），不久后改名为 Netscape。这家公司的方向，就是在 Mosaic 的基础上，开发面向普通用户的新一代的浏览器 Netscape Navigator。**

**Netscape 公司很快发现，Navigator 浏览器需要一种可以嵌入网页的脚本语言，用来控制浏览器行为。当时，网速很慢而且上网费很贵，有些操作不宜在服务器端完成。比如，如果用户忘记填写“用户名”，就点了“发送”按钮，到服务器再发现这一点就有点太晚了，最好能在用户发出数据之前，就告诉用户“请填写用户名”。这就需要在网页中嵌入小程序，让浏览器检查每一栏是否都填写了。**

**1995 年，Netscape 公司雇佣了程序员 [Brendan Eich ](https://baike.baidu.com/item/Brendan%20Eich/561441?fr=aladdin) 开发这种网页脚本语言。Brendan Eich 有很强的函数式编程背景，希望以 Scheme 语言（函数式语言鼻祖 LISP 语言的一种方言）为蓝本，实现这种新语言。**

![](/images/js/js1/eich.png)
![](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcROmYMj9gEXKwqNU_GYL7ArQ5fp2J65e4N1CY44jHEQGAoVAdcd)

**1995 年 5 月，Brendan Eich 只用了 10 天，就设计完成了这种语言的第一版，这也为 JavaScript 后来存在的缺陷埋下了伏笔。它是一个大杂烩，语法有多个来源：**

> 基本语法：借鉴 C 语言和 Java 语言

> 数据结构：借鉴 Java 语言，包括将值分成原始值和对象两大类

> 函数的用法：借鉴 Scheme 语言和 Awk 语言，将函数当作第一等公民，并引入闭包

> 原型继承模型：借鉴 Self 语言（Smalltalk 的一种变种）

> 正则表达式：借鉴 Perl 语言

> 字符串和数组处理：借鉴 Python 语言

**1995 年 12 月 4 日，Netscape 公司与 Sun 公司联合发布了 JavaScript 语言。当时的意图是将 JavaScript 作为 Java 的补充，用来操作网页。**

**所以 JavaScript 的编程风格是函数式编程和面向对象编程的一种混合体。**

## 二、 JavaScript 与 Java 的关系

**其实吧 Netscape 公司的这种浏览器脚本语言，最初名字叫做 Mocha(摩卡咖啡)，1995 年 9 月改为 LiveScript。12 月，Netscape 公司与 Sun 公司（Java 语言的发明者和所有者）达成协议，后者允许将这种语言叫做 JavaScript。这样一来，Netscape 公司可以借助 Java 语言的声势，而 Sun 公司则将自己的影响力扩展到了浏览器。**

**之所以起这个名字，并不是因为 JavaScript 本身与 Java 语言有多么深的关系（事实上，两者关系并不深），而是因为 Netscape 公司已经决定，使用 Java 语言开发网络应用程序，JavaScript 可以像胶水一样，将各个部分连接起来。当然，后来的历史是 Java 语言的浏览器插件失败了，JavaScript 反而发扬光大。**
![](https://i0.wp.com/www.lightblue.asia/wp-content/uploads/2016/11/java-logo.png?fit=357%2C225&ssl=1)

**JavaScript 的基本语法和对象体系，是模仿 Java 而设计的。但是，JavaScript 没有采用 Java 的静态类型。正是因为 JavaScript 与 Java 有很大的相似性，所以这门语言才从一开始的 LiveScript 改名为 JavaScript。基本上，JavaScript 这个名字的原意是“#FF0000}{很像 Java 的脚本语言”。**

## 三、 JavaScript 与 ECMAScript 的关系

**1996 年 8 月，微软模仿 JavaScript 开发了一种相近的语言，取名为 JScript（JavaScript 是 Netscape 的注册商标，微软不能用），首先内置于 IE 3.0。Netscape 公司面临丧失浏览器脚本语言的主导权的局面。**

**1996 年 11 月，Netscape 公司决定将 JavaScript 提交给国际标准化组织 ECMA（European Computer Manufacturers Association），希望 JavaScript 能够成为国际标准，以此抵抗微软。**

![](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSTVXk5LyqjCY6OA-z9gM32w3izd2uwxqmQ3yN9MZLk7xYhHcKH)

**1997 年 7 月，ECMA 组织发布 262 号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言称为 ECMAScript。这个版本就是 ECMAScript 1.0 版。之所以不叫 JavaScript，一方面是由于商标的关系，Java 是 Sun 公司的商标，根据一份授权协议，只有 Netscape 公司可以合法地使用 JavaScript 这个名字，且 JavaScript 已经被 Netscape 公司注册为商标，另一方面也是想体现这门语言的制定者是 ECMA，不是 Netscape，这样有利于保证这门语言的开放性和中立性。因此，ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现。在日常场合，这两个词是可以互换的。**

### **简单来说就是 ECMAScript 只用来标准化 JavaScript 这种语言的基本语法结构，与部署环境相关的标准都由其他标准规定，比如 DOM 的标准就是由 W3C 组织（World Wide Web Consortium）制定的。**

## 四、 JavaScript 的发展历程

**1997 年 6 月第一版 ECMAScript 发布**

**1999 年 12 月第三版发布，这也是至今使用最广泛的版本，之后还计划出第四版，但是因为第四版加入过多功能导致最后被抛弃。**

**2009 年 12 月才发布了第五版 ECMAScript，从 1999 到 2009 之间，JavaScript 可以说是经历了长达 10 年的停滞期，这其中的原因和微软的 IE 浏览器脱不了关系。**

**2001 年 IE6 随着 WindowsXP 一起发布，系统内嵌了 IE6 浏览器，这使得当时 IE 的时长份额高达 80%以上，一度到达 95%，由于 IE6 缺不兼容 W3C 中的 CSS 标准，使得前端发展举步维艰。**

**2008 年终于，Chrome 横空出世，并开始占据市场份额，这时候 ECMAScript 才计划发布第五版标准，同时加入了一些功能。**

**2015 年 6 月随着智能手机时代的来临，IE 已基本失去手机市场，而 Chrome 此时的市场份额达到了 62%，从此 JavaScript 的进入了极速发展时期。同期 ECMAScript 第 6 版发布。此后每年发布一版，并以年份命名。**

![](https://cdn.educba.com/academy/wp-content/uploads/2018/08/ES6-Interview-questions.jpg)

## 总结

**JavaScript 从一个仅仅花了 10 天开发的只能实现简单功能的语言，到现在能运行在各大服务器上，同时在 WebAssembly 的支持下能将任何语言编译成 JavaScript 运行在浏览器上，足以见得其生命力之强大与潜力之广阔，纵使因为历史原因，使得这门语言并不完美，也存在许多缺陷，但是在未来的发展中，随着第三方库的支持，JavaScript 的功能会愈发强大。十八世纪英国文学家约翰逊博士说过**<abbr title="它的优秀之处并非原创，它的原创之处并不优秀">**The part that is good is not original, and the part that is original is not good**</abbr>
