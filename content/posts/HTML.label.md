---
title: HTML
date: 2019-12-09T21:40:04+08:00
lastmod: 2019-12-09T21:40:04+08:00
author: FFreshman
cover: /img/timg.jpg
categories: ["HTML"]
tags: ["HTML"]
# showcase: true
draft: false
---

一些常用HTML标签的使用

<!--more-->

# 常用HTML标签

# 一、````<a>````标签
## ````<a>````有哪些属性
## （1）href
href是hyper reference的缩写，根据href的值不同，a标签又以下几种功能。

在预览自己html文件的时候建议使用
````
http-server -c-1
````
然后在推荐域名后加想要打开的html文件路径，根目录即http-server打开的目录比如
http://127.0.0.1:8081/index.html

### ①网址
````html
<a href="//baidu.com">超链接</a>
````
用//baidu.com可以让浏览器自行选择http或者https协议，不容易出问题

### ②路径
比如相对路径a/b/c，又或者/a/b/c,此时/a不代表根目录而代表代表http-server的打开目录。比如

    a/b/c/index.html
### ③伪协议
* javascript:代表可以连接到js
* mailto：链接到发送邮件
* tel：拨号
* id：可以连接到指定id的标签位置比如
  ````html
  <a href="#123">跳到123</a>
  `````
## （2）target
target标签代表点击此链接后打开新页面的位置，有一下几个值
### ①_blank
代表在新窗口打开链接
### ②_top
top属性比较复杂，一般在有iframe标签的时候使用比如
````html
<a href="//baidu.com">baidu</a>
    <div>
      <iframe src="a-iframe.html" frameborder="0"></iframe>
    </div>
````
iframe标签可以实现在原网页上再新开一个小窗口，他的source指向另一个html，当他引用的html中有a标签时，就可以选择top属性如
````html
<body bgcolor="red">
    我是iframe
    <a href="//baidu.com" target="_top">top</a>
    <iframe src="a-iframe2.html" frameborder="0">1</iframe>
</body>
````
top则会在最顶级窗口打开链接，如果设置为_self则在iframe中打开窗口
### ③_self
target设置为self属性则会在原窗口打开链接而不会新建窗口
### ④_parent
parent属性与top属性类似，只不过会用在多级iframe引用的时候，子级iframe的链接会在他的上一级窗口打开，而top则是在最外层即顶级窗口打开。
### ⑤ xxx
xxx代表一个确定的name可以是任意的只要不保留字冲突，如果两个两个a标签的target是同一个，则会在同一个窗口打开链接而不会另外新建窗口
### ⑥iframe-name
如果target的属性是iframe的name属性则会在相应的iframe中打开链接

# 二、````<table>````标签
## （1）````<table>````标签的基本结构
````html
 <table border="1">
      <thead>
        <tr>
          <th>表头1</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td>2</td>
        </tr>
      </tfoot>
    </table>
    <hr />
````
基本结构有4部分、````<table>````、````<thead>````、````<tbody>````、````<tfoot>````，用````<tr>````标签代表table-row也就是行，每行中如果是表头部分则用````<th>````标签，代表的是table-head，其余则用````<td>````代表的是table-data。

## （2）````<table>````的属性
### ① table-layout
* auto 代表单元格大小随内容大小变化
* fixed 代表尽量让单元格大小等大

### ② border-collapse
这个代表的是让单元格两条边框合并为一条或者分开，有collapse和separate两个值
````html
<table border-collapse:collapse>
````
### ③ border-spacing
指的是单元格边框的距离，一般在border-collapse为separate的时候使用
当border-collapse为0的时候也可以实现边框合并的效果

# 三、````<img>````
## （1） 作用
````html
<img src="" alt="" height="" width="" >
````
使用img标签会发出get请求获取src中的图片
## （2）属性
属性有以下几个
1. src (source)用于指示图片的引用路径可以
2. alt (alternative)当图片加载失败的时候可以显示的内容，可以是文字也可以是其他图片
3. width 宽度
4. height 高度
## （3）跟img有关的事件
    onload/onerror
````html
<img id="123" src="1.img" alt="">
<script>
    123.onerror=function{
        console.log("加载成功")
    }
</script>
````
可以被js调用
## （4）响应式布局
可以在css中设置
````html
<style>
    img{
        max-width:100%;
    }
<style>
````
# HTML的标签还有很多，如input，form等