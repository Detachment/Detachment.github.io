---
title: 《jQuery学习教程》
date: 2016-07-31
updated: 2016-08-01
categories: 前端
tags:
    - jQuery
    - 基础
    - 前端
---

## 前言
&nbsp;&nbsp;&nbsp;&nbsp;网上学习JS的过程告一段落，然后就马不停蹄的开始找JS框架和库的教程（感觉知乎上很多学习课程都是不负责任推荐，有点怀疑他们本身有没有看过那些推荐的教程。当然了，也可能是那些课程仅仅是不适合我。），找了一圈下来（网易云课堂、慕课网、极客学院、codecademy、free code camp等）没有发现适合的，要么讲的太简单了，要么信息量太大了。这时候，终于想起了w3school。以下的学习内容大部分都是基于这上面的，需要更详细的内容可以上[w3school](http://www.w3school.com.cn/jquery)查看。

<!---more--->

## 课程章节
### jQuery介绍
#### 关键词：简介、安装、语法、选择器、事件、名称冲突
- **简介**：jQuery是一个轻量级的JavaScript库，能极大的简化JavaScript编程，宗旨是“write less, do more”；包含的功能非常多（1. HTML元素选取；2. HTML元素操作；3. CSS操作；4. HTML事件函数；5. JavaScript特效和动画；6. HTML DOM遍历和修改；7. AJAX；8. Utilities；）；
- **安装**：可以将jQuery库下载到本地引用，也可以直接引用Microsoft或者google的CDN；使用引用CDN的方式有一个很大的优势就是许多用户在访问其他站点的时候已经加载过jQuery，结果就是当这些人访问站点时，会直接从缓存中加载jQuery，从而减少加载时间。而且，大多数CDN都可以确保用户在请求文件时，从最近的服务器上返回响应，从而提高加载速度；
- **语法**：语法形式为`$(selector).action()`，其中美元符号定义了jQuery，选择符（seclector）查询出符合条件的html元素，action函数对筛选出来的元素进行操作；举个最常见的例子：`$(document).ready(function(){});`这段代码表示在整个页面加载完成后再执行其中的操作；
- **选择器**：常见的选择器有以下几种：
    1. 元素选择器：例如`$('p')`表示选取`<p>`元素；`$('p.intro')`表示选择类别为intro的`<p>`元素；
    2. 属性选择器：例如`$("[href]")`表示选取所有带有href属性的元素；`$("[href='#']")`表示选择所有带有href值等于#的元素；`$("[href$='.jpg']")`表示选择所有href值以.jpg结尾的元素；
    3. 更多是选择器参考[jQuery选择器手册](http://www.w3school.com.cn/jquery/jquery_ref_selectors.asp)。
- **事件**：jQuery事件处理方法是jQuery的核心函数，事件处理程序指的是当HTML中发生某些事件所调用的方法，也叫作“触发”；（通常把jQuery代码放在`<head>`部分的事件处理方法中；详细的事件参考[jQuery事件手册](http://www.w3school.com.cn/jquery/jquery_ref_events.asp)
- **名称冲突**：由于其他库也可能使用`$`符号，那么就会引起冲突，jQuery中使用`noConflict()`方法来解决这个问题；
- **注意**：为了使代码更容易维护，以下事项需要注意：
    1. 把所有的jQuery代码置于事件处理函数中；
    2. 把所有事件处理函数置于文档就绪事件处理器中；
    3. 把jQuery代码置于单独的`.js`文件中;
    4. 如果存在名称冲突，则重命名jQuery库；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/akawvG/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/akawvG/'>jQuery01</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 注意：由于CodePen后台提供了jQuery的链接，所以在面板上看不到引入库的这一段代码。

#### 小测试
本节主要是关于jQuery的简单介绍，其中选择器及事件为重点内容，可以查看手册后挑几个练习，使得具有最基本的功能：
> 1. 下载jQuery库后本地引用或者直接引用链接；
2. 具有基本的选择器及事件函数；

---

### jQuery效果
#### 关键词：隐藏显示，淡入淡出，滑动，动画，stop()，Callback, Chaining
- **隐藏显示**：方法为`hide(), show()`，使用语法为`$(selector).hide(speed, callback)`，其中speed可以是slow，fast或者毫秒；而callback表示的是完成这个动作之后执行的函数；除了这两个方法之外，可以用`toggle()`的方法来切换显示隐藏，效果不错；
- **淡入淡出**：方法为`fadeIn(), fadeOut(), fadeToggle(), fadeTo()`，使用语法为`$(selector).fadeIn(speed, callback)`，其中speed和callback的理解和上面的一样；其中`fadeTo()`方法略有不同，语法为`$(selector).fadeTo(speed,opacity,callback)`，表示的是将选择出的元素的透明度变成目标值；
- **滑动**：方法为`slideDown(), slideUp(), slideToggle()`使用语法为`$(selector).slideDown(speed, callback)`，其中speed和callback的解释同上；
- **动画**：方法为`animate()`，使用语法为`$(selector).animate({params}, speed, callback)`，其中params参数定义形成动画的css属性，speed和callback的含义解释同上；其中属性的动画值可以设置成`"show","hide","toggle"`，具体见实例；如果需要实现步骤有先后的动画，那么可以通过编写多个animate()方法，jQuery就会逐一运行这些代码，这种功能叫做队列功能；animate方法几乎能操作所有的CSS属性，但是需要注意的是需要使用Camel标记法来书写属性名，比如paddingLeft,marginRight等；
- **stop()**: 此方法用于停止动画或者效果，适用于所有jQuery效果函数，语法为`$(selector).stop(stopAll,goToEnd)`，其中可选参数stopAll规定是否应该清除动画队列，默认是false，即仅停止活动的动画，但允许队列中的其他动画执行；可选参数goToEnd表示是否立即完成当前动画，默认为false；
- **Callback**：此函数在当前动画100%完成之后执行；因为JS语句是逐一执行的，为了避免因为动画还没执行完成而造成动画与之后的语句之间可能产生的错误或者页面冲突，建议以参数的形式添加Callback函数；
- **Chaining**：Chaining允许我们在一条语句中添加多个方法，例如`$('p').css('color', 'red').slideUp(2000).slideDown(2000);`，这是p元素就会先改变css样式，然后收缩，最后张开；为了易读性及格式的美观，可以通过换行及空格来美化；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/EyZZQY/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/EyZZQY/'>jQuery02</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 小测试
利用这节课所学的知识点，重现具有以上功能的div。

#### 小问题
  既然很多方法中已经都有callback函数的可选参数来达到链式运动的目的，那么为什么jQuery还需要有链式运动的功能？

    1. callback函数可以是任意函数，函数改变的对象可以是任意对象；
    2. 链式运动改变的对象是同一元素，链式运动的写法更简单；
    3. 还有类似功能的是动画的队列功能，不过动画改变的是具体的css属性；

---

### jQuery HTML
#### 关键词：获取、设置、添加、删除、css类、css()、尺寸
- 获取:用于获取内容的DOM操作方法主要有三个，获取属性值的方法主要有一个，分别是：
    1. text(): 设置或返回所选元素的文本内容；
    2. html(): 设置或者返回所选元素的内容（包括html标签）；
    3. val(): 设置或返回表单字段的值；
    4. attr(): 用于获取属性值；
- 设置：设置内容也是用上一节提到的三个函数，不过需要在括号中加入需要设置的内容，具体方法可见例子；同时需要知道，这三个jQuery方法都拥有回调函数，函数有两个参数，分别为被选元素列表中当前元素的下标以及原始值，[text()、html() 以及 val() 的回调函数](http://www.w3school.com.cn/jquery/jquery_dom_set.asp)；利用attr()来设置属性时可以同时设置多个属性，属性之间利用逗号隔开，此方法同样具有回调函数；
- 添加：利用jQuery可以很容易的添加新元素或者新内容，方法如下：
    1. append()：在被选元素的结尾插入内容或元素；
    2. prepend()：在被选元素的开头插入内容或元素；
    3. after()：在被选元素之后插入内容或元素；
    4. before()：在被选元素之前插入内容或元素；
- 删除：删除元素或内容主要通过以下两个jQuery方法：
    1. remove()：删除被选元素及其子元素，括号中可添加选择器，用于删除符合选择器条件的元素及其子元素；
    2. empty(): 从被选元素中删除子元素；
- css类：通过jQuery可以很容易对css元素进行操作，主要方法有：
    1. addClass()：向被选元素添加一个或多个类（添加多个类的时候类名称之间用空格隔开）；
    2. removeClass()：从被选元素删除一个或多个类；
    3. toggle()：对被选元素添加/删除类的切换操作；
    4. css()：设置或返回被选元素的一个或多个样式属性，语法为`css('propertyName')`如果有多个满足被选条件，则只返回第一个元素的属性；如需设置CSS属性，则需使用语法为`css('propertyName', 'value')`，此时将所有满足条件的元素的样式都设置成目标样式；
- 尺寸：通过jQuery很容易处理元素和浏览器窗口的尺寸，主要的方法如下：
    1. width()：设置或返回元素的宽度（不包括内边距、边框和外边距），如果对象为document或者window，则表示返回HTML文档或者浏览器窗口的宽度和高度；如果在括号中加入数字，则表示将对应的尺寸设置为对应的值；
    2. height()：设置或返回元素的高度（不包括内边距、边框和外边距）；
    3. innerWidth()：返回元素的宽度（包括内边距）；
    4. innerHeight()：返回元素的高度（包括内边距）；
    5. outerWidth()：返回元素的宽度（包括内边距和边框），如果括号中增加参数‘true’则表示返回包括内外边距及边框的宽度；
    6. outerHeight()：返回元素的高度（包括内边距和边框），如果括号中增加参数‘true’则表示返回包括内外边距及边框的高度；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/OXBzLX/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/OXBzLX/'>jQuery03</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 本小程序具有的功能：
1. 点击第一个按钮，能在方框中添加一个list，list的内容为输入框中的内容，且添加都是从头开始添加；
2. 点击第二个按钮，移除方框中的一个list，且每次移除都是移除第一个；
3. 点击第三个按钮能够改变方框中list的样式，具体为改变字体、字体颜色及list的样式；
4. 点击第四个按钮能够改变方框的尺寸；

#### 小问题
利用append()及after()来添加内容的话，有何不同？
> 前者是在所选元素的结尾处添加内容，也就是说，并没有新增加一个节点；而后者则在所选元素的后面增加内容，很显然这时候增加了一个节点。可以通过一个很小的例子来证明，局部代码如下：

```javascript
<p>This is a paragraph!</p>

<p>This is a paragraph!</p>
hello!                           //利用after()来添加 "Hello!"

<p>
This is a paragraph!
Hello!                          //利用append()来添加 "Hello!"
</p>
```
#### 小测试
通过本节的学习，应该已经知道了利用jQuery来控制html元素的添加与删除以及css样式的设置，那么可以从添加、删除及设置样式的方法中任选几个来制作一个和上面所示类似功能的程序。

---

### jQuery遍历
#### 关键词：遍历、祖先、后代、同胞、过滤
- 遍历：用于根据其相对于其他元素的关系来查找或者选取HTML元素；
- 祖先：祖先元素包括父元素、祖父元素等等，常用的方法为：
    1. parent()：返回被选元素的直接父元素；
    2. parents()：返回被选元素的所有祖先元素，其中甚至包括文档的根元素（即<html>)；
    3. parentsUntil()：返回介于两个给定元素之间的祖先元素；
- 后代：与祖先相对的，后代指的是子、孙、曾孙等，常用的方法为：
    1. children()：返回被选元素的直接子元素；
    2. find()：返回被选元素的被find的元素，包括所有后代；
- 同胞：同胞拥有相同的父元素，常用的方法为：
    1. siblings()：返回所有被选元素的同胞元素；
    2. next()：返回被选元素的下一个同胞元素；
    3. nextAll()：返回被选元素的所有跟随的同胞元素；
    4. nextUntil()：返回介于两个给定参数之间的所有跟随的同胞元素；
    5. prev()：返回被选元素的上一个同胞元素；
    6. prevAll():返回被选元素的所有前面的同胞元素；
    7. prevUntil()：返回介于两个给定参数之间的所有的同胞元素；
- 过滤：缩小搜索元素的范围，常用的方位有以下几种：
    1. first()：返回被选元素的首个子元素；
    2. last()：返回被选元素的最后一个元素；
    3. eq()：返回被选元素中带有指定索引号的元素；
    4. filter()：返回符合匹配标准的元素集合；
    5. not()：返回不匹配标准的所有元素集合；

#### 代码及实例
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/BzqvZJ/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/BzqvZJ/'>jQuery04</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 注意：
> 在使用filter()进行筛选的时候，`$(selector).filter(some)`其中seclector和some是同一等级的，也就是说是在很多selector中找出符合‘some’这个筛选要求的selector。

#### 小测试
本节的内容比较简单，只需要注意方法之间的细微差异就好。通过本节的学习，应该已经能够快速的找出所需要的元素或元素合集了。为了加深印象，可从上面那么多的遍历方法中挑出几个来进行练习。

---

### jQuery AJAX
#### 关键词：AJAX简介、加载、Get/Post
- 简介：全称为Asynchronous JavaScript and XML，异步的JavaScript和XML，此功能能够在不重载整个页面的情况下通过后台加载数据，并在页面上显示出来；
- 加载：在jQuery中的AJAX方式为：load()，此方法能够从服务器中加载数据，并把返回的数据放入到被选元素中；语法为：`$(selector).load(URL, data, callback)`其中URL参数表示希望加载的地址；可选参数data规定了与请求一同发送的查询字符串键/值对集合；可选参数callback是load方法完成后所执行的函数名称，可设置参数为responsTxt（包含调用成功时的结果内容）,statusTxt（包含调用的状态）,xhr（包含XMLHttpRequest对象）；
- Get/Post：两种常见的从服务器请求数据的方法，[点击这个链接可了解这两者的详细区别](http://www.w3school.com.cn/tags/html_ref_httpmethods.asp)；

#### 代码及实例
```javascript
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <style>

    </style>
    <script type="text/javascript" src='https://code.jquery.com/jquery-2.2.4.min.js'></script>
    <script>
        $(document).ready(function () {
            $('#btn').click(function () {
                $.get('a.txt?t='+ new Date().getTime(), function (data, status) {
                    alert('Date:'+data+"\nStatus:"+status);
                });
            });
        });
    </script>
</head>

<body>
    <button type="button" id="btn">Get</button>
</body>
</html>
```

> 注意：由于ajax部分的内容需要在服务器环境下进行测试，所以本节只给出了代码的例子。

#### 小测试
利用jquery我们不再需要自己去手写ajax文件了，确实是非常的方便。通过本节课程的学习，可自己动手在服务器环境下测试一下获取信息。（需要注意的是最好将html文件和待查询文件放在同一个服务器的文件夹中）

---

### jQuery杂项
#### 关键词：命名冲突
- 命名冲突：noConflict()，由于有可能其他框架也使用$符号作为简写，那么如果同时使用这两种框架的话就可能导致脚本停止运行，为了解决这个问题，在jQuery中使用noConflict()方法。语法为`$.noConflict()`这样写完以后，就需要用全名jQuery来代替$符号了。如果希望直接用$符号且不引起冲突，那么可以将$符号作为变量传给ready函数，但是需要注意的是在函数外还是需要用全名。

#### 实例及代码
```javascript
$.noConflict();
jQuery(document).ready(function($){
  $("button").click(function(){
    $("p").text("jQuery 仍在运行！");
  });
});
```

---


## 总结
&nbsp; &nbsp; &nbsp; &nbsp; 接触jquery其实有一段时间了，但是真正开始学习的时间并不长。初步学完JS之后，又接触到bootstrap，然后了解到其中也包含了jquery的内容，所以决定先全面了解jquery然后再来学习bootstrap。
&nbsp; &nbsp; &nbsp; &nbsp; jQuery作为JS的轻量级的库存在，自然而然的在应用层面上比原生JS有着很大的优势，在利用jQuery写效果的时候就能明显的感觉到这一点。在jQuery中各种选择器应有尽有，各种事件也非常多，还有很好用的链式写法，这一切都与jQuery的宗旨“Write less, do more”不谋而合。
&nbsp; &nbsp; &nbsp; &nbsp; 由于时间关系，并没有去了解jQuery的内部写法的精妙，在之后的学习生涯中一定会找出时间来认真了解下。同样的由于时间关系，并没有将每种事件，每个选择器，每个效果都去实现一遍，但私以为在应用层面上效果只不过是外表，其内核都是一样的，所以这并不影响在需要这种效果的时候来调用。
