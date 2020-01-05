---
title: Css Box
date: 2019-12-12T14:01:09+08:00
lastmod: 2019-12-12T14:01:09+08:00
author: FFreshman
cover: /img/css.jpg
categories: ["css"]
tags: ["css"]
# showcase: true
draft: true
---

CSS 盒模型

<!--more-->

# [CSS 盒模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)

## 一、盒模型简介

**当对一个文档进行布局（lay out）的时候，浏览器的渲染引擎会根据标准之一的 CSS 基础框盒模型（CSS basic box model），将所有元素表示为一个个矩形的盒子（box）。CSS 决定这些盒子的大小、位置以及属性（例如颜色、背景、边框尺寸…）。**

**每个盒子由四个部分（或称区域）组成，其效用由它们各自的边界（Edge）所定义。如图，与盒子的四个组成区域相对应，每个盒子有四个边界：内容边界 _Content edge_、内边距边界 _Padding Edge_、边框边界 _Border Edge_、外边框边界 _Margin Edge_。**

![](/images/boxmodel.png)

# 二、 盒模型结构介绍

## 盒模型分类

### **1.<abbr title="w3c盒模型">content-box</abbr>**

> **属性 width,height 只包含内容 content，不包含 border 和 padding。**

### **2. <abbr title="IE盒模型">border-box</abbr>**

> **属性 width,height 包含 border 和 padding，指的是 content+padding+border。**

#### 两者可以通过`box-sizing`属性切换，默认是`content-box`

## (1) content-area

> **内容区域 content area ，由内容边界限制，容纳着元素的“真实”内容，例如文本、图像，或是一个视频播放器。它的尺寸为内容宽度（或称 content-box 宽度）和内容高度（或称 content-box 高度）。它通常含有一个背景颜色（默认颜色为透明）或背景图像。**

## (2) padding-area

> **内边距区域 padding area 由内边距边界限制，扩展自内容区域，负责延伸内容区域的背景，填充元素中内容与边框的间距。它的尺寸是 padding-box 宽度 和 padding-box 高度。**

**内边距的粗细可以由 `padding-top`、`padding-right`、`padding-bottom`、`padding-left`，和简写属性 padding 控制。**

## (3) border-area

> **边框区域 border area 由边框边界限制，扩展自内边距区域，是容纳边框的区域。其尺寸为 border-box 宽度 和 border-box 高度。**

> **边框的粗细由 border-width 和简写的 `border` 属性控制。如果 `box-sizing` 属性被设为 border-box，那么边框区域的大小可明确地通过 `width`、`min-width`, `max-width`、`height`、`min-height`，和 `max-height` 属性控制。假如框盒上设有背景（background-color 或 background-image），背景将会一直延伸至边框的外沿（默认为在边框下层延伸，边框会盖在背景上）。此默认表现可通过 CSS 属性 background-clip 来改变。**

## (4) margin-area

> **外边距区域 margin area 由外边距边界限制，用空白区域扩展边框区域，以分开相邻的元素。它的尺寸为 margin-box 宽度 和 margin-box 高度。**

> **外边距区域的大小由 `margin-top`、`margin-right`、`margin-bottom`、`margin-left`，和简写属性 `margin` 控制。**

## margin 的合并现象(合并现象仅限上下 margin)

### (1)上下 block 之间的 margin

> **除最顶上与最下面的 block 元素中间的 block 会出现 margin 合并**
>
> **如果设置了属性`display：inlineblock`，那么 margin 则会分开计算不会合并**

### (2)最上下与父级 block 元素的 margin

> **如果子元素的 border 与父元素的 margin 之间没有 border、padding，或者没有设置 overflow：hidden 属性的时候，margin 会合并**

![](/images/box1.png)
![](/images/box2.png)
