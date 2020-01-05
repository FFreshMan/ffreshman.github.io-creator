---
title: Js_object
date: 2019-12-26T17:30:56+08:00
lastmod: 2019-12-26T17:30:56+08:00
author: FFreshman
cover: /img/co.png
categories: ["JavaScript"]
tags: ["JavaScript"]
# showcase: true
---## JS 对象

<!--more-->

### **在 javascript 中，一个对象可以是一个单独的拥有属性和类型的实体。我们拿它和一个杯子做下类比。一个杯子是一个对象(物体)，拥有属性。杯子有颜色，图案，重量，由什么材质构成等等。同样，javascript 对象也有属性来定义它的特征。**

## 一、声明一个对象

**如何声明一个对象**

```js
let obj = { key1: "value1", key2: "value2" };
```

**其中**

- obj 是对象的名称，可以是任意标识符
- key 是对象的键名，类型总是 string，一般加上双引号""，如果省略则可以是合法标识符和数字，symbol 也能做为键名
- value 是对应键名的值，可以是任意类型

### 下面介绍几种特殊的键名（属性名 property）

### (1)表达式做属性名

例如

```js
Let obj={[1+2+3]:"10"}
let obj={1e2:"10"}

```

上述语句等价于

```js
Let obj={[10]:"10"}
let obj={100:"10"}
```

**这是因为对象的属性名始终是 string 类型，所以如果去掉引号，会被强制转成 string 类型，这时候数字或者数学表达式就会默认变成 10 进制，所以保险起见，最好别省略""**

### (2)变量做属性名

上述的属性名都是常量，但是要传入一个变量作为属性名应该怎么做呢

```js
let p1 = "name";
let obj = { [p1]: "freshman" };
```

这样的写法会先求出 p1 的值，即"name"，然后再传入属性名中等价于

```js
let obj = { name: "freshman" };
```

但是要注意如果

```js
let obj = { p1: "freshman" };
```

那么实际上，属性名还是 p1，并不会传入 name 作为属性名

## 二、 属性的增、删、改、查

### (1) 查属性

**在 js 中，是用[原型链](http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html)来定义一个对象的类的，所以一个对象有基于原型的共有属性（prototype）和自身的私有属性（OwnProperty）**

1. 查看自身属性名

```js
Object.keys(obj);
```

2. 查看自身属性值

```js
Object.values(obj);
```

3. 查看所有属性结构

```js
Console.dir(obj);
```

这里会打印出对象的私有属性和原型*proto*

4. 用数组的方式查看键值对

```JavaScript
Object.entries(obj);
```

5. 如何判断一个属性是否是私有属性呢

```JavaScript
name.hasOwnProperty("key");
```

可以查询 key 属性是否是 name 对象的私有属性，若为 true 则是，false 则不是。

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1577444744306&di=78e27d46a9fb51c63bf94d5b4481c702&imgtype=0&src=http%3A%2F%2Fwww.vvfeng.com%2Fdata%2Fupload%2Fueditor%2F20170223%2F58ae7afd7818c.jpg)

### 那么如何查看单独的一个属性呢

1. 中括号语法

```js
obj["key"];
```

等价于

2. 点语法

```JavaScript
obj.key;
```

但是和

```js
obj[key];
```

并不相等，`obj[key]`代表的是变量 key 的属性值。

### (2) 删属性

```js
delete obj.name;
delete obj["name"];
```

这里的注意点和上文的相同，[]中省略""代表的是变量，而不是字符串的属性名

**如何查看属性是否还在对象中呢**

```js
“xxx” in obj
```

### (3)增加和修改属性

1. 中括号

```js
obj.key1 = "a";
```

2. 点语法

```js
obj["key1"] = "a";
```

3. 传入变量

```js
let x = "key1";
obj[x] = "a";
```

**这里要强调的问题同上，`obj.x`等价于`obj["x"]`而不等价于`obj[x]`，所以要深刻理解属性名是 string 类型这个点。**

4. 写入多个属性

```js
Object.assign(obj, { k1: 1, k2: 2, k3: 3 });
```

## 三、 原型链和原型

**如果我想要修改一个属性的原型该怎么办呢
如果只是在对象上写入某个与原型同名的属性，那么并不会影响到原型的属性，这是因为原型的读写权限不一致决定的，而且就算改变了对象原型的某个属性，对象再次定义这个属性的属性值，此时重新定义的属性会覆盖原型的属性，可以做一个小实验**

![](/images/js/js1/ts.png)

**但是！尽量别更改对象的原型，如果非要更改可以选择更改`window.Object.prototype`**

![](/images/js/js1/ts2.png)

### 接下来讲一下原型链的使用

```js
let common = { kind: "human" };
let obj = Object.create(common);
```

![](/images/js/js1/ts3.png)

**用 `Object.create()`能以某个对象为原型生成一个对象，那么这个新对象 obj 的原型就是 common，他的`_proto_`隐藏属性就是 common，同时 common 也是一个对象，也有自己的隐藏属性，他的`_proto_`指向对象的根原型。**
