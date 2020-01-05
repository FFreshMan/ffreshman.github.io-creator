---
title: URL
date: 2019-12-18T15:32:12+08:00
lastmod: 2019-12-18T15:32:12+08:00
author: FFreshman
cover: /img/URL.png
categories: ["HTTP"]
tags: ["URL", "HTTP"]
# showcase: true
draft: false
---

URL 的基础知识

<!--more-->

### **首先我们要访问一个网页会经历哪些过程**

![](/images/HTTP/DNS.png)

### 总结一下有以下几个过程

1. DNS 解析:将域名（URL）解析成 IP 地址
2. TCP 连接：TCP 三次握手
3. 发送 HTTP 请求
4. 服务器处理请求并返回 HTTP 报文
5. 浏览器解析渲染页面
6. 断开连接：TCP 四次挥手

## (1)**IP**

**互联网协议（Internet Protocol ，是分配给网络上使用网际协议）的设备的数字标签。常见的 IP 地址分为 IPv4 与 IPv6 两大类，但是也有其他不常用的小分类。**
**ip 又分为公网 ip 和局域网 ip（比如你的 wifi），通俗来讲就是给世界上每个能相互通信的设备都编个号，这样我就可以顺这个号码来找到你。**

**在 shell 中输入`ping www.baidu.com`就可以知道你是否能访问这个 IP，延迟是多少**

## (2)**<abbr title="Uniform Resource Locator">URL</abbr>**

URL，统一资源定位符，用于定位互联网上资源，俗称网址。 比如 "http://www.google.com/html/index.asp"，遵守以下的语法规则：

**scheme://host.domain:port/path/filename**

1. scheme - 定义因特网服务的类型。常见的协议有 http、https、ftp、file，其中最常见的类型是 http，而 https 则是进行加密的网络传输。
2. host - 定义域主机（http 的默认主机是 www）
3. domain - 定义因特网域名，比如 w3school.com.cn
4. port - 定义主机上的端口号（http 的默认端口号是 80,https 默认是 443，FTP 默 21 端口）
5. path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）
6. filename - 定义文档/资源的名称

## (3)**DNS**

DNS，全称 Domain Name System(service)，是一个域名系统，我们输入的网址并不能帮我们访问到应该去的服务器获取资源，因为我们没有该服务器的 ip 地址，所以就需要一个能帮我们找到该域名对应服务器 ip 的系统。

![](/images/HTTP/DNS2.png)

### **这个过程也分几个步骤：**

1. 先到本地的 hosts(C:\Windows\System32\drivers\etc\hosts) 文件中查看 ip 和域名的映射
2. 若 hosts 没有，则找本地 dns 缓存
3. 若 hosts 与本地 dns 缓存都没有，则找 tcp/ip 参数中设置的首选 dns 服务器，在此我们叫它本地 dns 服务器，此服务器收到查询时，若要查询的域包含在本地配置资源中，则返回
4. 若要查询的域名不是本地 dns 解析，但该服务器已经缓存了此网址映射关系，则调用这个 ip 地址映射
5. 若本地资源和缓存里都没有，则根据本地 dns 服务器的设置（是否设置转发器）进行查询
6. 如果该域名绑定了多个 ip，那么 DNS 服务器一般会访问一个 nginx 服务器，再由其根据分配策略向相应的服务器 ip 发起请求，这就是 SLB（负载均衡）

**Tip**

在 shell 中输入`nslookup baidu.com`就可以获取到此域名对应的 ip

## (4)域名

**上面所说的 URL，俗称网址并不等于域名，URL 中包括了域名，那么域名到底是什么呢**

域名可以说是一个 IP 地址的代称，目的是为了便于记忆后者。例如，wikipedia.org 是一个域名，和 IP 地址 208.80.152.2 相对应。人们可以直接访问 wikipedia.org 来代替 IP 地址，然后域名系统（DNS）就会将它转化成便于机器识别的 IP 地址。这样，人们只需要记忆 wikipedia.org 这一串带有特殊含义的字符，而不需要记忆没有含义的数字

### 域名分为顶级域名和子级域名

### 1、 顶级域名

![](/images/HTTP/9in.jpg)

- .com 商业，现在成为全球注册量最大、最通用的域名，company
- .gov 政府，现被用于政府的网站
- .edu 教育机构，

* .mil 军事，现被用于国防部及其附属机构的网站
* .org 非营利组织

### 2、 子域名

子域名将顶级域名进一步细分。域名层次结构中，顶级域名下面是二级域名，它位于顶级域名的左侧。例如，在 zh.wikipedia.org 中，wikipedia 是二级域名。w3.org 中，w3 也是二级域名，与前例中的 wikipedia 属于一个层面。
