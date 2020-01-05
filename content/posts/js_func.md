---

title: JS 函数
date: 2020-01-02T20:04:21+08:00
lastmod: 2020-01-02T20:04:21+08:00
author: FFreshman
cover: /img/this.png
categories: ["JavaScript"]
tags: ["JavaScript"]

# showcase: true

---# JS 函数

<!--more-->

## **在 JS 中，函数也是一种对象，他拥有以下几种要素**

1. **调用时机**
2. **作用域**
3. **闭包**
4. **形式参数**
5. **返回值**
6. **调用栈**
7. **函数提升**
8. **argument （箭头函数除外）**
9. **this （箭头函数除外）**

### **接下来会重点介绍一下调用时机以及`this`**

# 一、函数的调用时机

### 当一个函数被写好以后，并不会马上执行，而是等待被调用，所以什么时候被调用就决定了函数的输出结果是什么

# **exm1:**

```js
let a = 1;
function fn() {
  console.log(a);
}
fn();
```

### 这时候会在控制台打印出数字`1`

# **exm2:**

```js
let a = 1;
function fn() {
  console.log(a);
}
a = 2;
fn();
```

### 这时候会在控制台打印出数字`2`，因为`fn()`的调用时间在`a=2`之后，这时候 a 已经被重新赋值为 2 了，所以输出结果是 2，如果这里`fn()`调用在`a=2`之前，则会输出 1

# **exm3:**

```js
let a = 1;
function fn() {
  setTimeout(() => {
    console.log(a);
  }, 0);
}

fn();
a = 2;
```

### 这个代码会输出**2**，因为 setTimeout()这个函数的意思是等一会执行，所以当你调用 fn()的时候并不会马上输出 a，而是继续执行`a=2`，然后才执行`console.log(a)`

# **exm4:**

```js
let i = 0;
for (i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

### 以上代码的输出结果是 6 个 6，是不是跟你预期的 0-5 有出入

### 原因是``setTimeout()``函数回调属于异步任务，会出现在宏任务队列中，被压到了任务队列的最后，在这段代码应该是for循环这个同步任务执行完成后才会轮到它
### 简单来说当循环执行到`setTimeout()`的时候并不会马上打印出 i，而是会记下一个事件，”我等下要把`i`打一次“，然后会继续执行循环，

### 当 for 循环结束的时候，这时候 i 的值是 6，然后`setTimeout()`开始执行，因为刚才循环了 6 次，所以会将这个语句也执行 6 次，这时候会把`i`的值打印出来，但是这时候`i=6`，所以他就连续打了 6 个 6，是不是 666666。

### 但是这种性质其实对新人非常不友好，因为他是反直觉的，所以在最新版的 JS 语法中，做了一个微调

# **exm5:**

```js
for (let i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

### 将`let i=0`放到 for 的条件里之后，情况发生了改变，这时候的输出结果就是一般人认为的，0-5 的输出 6 个数字

## 其实这个问题还有另一种解决方法，那就是立即执行函数和闭包
```js
for (let i = 0; i < 6; i++) {
  (function fn(i){setTimeout(() => {
    console.log(i);
  }, 0);})(i)
}
```
### 在闭包函数内部形成局部作用域，不受外界变量变化的影响
![](/images/js/js1/jsf/2.png)

# 二、this

### 首先我们会问，这 this 到底是个什么，试着写一个函数，然后查看他的 this，我们可以看到 this 属性默认是指向 window，要了解他到底是什么我们可以从他的由来和作用入手

![](/images/js/js1/jsf/1.png)

### 加入我们现在要写一个构造函数或者一个 class，我们想要调用将来要创建的对象的属性该怎么办呢，又或者我们在声明一个在声明一个对象的时候调用了这个对象的属性，这时候我们还不知道我们将要创建一个什么对象，这时候我们可以想到，可以设置一个形参给需要得到未知对象属性的函数中，然后在未知对象调用某个函数时，将这个对象的名字作为参数传到函数中，就可以实现这个功能了。

```js
let person = {
  name: "fish",
  sayHi(p) {
    console.log("大家好我是" + p.name);
  }
};
```

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  sayHi(p) {
    console.log("大家好我是" + p.name);
  }
}
```

## 这样的话当我们需要调用 sayHi 的时候就可以这样写

```js
person.sayHi(person);
```

## 这时候`person`这个对象就作为 p 参数传入了`sayHi()`，那`p.name===person.name==="fish"`

## 其实 this 就是那个形参 p，只不过 JS 把 this 作为一个关键词而把他从函数的参数中隐藏了

```js
let person = {
  name: "fish",
  sayHi(省略this) {
    console.log("大家好我是" + p.name);
  }
};
```

## 这时候我们使用`person.sayHi()`就可以直接调用函数，这是因为 JS 会默认把`person`当做 this 传入`sayHi()`

## 当然我们可以自定义传入的 this 是什么使用`person.sayHi.call(person)`，又或者我们可以直接改掉这个 person 传入另外一个`person.sayHi.call({name:"batman"})`，这时候你会发现，输出结果就是“大家好我是 batman”，因为实际上传入的 this 是对象`{name:"batman"}`，他的 name 属性是``{name:"batman"}.name==="batman"

## 所以其实所以函数都可以用 obj.function.call(undefined,a,b,...)的形式来调用，其中的第一个参数就是 this，如果目标函数没有 this，那么可以用一个其他属性来占位，因为如果不占据这个 this 的位置，后一个参数会被当成 this 传入，a,b...就是目标函数的其余参数，这种调用函数的方法可以帮助你深刻理解 this 是什么
