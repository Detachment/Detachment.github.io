---
title: 从点击下载不兼容火狐谈起
date: 2018-09-04
updated: 2018-09-05
categories: 前端
tags:
    - 工作
    - 浏览器兼容
    - JavaScript
    - 基础
---

## 前言

&nbsp;&nbsp;&nbsp;&nbsp;最近遇到这样一个问题：点击按钮下载文件的时候，在 Safari 和 Chrome 上都没有问题，在 Firefox 和 Edge 上则无反应。一开始我以为是后者默默的把下载好的文件保存在了浏览器的默认位置导致的，直到昨天产品大佬告诉我默认文件夹并没有对应的文件，这才怀疑可能是在实现过程中有兼容性问题。

<!-- more -->

## 从 window.URL.createObjectURL(blob) 说起
点击下载的时候有一段代码是这样的：
```javascript
let a = document.createElement('a');
a.style = "display: none";
document.body.appendChild(a)
let url = window.URL.createObjectURL(blob);   
let disposition = response.headers.get('Content-Disposition');
let filename = (disposition &&disposition.replace(/attachment;filename=/,'')) || 'data.xlsx'
filename = decodeURI(filename);
a.href = url;
a.download = filename;
a.click();
```
这段代码其实很简单，就是先创建个 Blob 对象，然后点击它下载。由于之前没有接触过这个 API， 所以稍微去了解了下，发现两篇文章：[JavaScript 中 Blob 对象](https://juejin.im/entry/5937c98eac502e0068cf31ae)， [JS前端创建html或json文件并浏览器导出下载](https://www.zhangxinxu.com/wordpress/2017/07/js-text-string-download-as-html-json-file/)，比较通俗易懂的介绍了下 Blob 对象的使用方式。这一步是没有什么问题的。

自然而言的会怀疑到这个API的浏览器兼容性，然后查了一下，结果如下图所示。我是用的 Firefox 是 62 版本的，所以应该也不存在兼容性问题。
![compatibility](http://o9ybnkuir.bkt.clouddn.com/UC20180904_224947.png)

## 到事件监听
然后开始怀疑是不是点击事件没有触发。
触发一个点击事件的前提：事件绑定在元素上，那么如何将一个点击事件绑定在元素上呢？
> 以下内容引用自 [addEventListener vs onclick](https://stackoverflow.com/questions/6348494/addeventlistener-vs-onclick)         

1. Event Listeners (addEventListener and IE's attachEvent)
在 IE 9 及以前，需要用 `attachEvent` 方法来绑定点击事件：
`element.attachEvent('onclick', function() { /* 具体函数*/})`       
在其他绝大多数浏览器中，则可以用 `addEventListener` 来进行绑定：
`element.addEventListener('click', function() { /* 具体函数*/ }, false);` 
利用这种方式添加事件绑定的时候，理论上可以在同一个元素绑定无数的事件，唯一需要考虑的就是性能问题以及客户端的内存，这些就都和浏览器有关了。
上面的例子中添加的函数都是匿名函数，其实可以先声明一个函数，然后通过函数引用的方式来绑定事件：
    ```javascript
    var myFunctionReference = function() { /* do stuff here*/ }
    element.attachEvent('onclick', myFunctionReference);
    element.addEventListener('click', myFunctionReference , false);
    ```
    利用  `addEventListener` 进行绑定的时候需要传第三个参数，这个参数是用来控制事件是否冒泡的。在  `attachEvent` 方法中没有此参数。     
2. Inline events (HTML onclick="" property and element.onclick)
在支持 JavaScript 的浏览器中，我们可以在元素上加上事件监听函数，方法如下：
`<a id="testing" href="#" onclick="alert('did stuff inline');">Click me</a>`
虽然大部分有经验的程序员都很少用这种方式，但这种方式确实也可以达到目的，而且简单直接。这种写法的缺点也显而易见：函数必须要非常简单。
另外一种写法是：
`element.onclick = function () { /*do stuff here */ };`
这种写法和上面其实是等价的，不过这样写的话函数的复杂程度就可以大大提高了。
利用行间事件的写法有一个很明显的缺点：每一个元素都只能有一个对应的事件，事件是作为元素的属性存储的，这样一来如果有多个同样的事件，那么前者就会被后者覆盖：
    ```javascript
    var element = document.getElementById('testing');
    element.onclick = function () { alert('did stuff #1'); };
    element.onclick = function () { alert('did stuff #2'); };
    ```
	上面这段代码执行的时候，只有第二个函数会执行，因为第一个事件被覆盖掉了。

## 问题解决
上面两个点都没有解决到实际的问题，最后终于在 stackOverflow 上看到了一个问题: [Blob createObjectURL download not working in Firefox (but works when debugging)](https://stackoverflow.com/questions/30694453/blob-createobjecturl-download-not-working-in-firefox-but-works-when-debugging) 利用里面提到的解决方案顺利解决了这个兼容性问题。