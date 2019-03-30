---
title: 【置顶】 《精通JavaScript开发》
date: 2016-07-02
updated: 2016-08-30
categories: 前端
tags:
    - 基础
    - 前端
---

## 前言
&nbsp;&nbsp;&nbsp;&nbsp;从5月25日开始开始学习，用了将近一个月的时间将[视频课程](http://study.163.com/course/courseMain.htm?courseId=224014)过了一遍，对比W3school及另外一套课程，这个课程给我的体验是整体进度设置很合理，Blue老师循循善诱，讲课风格非常适合新手学习。为了更好的掌握JavaScript的内容，下文将对每一章节做对应的总结与复习，并有相应的小测试来巩固复习。本文内容适合所有正在学习此课程的同学。<b>对于本课程或者本博客有任何问题，非常欢迎给我发邮件，我会尽我所能回答你的问题。</b>

<!--more-->

## 课程章节
### 《初探JavaScript魅力01》
#### 关键词：JS、事件、属性、函数、重用、变量
- JavaScript：交互、功能；
- 事件：用户操作或者其他改变；
- 属性：属性是与对象相关的值；
- 函数：函数是指由事件驱动的或者当它被调用时执行的可重复使用的代码块；
- 重用：使开发效率更高，布局更简洁；
- 变量：存储信息的容器；

#### 实例及代码
<iframe height='277' scrolling='no' src='//codepen.io/Leon-Zhao/embed/kXwLYb/?height=277&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/kXwLYb/'>JavaScript-01</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
请利用这节课的知识，完成具有下面功能的区块：
> 1. 区块大小200px*200px；背景颜色为红色；
> 2. 鼠标移入区块大小变成300px*300px，背景颜色变成蓝色；
> 3. 鼠标移出区块大小及颜色变成初始状态。

---

### 《初探JavaScript魅力02》
#### 关键词：变量、函数的定义及调用、ID、if判断、双等号、className
- 函数定义及调用：定义时只是告诉系统有这个函数，但不会执行；调用的时候函数执行；
- ID：任何标签都可以加ID，包括link。任何标签的任何属性都可以改，而且html上怎么写，js里就怎么写（除了className）；
- if：条件判断；
- 双等号：用于判断双等号两边是否相等；
- className： 列别名，为js中的保留字，唯一一个在html及js中写法不同的属性；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/zBzpjv/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/zBzpjv/'>JavaScript-02-01</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/XKgVoX/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/XKgVoX/'>JavaScript-02-02</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>


#### 测试题
请根据本节所学的知识，完成下面一个小程序：
> 1. 新建一个按钮及div；
2. 点击按钮更改div的样式（可以是背景颜色、大小或者其他）；
3. 必须通过更改div的类来达到上面的效果；

---

### 《初探JavaScript魅力03》
#### 关键词：函数传参、操作属性方法、字符串及参数
- 函数传参：当函数中有参数有多个值时使用传参，参数就是占位符；
- 操作属性方法：最常用的为通过“.”，但是当属性作为参数的时候，需要用"[]"的形式来改变参数，否则无法被识别；所有用.的地方都能用[]替换，但反过来不成立；
- 字符串为常量，设定后即为定值；参数则为变量，传入时才确定；传入字符串时需要加双引号，而后者不需要；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/grRZBL/?height=265&theme-id=0&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/grRZBL/'>JavaScript-03</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
请根据本节所学的知识，完成下面一个小程序：
>1. 新建三个按钮及一个有字体内容的div；
2. 分别点击按钮改变div中字体的大小、颜色及样式；
3. 通过函数传参的方式达到上面所要求的效果。

---
### 《初探JavaScript魅力04》
#### 关键词：样式优先级、提取行间事件、匿名函数、window.onload、获取元素组、循环
- 样式优先级：表示样式优先执行的顺序，如右： 通配符<标签<class<ID<行间；（对于同一个元素，修改样式的时候建议在同一优先级进行修改。）
- 提取行间事件：行间事件也是一种特殊的属性；
- 匿名函数：不进行命名的函数；
- 获取元素组：利用getElementsByTagName获取;
- 循环：while（包括初始化、条件、语句和自增）；for 循环。

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/zBzJAV/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/zBzJAV/'>JavaScript-04</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
请根据本节所学的知识，完成下面的一个小程序：
> 1. 新建两个按钮及若干个div，大小及背景颜色随意；
2. 点击按钮分别能改变所有div的大小或者颜色。

---
### 《初探JavaScript魅力05》
#### 关键词：This、innerHTML、字符串连接、数组
- This：当前发生事件的元素（目前这么理解就行了，更多的用法后面会涉及到）；
- innerHTML：写入到html页面中，写入的内容本身可以包含html标签；
- 字符串连接：通过了解符 ` + ` 来实现，注意有优先级的问题；
- 数组：一系列值的组合；

#### 实例及代码
<iframe height='559' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/ZOydkq/?height=559&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/ZOydkq/'>JavaScript-05</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
请根据本节所学的知识，完成下面一个小程序：
> 1. 制作一个选项卡；
2. 有四个选项，且每一项都对应不同的内容；
3. 鼠标移动到不同选项卡的时候，显示不同的内容；
4. 鼠标移入选项卡的时候，选项卡本身的样式也会发生一些变化。

---
### 《JavaScript基础01》
#### 关键词：JS组成、变量类型、parseInt、NaN、作用域、闭包、命名规范
- JS组成：JS由ECMAScript（解释器、翻译）、DOM（操纵html）、BOM（操作浏览器，兼容性）；ECMA几乎没有兼容问题，DOM有一些操作不兼容，BOM没有兼容问题（完全不兼容）；
- 变量类型：数字、字符、对象、函数、布尔值、未定义；（一个变量最好只存一种类型的变量）；
- parseInt：将字符转换成数字，从左到右扫描字符，一旦遇到不是数字的就直接返回，因此也可提取字符串中的数字；字符串不为数字，则返回NAN；只用于转换整数，如要转换成小数，则为parseFloat；
- NaN：唯一一个不等于本身，isNaN用于判断是否为NaN；
- 类型转换：显示类型转换（如上面提到的）及隐式类型转换（系统自动转换），然后就涉及到`==`和`===`后者不进行隐式类型转换就开始比较；`+`运算时不会进行隐形类型转换而`-`符号则会先进行类型转换再运算；
- 作用域：变量作用范围，局部变量及全局变量；
- 闭包：子函数可使用父函数的局部变量；
- 命名规范：可读性及规范性（匈牙利命名法）；

#### 实例及代码
<iframe height='124' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/bZAbVk/?height=124&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/bZAbVk/'>JavaScript-06</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
请根据本节所学的知识，完成下面一个小程序：
> 1. 制作一个加法计算器；
2. 计算器形式为`a + b = c`，其中a和b为输入框中的数字，c为输出的数字；
3. 计算前先判断是否为数字类型，如果不是则弹出提示；
4. 能计算整数及小数；

---

### 《JavaScript基础02》
#### 关键词：运算符、程序流程控制、True和False、Json、Json和数组
- 运算符：用于算数、赋值、关系、逻辑、优先级等；
- 程序流程控制：判断（if、switch、？：），循环（while、for），跳出（continue、break）
- True和False： 表示的是计算机用于计算的真与假，true包括：true、非零数字、非空字符串、非空对象；false包括：false、0、空字符串、空对象、undefined；
- Json：一种轻量级的数据交换格式，是基于JavaScript的一个子集；（注意Json没有length属性，使用循环的话需要for（var i in json）这种形式）；
- Json与数组的区别：1.Json的下标为字符串，而数组为数字；2.前者无length属性而后者有；3.前者循环只能用for（var i in json）的形式，而后者两种形式都可以；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/NAvGjb/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/NAvGjb/'>JavaScript-07</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
由于本节内容多为介绍性，基本上每个程序都非常简单，可用练习下列小程序：
>1. 制作一个隔行变色的表格；
2. 利用switch制作一个小程序；
3. 利用三运算符`?:`制作一个小程序；
4. 利用break或者continue制作一个小程序；
5. 利用Json制作一个小程序。

---

### 《深入JavaScript》
#### 关键词：函数返回值、函数传参（不定参）、取非行间样式、数组、splice、concat、join、sort
- 函数返回值：即为函数的执行结果；
- 传不定参：arguments，参数的个数可变；（例子：求和、css函数）
- 取非行间样式：如果样式没有写在行间，那么应该利用currentStyle(IE)或者getComputedStyle(obj，false).name。利用if，else来进行兼容性处理；获取复合样式的属性时需要注明所取的明确样式（如获取背景颜色，需要写backgroundColor，直接写background是没有作用的）。
- 数组：使用单一变量的值存储一系列的值；数组的length属性既可读亦可写，因此可利用可写功能快速清空数组；添加：push及unshift（分别表示在尾部及头部添加）；删除：pop及shift（分别表示从尾部及头部删除）；
- splice：splice(n1,n2)表示从数组的n1位置开始删n2个元素；splice(n1,n2,"a","b","c"...)表示在n1位置删除n2个元素，并添加后面的"a","b","c",等等；
- concat：数组的连接，语法:`a.concat(b)`,则数组a和b连接，a是元素在b的元素前面；
- join：表示用给定的参数连接数组里面的值，语法为`arr.join("value")`,那么arr中的值就将会被value连接起来；
- sort：数组的排序，语法为`arr.sort()`,其中sort()括号中可传入函数，表示排序的依据；在对数字排序的时候，因为sort属性只认字符串，所以必须传入比较函数；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/EyvXLd/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/EyvXLd/'>JavaScript-08</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
同样的，本节也主要是在讲一些非常基础的知识，没有涉及到复杂程序的练习，所以大家可选择性练习下方小程序：
> 1. 利用不定参argument制作一个程序，如果传入的是两个参数则获取参数值；如传入三个值，则设置参数；
2. 练习数组的相关属性：pop、unshift、push、shift、concat、join、sort、splice、length；

#### 小问题
> 有没有什么方法能够直接修改css样式中的参数值？（由本节讲到的可直接获取样式中的参数值想到的）

---

### 《定时器的使用01》
#### 关键词：定时器、清除定时器、Date对象、charAt()
- 定时器：间隔性(setInterval)、延时性(setTimeout);
- 清除定时器：clearInterval(name),name为需要关闭的定时器的名称；对应的还有clearTimeout;
- Date(): 包括`getHours(),getMinutes(),getSeconds(),getFullYear(),getMonth(),getDate(),getDay()`，其中getMonth()获取的月份是从0开始的；
- charAt: 兼容低版本的获取元素的方法，比如获取str中第i位元素：`str[i]=str.charAt(i)`;

#### 实例及代码
<iframe height='355' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/akyxYo/?height=355&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/akyxYo/'>JavaScript09</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
本节讲到了两个例子，一个就是上面的数码时钟，另一个就是下面的延时提示框，需要满足的功能如下：
> 1. 有一大一小两个div，左右分布；
2. 当鼠标放入小div区域时，大的div显示；
3. 当鼠标移出小div到别处，大div经过500ms后消失；
4. 如果在这500ms内，鼠标移入大div区域，则大div不消失；
5. 从大div移出时，500ms后大div消失；
6. 在500ms内如果鼠标移入小div，则大div不消失；
  （简单来说：当鼠标在可见的div范围内，div常显；当鼠标在空白处500ms后，大div消失）

---

### 《定时器的使用02》
#### 关键词：offsetLeft、无缝滚动、innerHTML
- offsetLeft：元素的水平偏移位置（包括margin）；
- 无缝滚动：结合offsetLeft及定时器的综合应用；应该包括的功能：左右都能滚动、鼠标移入暂停，移出重新滚动；
- innerHTML: 可以用innerHTML+=innerHTML来使得某元素内的内容为两份的之前的内容；
- 在编写本节课程的时候一定不要不要忘记了加上`px`.

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/NAvkQj/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/NAvkQj/'>JavaScript10</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据所学的知识，拓展本节课的实例功能：
> 1. 增加滚动速度选项：可分为快、一般、慢，三种滚动速度。

---

### 《DOM基础》
#### 关键词：DOM节点、childNodes、文本节点及元素节点、nodeType、children、parentNode、offsetParent、firstChild、lastChild、setAttribute、className
- 节点：和css中的标签、js中的元素是一个意思；
- childNodes：子节点集合，包括文本节点及元素节点（在IE8下不包括空白的文本节点）
- 文本节点及元素节点：前者不包括在标签中，后者包含在标签中；
- nodeType：节点类型；nodeType为3时为文本节点，nodeType为1时为元素节点；
- children：子节点集合，不包括文本节点，只包含元素节点；
- parentNode：元素父节点；
- offsetParent：表示用于定位的父级；
- firstChild： 第一个子节点（包括文本子节点）。firstElementChild则不包括文本子节点，只包括元素子节点，但是低版本IE不兼容，因此要用if语气来兼容；
- setAttribute：用DOM方式操纵元素，语法为`setAttribute(name, value)`，与此类似的还有getAttribute，语法为`getAttribute(name)`，以及removeAttribute，语法为`removeAttribute(name)`；
- className：类别名，结合判断能批量修改特定类别的元素，也可以将if函数及类别封装成固定的函数，方便调用；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/EywNVV/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/EywNVV/'>JavaScript11</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据本节所学的知识，完成下面一个小程序：
>1. 将有特定class属性的div的第一个子节点的所有内容的字体改为times；
2. 提示：需要使用firstChild及className的使用，注意兼容性；

---

### 《DOM操作应用》
#### 关键词：createElement、appendChild、insertBefore、removeChild、文档碎片
- creatElement： 创建元素，语法`createElement(element)`，创建完成后还需要添加到父节点才有效；
- appendChild：将创建的元素添加到父节点，语法：`obj.appendChild(element)`，其中obj为父节点，element为创建出来的元素；如果appendChild的元素为现有的元素，那么使用这个属性的时候会先从现有的父级上删除，然后添加到新的父级里；
- 注意：不管是html中原有的，还是通过DOM创建出来的，性质都是一样的，没有区别；
- insertBefore：在父节点内插入子节点，语法：`obj.insertBefore(element, obj[i])`表示在父节点obj中的第i个元素前面插入元素；但是如果obj中本来没有元素，那么就没法obj[i]就不存在，这时候还得用appendChild，所以这两个经常结合使用，解决兼容性问题；
- removeChild：移除子节点，语法`obj.removeChild(element)`，其中obj为父节点，element为需要移除的元素；
- 文档碎片：文档碎片可以提高DOM操作性能（理论上），语法：`createDocumentFragment()`；（实际上在高级浏览器上，文档碎片几乎不会提高效率）

#### 实例及代码
<iframe height='219' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/zBEPKE/?height=219&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/zBEPKE/'>JavaScript12</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据本节所学的内容，完成下面一个小程序：
> 1. 制作一个表格。两个按钮：一个增加表格行数，一个删除表格行数；
2. 每次增加的行数都在第一行，删除则从最后一行开始；
3. 顺便加上各行变色的小功能；

---

### 《DOM操作应用高级-01》
#### 关键词：tBodies、隔行变色、移入高亮、搜索、toLowerCase()、search()、
- tBodies:选出tbody元素，相当于`getElementsByTagName('tbody')`，同样的还有tHead、tFoot、rows及cells；
- 搜索：需要的功能有——忽略大小写、模糊搜索、多关键词搜索；
- toLowerCase:转化成小写；
- search：搜索文本，如果搜索到则返回所在位置，未找到则返回-1；
- split：切分字符串，语法为`str.split('aa')`，表示用aa来切分str，aa可以为空格或者任何字符；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/jAGxaz/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/jAGxaz/'>JavaScript13</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 本程序具有的功能：
1. 表格隔行变色；
2. 鼠标移入移除高亮；
3. 手动输入添加内容，并同时保证功能1和2有效，而且自动标号不重复；
4. 具有删除所添加行的功能，同时保证1和2的功能有效；
5. 只能搜索，可忽略大小写及模糊搜索；

#### 测试题
根据本节所学内容，完善上面的小程序：
> 1. 加入多关键词搜索功能（结合split功能及search）；
2. 搜索功能与上述功能1，2兼容；（目前我还没想到更好的办法去解决）

---

### 《DOM操作应用高级-02》
#### 关键词：排序、aLi、表单、onsubmit、onreset、表单验证
- 排序：中心思想是结合利用appendChild的移动功能及sort的排序功能；
- aLi：aLi=document.getElementById('li'),虽然看起来像是数组，但却又不是正真的数组，它不具备sort、join等功能，确切来说这只是一个元素集合；
- 表单：用于向服务器提交数据，action为链接地址；
- onsubmit：提交数据是发生的事件；
- onreset：重置表单时发生的事件；
- 表单验证：阻止用户输入非法字符等；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/YWABXk/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/YWABXk/'>JavaScript14</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

>本小程序就有的功能：
>  1. 所有上节课程序所具有的功能；
2. 在上节课的基础上具有排序功能；
3. 与课程相比，本排序功能具有选择性，即可根据所需要的排序依据进行排序；

#### 测试题
表单内容比较简单，可利用表单完成下面一个小程序：
> 1. 制作一个表单，包括用户名、密码和提交；
2. 提交时会弹出一个确认页面；
3. 具有重置内容；

---

### 《JS运动基础-01》
#### 关键词：运动框架、分享侧边栏、图片淡入淡出
- 运动：利用定时器及offsetLeft来实现；
- 框架完善过程：
  1. 到指定地点停止；
  2. 点击后，运动前先清除定时器，保证每次只有一个定时器处于工作状态；
- 分享侧边栏：鼠标移入移出，运动方向相反；
- 图片淡入淡出：鼠标移入移出改变图片的透明度；

#### 实例及代码
<iframe height='353' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/XKZwyK/?height=353&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/XKZwyK/'>JavaScript15</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

**注意：变量申明的位置非常重要，变量申明的位置能够直接影响到变量的值是否收到函数的影响**

#### 测试题
根据本节所学的运动框架的学习，完成下面的小程序：
> 1. 新建一个分享侧边栏，侧边栏上有个小标签；
2. 将整个div布局在视窗的左下角；
3. 正常情况下侧边栏只有标签能看到，鼠标移入时，整个div出现，移出div后0.5s后侧边栏又隐藏到视窗外；

---

### 《JS运动基础-02》
#### 关键词：缓冲运动、Math、右侧悬浮框
- 缓冲运动：运动速度与到目标位置相关；
- Math：数学函数，常用的有Math.ceil()，表示向上取整；Math.floor()，表示向下取整；由于目标值可能大于也可能小于现在的值，所以需要根据速度来判断是向上还是向下取整，这时候就可以利用三元运算符简单的判断一下了，具体的操作可以在下面的实例中看到；Math.abs()，表示的是取绝对值，在匀速运动的停止条件的时候能用到；
- 匀速运动时，由于速度可能不能被运动量整除，那么为了正好达到目标，可以定义在距离目标近到一定程度（绝对值小于速度值）的时候，直接让程序到达目标点；在缓冲运动中由于运动在最后，速度值可能会是小数，而浏览器默认会将小数部分舍去，所以达不到目标，为了达到目标，只要直接对速度进行取整（整数时向上取整，负数时向下取整），保证在速度为小数时也能继续运动；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/zBPaLv/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/zBPaLv/'>JavaScript16</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 本程序具有的功能：
1. 这个小程序就综合了匀速运动与缓冲运动，水平方向上为匀速运动，竖直方向为缓冲运动；
2. 注意：特别需要小心的是在写尺寸的时候别忘了加上“px”，否则代码无效而且不会报错！

#### 测试题
根据本节缩写的内容，完成制作一个缓冲样式的滚动条，具体如下：
> 1. 缓冲条位于视窗的右侧中间位置；
2. 不管是向上滚动还是向下滚动，缓冲后滚动条都会停止在视窗右侧中间；
3. 停止运动时不能抖动（用到parseInt属性）；

---

### 《JS运动应用-01》
#### 关键词：多物体同时运动、offsetWidth、任意值运动框架
- 多物体运动框架：将定时器变成元素的属性，那么调用时则不会相互干扰；（例子：改变div的长度，互不影响；或者改变透明度；）
- 补充：在多物体运动的情况下，所有的属性都不能共用，例如上面提到的透明度，需要先把透明度赋值给一个变量，那么就需要将这个变量变成所有需要调用的对象的属性；
- offsetWidth：本节讨论到了与offset相关的属性，**提到这是包含padding及border的属性**，那么在有border的情况下，前面的例子就会有一定的变化；为了避免因为border及padding带来的影响，建议使用本身的属性来带入程序（因为一般样式属性写在样式表中，那么就会用到之前学到的currentStyle活getComputeStyle属性了）；
- 任意值运动框架：一套运动框架能控制几乎所有的属性变化，其包含三个属性：作用对象、作用属性、变化值；

#### 代码及实例
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/mEqNoE/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/mEqNoE/'>JavaScript17</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据本节所学的知识，制作如下一个小程序：
> 1. 自己重写一个完美运动框架；
2. 利用这个框架来改变不同的样式，但是别包括上面已经写过的长度、宽度或者透明度；
3. 给对象加上border属性后检查效果是否仍然相符。

---

### 《JS运动应用-02》
#### 关键词：仿flash运动
- 仿flash运动：这个小程序结合了近几节课所学的知识点，非常值得联系，具体的实现过程如下：
  1. 左右按钮移入移出显示隐藏；（包括在左右键上）；
  2. 点击小图能起到切换大图的功能（更改大图的Zindex--写在行间为Zindex，写在样式表中为Z-index，缓冲运动改高度）；切换之前需要判断切换到的是否为当前，如果为当前则不发生变化；
  3. 点击时，小图除切换功能外还会变成不透明；所有的小图移入移出透明度都有变化，但是当前图片移出时不变化；
  4. 增加左右按钮点击时大图切换的功能；（第一张图及最后一张图的时候则开始自循环）
  5. 点击左右按钮时除了大图要切换，小图也需要滚动，而且也要注意第一张及最后一张的特殊情况；
  6. 增加自动播放的功能，也加入鼠标移入移出时的消除启动播放；

#### 实例及代码
<iframe height='769' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/grorbK/?height=769&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/grorbK/'>JavaScript18</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 注：
1. 本程序实现的过程中没有利用课程中所讲到的利用Z-index属性的叠加，而是利用了之前课程中学到的轮播，效果算是各有特色；
2. 实现的过程中发现布局对JS的影响非常大，第一次跟着课程实现效果的时候因为CSS还学习的很糟糕，所以就知识重写了JS部分，这次再重写的时候，写到CSS才发现为什么用到Z-index，以及不用也行的道理；
3. 实践出真知。

#### 测试题
根据这节课所学到的知识点，完成下面的小程序：
> 1. 利用Z-index或者我上面使用的轮播的形式重写一次这个程序，巩固学习效果；
2. 所重写的程序应该具有上面提到的所有功能；

---

### 《JS运动中级》
#### 关键词：链式运动（土豆提示栏）、完美运动框架（新浪微博）
- 链式运动：完成一个运动之后，开始另一个运动。原理即为在原来的运动框架中加入一个函数参数，即在动作完成的部分加入一条新的语句；
- 完美运动：结合json及运动框架，构建一个完美运动框架，能同时改变多个属性值；（注意：在同时改变多个属性值的时候，需要所有值都达到目标值后才能关闭定时器）；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/groGqv/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/groGqv/'>JavaScript19</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

>注：
1. 本例为完美运动框架的简单运用，这个运动框架能满足多个元素属性值的同时改变直到所有的属性值都达到目标值才停止；

#### 测试题
根据这节课所学到的完美运动框架，写出下面一个小程序：
> 1. 形式如新浪微博的新消息发布；
2. 点击发布后，公告栏则会生成输入的信息；
3. 信息显示按时间排布，最新的消息显示在最上端；
4. 新生成消息的过程加上完美运动框架，达到高度缓慢撑开，透明度逐渐增加的效果；

---

### 《JS事件基础》
#### 关键词：event对象、document、事件流（事件冒泡）、鼠标事件、keyCode、其他属性
- event对象：事件对象，应用在IE6-8及高版本的chrome浏览器，在低版本的chrome浏览器及Firefox中需要用到一个参数：ev，在调用函数时，系统就将这个参数传给函数；为了解决这个兼容问题，可以用一个“或”的表达式，例如：`var oEvent=event||ev;`，然后调用的时候，直接用oEvent就好了；
- document：包含整个页面的内容，上至<!DOCTYPE html>，下至</html>;如果需要给整个页面加点击事件，应该加在document上而不是body上，因为body的范围由它所包含的内容决定；
- 事件流：最简单的一个事件流的例子——事件冒泡（一般会带来一些困扰，所以很多时候需要取消冒泡：通过事件对象来解决——`oEvent.cancelBubble=true;`，典型的例子为仿select下拉框）；
- 鼠标事件：鼠标坐标，clientX及clientY(表示的是可视区的坐标，所有如果有滚动的时候需要加上scrollTop和scrollLeft)；
- keyCode：表示键盘上按键的键码，按键事件为onkeydown及onkeyup；（按键卡顿现象：照顾特殊人群，但是会造成不好的影响，解决方案为将事件加上setInterval函数来将延迟给掩饰掉，按键抬起时清除定时器）；
- 其他属性：ctrlKey，shiftKey、altKey，使用的时候都需要结合事件对象，例如：`oEvent.ctrlKey`；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/EyQxLk/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/EyQxLk/'>JavaScript20</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

> 注：
1. 在输入框中输入任意字符；
2. 鼠标点击enter或者直接用键盘enter；
3. 移动鼠标就能按到效果，输入的字符越多，效果越明显；
4. 如果未输入任何字符，那么将会提示输入；

#### 测试题
根据本节所学的鼠标及键盘事件，写出下面一个小程序：
> 1. 能通过鼠标及键盘控制一个div的运动；
2. 需要将scroll因素考虑在移动的范围内；
3. 需要避免连续按住不放时产生的卡顿现象（利用定时器）；

---

### 《JS事件中级》
#### 关键词：默认行为、拖拽
- 默认行为：浏览器自带的一些行为，有些时候需要阻止系统自带的默认行为，加上自己设置的行为；（比如右键菜单-oncontextmenu）
    1. 阻止右键菜单：需要阻止时，直接oncontexmenu函数返回为false即可；自己设置一个菜单，并且在鼠标右键的时候改变display属性，将定制菜单的位置改为鼠标的位置，然后在页面空白处点击的时候（给document加上onclick事件）将定制菜单栏收回；
    2. 设置一个只能输入数字的输入框：默认时，在输入框按下按键则会在输入框显示相应字符或者操作。这也是一种默认行为，当onkeydown事件返回为false的时候，则能阻止这种默认行为。结合keyCode和阻止这种默认事件的功能，则可以设计一个能输入数字及特定按钮（如方向键及退格键）功能的小程序；
- 拖拽：保证鼠标的位置及被拖动元素的相对位置不变，需要注意的点如下：
    1. 应该是只有杂鼠标按下之后才能移动，鼠标抬起时移动停止；
    2. 对于鼠标快速移动时可能移出元素范围带来的移动异常，将移动事件加在document上即可解决；
    3. 当移动出视窗时释放鼠标按键，仍然能够移动，为了解决这个问题，需要将鼠标释放按钮事件也加在document上；
    4. 在Firefox中拖拽空元素的时候会出现重影，这也是FF中的一种默认事件，可以用返回false的方法来组织这个bug；
    5. 被拖拽元素被拖出视窗范围，这时候就可以判断来阻止元素被拖出视窗；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/zBRKYz/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/zBRKYz/'>JavaScript21</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据本节所学的内容，制作一个小程序：
> 1. 在整个页面组织右键菜单的默认属性；
2. 自己定制一个菜单栏，里面可以包括一些链接之类的；
3. 页面空白处单击则菜单栏消失；

---

### 《JS事件高级应用-01》
#### 关键词：事件绑定、高级拖拽
- 事件绑定：attachEvent(name, function)，可以将多个函数加到同一个事件上，在chrome及FF上不兼容，为了兼容需要用到addEventListener（name，function，false）（此属性也不兼容IE9以下的IE浏览器）。所以为了都兼容，应该使用一个判断函数整合这个属性的不同写法，但是要注意addEventListerner属性中的事件是没有“on”的（具体写法可见实例）；
- 高级拖拽：新增功能———— 1.不拖出父级div或者其他指定对象的区域；2.边缘吸附；3.利用事件捕获来解决在低版本IE下拖拽时会选中文字的问题，setCapture（只兼容IE，功能是将页面的所有事件都集中在加了事件捕获的对象上），与之相应的为releaseCapture，即解除对象的捕获；

#### 代码及实例
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/qNoPxz/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/qNoPxz/'>JavaScript22</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

这个小程序所具有的功能：
> 1. 事件绑定，点击内部的div后会弹出两次会话框；
2. 可以在指定外框自由移动；
3. 不会产生移动时文字的选中；
4. 兼容低版本的IE浏览器；

#### 测试题
根据本节所学的内容，重写事件绑定及完美拖拽的小程序，特别注意以下两点：
>1. 兼容性问题；
2. 代码重用性；

---

### 《JS事件高级应用-02》
#### 关键词：带框拖拽、自定义滚动条
- 带框拖拽：预先设置一个样式，按下鼠标产生一个div并赋予样式，div的大小与框相同，位置与框相同，移动时只移动框，松开鼠标时才移动框，并且将产生的div移出；
- 自定义滚动条：控制对象的大小、透明度、文字滚动等；

#### 代码及实例
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/wWmQjx/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/wWmQjx/'>JavaScript23</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

这个小程序具有的功能：
> 1. 利用滚动条能控制div的大小；
2. div具有带框移动的功能；

#### 测试题
根据本节所学的知识，制作一个自定义的滚动条：
> 1. 自定义滚动条样式；
2. 能实现通过滚动来控制文字上下翻转的功能；

---

### 《Ajax基础》
#### 关键词：服务器、字符集编码、缓存、eval、Ajax原理
- 服务器：有两种含义：一个管理资源并为用户提供服务的计算机软件，通常分为文件服务器（能使用户在其它计算机访问文件），数据库服务器和应用程序服务器；运行以上软件的计算机，或称为网络主机（Host）。（我自己用的服务器程序为XAMPP）
- 字符集编码：把字符集中的字符编码为指定集合中某一对象（例如：比特模式、自然数序列、8位组或者电脉冲），以便文本在计算机中存储和通过通信网络的传递；
- 缓存：存储在本地电脑中的资料，通过url来识别是否为同一网站，所以为了避免缓存带来不好的影响，可以通过加上一个时间戳的方式来解决这个问题；
- eval：将语句解析成js能够识别的内容；
- Ajax原理：
    1. http请求分为两种方式： get方式及post方式；前者提交的数据直接加在网址上，而后者通过http content传递；前者长度有限制（容量小，不适合传输数据），后者可传输容量较大的数据；前者安全性较差，后者安全性较好；前者有缓存，后者无缓存；因此前者适合获取数据，后者适合上传数据；

#### 代码及实例
由于本节需要用到本地服务器，因此这里就不上传实例了。

#### 测试题
根据本节所学的内容，完成小程序：
> 1. 搭建本地服务器（我自己用的是XAMPP);
2. 结合已有的ajax文件（如果自己不会写，可参照下节内容中的源代码），新建一个html及txt文本来创建一个实时更新显示内容的页面（通过按钮）；

---

### 《Ajax中级》
#### 关键词：编写Ajax对象、接收状态值、onreadystatechange、responseText
- 编写Ajax对象：
    1. 创建Ajax对象；
    2. 连接到服务器；
    3. 发送请求；
    4. 接收返回值；
- 注意：在JS中利用没有定义的变量时会弹出错误，而利用没有定义的属性时则会提示undifined；
- 接收状态值（readyState）：
    1. 0 （未初始化）还没有调用open（）方法；
    2. 1 （载入）已调用send（）方法，正在发送请求；
    3. 2 （载入完成）send（）方法完成，已收到全部相应内容；
    4. 3 （解析）正在解析相应内容；
    5. 4 （完成）相应内容解析完成，可以在客户端调用了；
- http状态码（status）：最常见的为200，表示读取成功；
- onreadystatechange: 表示返回状态；
- responseText: 读取的文件内容；

#### 实例及代码
由于本节也需要在本地服务器运行，所以只能讲代码贴出来，ajax代码如下：
```javascript
function Ajax(url, fnsucc, fnfail){
    // 1. Set a new ajax object:
    if(window.XMLHttpRequest){
        var oAjax=new XMLHttpRequest();
    }
    else {
        var oAjax=new ActivaXObject('Microsoft.XMLHTTP')
    }

    // 2. Get connected:
    oAjax.open('GET', url, true);

    // 3. Send the request:
    oAjax.send();

    // 4. Get data back:
    oAjax.onreadystatechange=function (){
        if(oAjax.readyState==4){
            if(oAjax.status==200){
                fnsucc(oAjax.responseText);
            }
            else {
                if(fnfail){
                    fnfail(oAjax.status);
                }
            }
        }
    }
}
```

#### 测试题
由于本节所学的内容比较单一，所以根据本节所学的内容自己手写一个完整的Ajax程序。

---

### 《JS面向对象基础-01》
#### 关键词：面向对象、对象组成、this、object对象、构造函数、工厂方式、
- 面向对象：对象是一个整体，对外提供一些操作；面向对象指的是使用对象时只关注对象提供的功能，而不关注其内部细节；（这是一种通用思想，而非只在编程中适用）
- JS中面向对象：简称OOP，具有以下三个特点：
    1. 抽象：抓住主要问题；
    2. 封装：不考虑内部实现，只考虑功能使用；
    3. 继承：从已有对象上，继承出新的对象，可以最大限度重用现有代码，包括多重继承（继承多个对象的功能）和多态；
- 对象组成：包括方法和属性
    1. 方法：和函数类似，函数是自由的，但方法具有归属的对象，这两者都是过程量，是动态的；
    2. 属性：和变量类似，变量时自由的，但属性具有归属的对象，这两者都是状态量，是静态的；
- this：当前的方法属于谁就指向谁；
- 注意：不能在系统对象中随意附加方法、属性，否则会覆盖已有方法、属性；
- object对象：空白对象；
- 构造函数：用于构造一个对象的函数，功能与普通函数一样；
- 工厂方式：创建空白对象，加工对象，返回对象；缺点：创建时没有'new'，函数重复导致资源浪费；

#### 实例及代码
<iframe height='304' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/WxJQmL/?height=304&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/WxJQmL/'>JavaScript26</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
用工厂方式重写一个面向对象的程序。

---

### 《JS面向对象基础-02》
#### 关键词：new、原型(prototype)、类和对象、对象命名规范
- new：通过new+构造函数来构造对象，可以理解为“new”会先通过系统在函数内部创建`var this=new Object()`这个对象，然后在最后的时候又自动返回`return this`这个对象，这样理解之后，面向对象的方式和工厂方式原理上也是一样的；
- 原型(prototype)：可以理解为css中的class， 能够同时给多个对象加方法；
- 类和对象：前者不具备实际功能，而后者具有，它们之间的关系就相当于模子和产品的关系；为了同时给多个对象加方法，那么就需要在类上面加原型，既可以给系统对象加也可以在创建的对象加；
- 注意：用构造函数加属性，用原型加方法。区别于工厂方式，这种方式叫做混合的构造函数/原型方式，简称混合方式构造对象；
- 对象命名规范：为了和系统对象保持一致，自己构造出来的对象命名时最好也保持首字母大写；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/OXkrVB/?height=265&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/OXkrVB/'>JavaScript27</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
用混合方式重写一个面向对象的小程序。

---

### 《JS面向对象实例》
#### 关键词：将面向过程的函数改写成面向对象的形式
- 改写：
    1. 不能有函数嵌套，但可以有全局变量；
    2. 将onload改写成构造函数，将全局变量改写成属性，将函数改写成方法；
    3. debug，主要容易出现在this、事件、闭包及传参上；

#### 代码及实例
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/jAxqQa/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/jAxqQa/'>JavaScript28</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
按照这节课所学的内容，利用面向对象的方式重写选项卡或者之前写过的任何一个程序。

---

### 《JS面向对象高级》
#### 关键词：Json方式、命名空间、继承、call、引用、系统对象
- Json方式面对对象：用Json的方式来实现对象虽然比较简单，但是如果对象超过一个，那么又回到了之前写对象的方法。这种方式也有人叫做单体方式。
- 命名空间：在不同的Json中写具有相同名字的函数，可以让具有相同名字的函数同时工作；
- 继承：能够继承父级的属性和方法；
- call：通过call的方式调用属性时，如果call传入的参数，则参数会替换掉函数中的this；
- 引用：通过`=`号使数组、方法或者其他相等的时候，系统会将等号两边指向同一内存位置，所以不管是针对谁做出改变，最终的结果是两者都会发生改变。比如：有两个数组A和B，其中A中有1，2，3，三个变量，又有A=B，这时候如果在B中push一个变量4，那么数组A中也会存在这个变量。为了解决这个问题，可以利用循环将A中的变量一个个都push到数组B中；
- 总结：属性的继承利用call，方法的继承利用循环；
- 系统对象：本地对象（非静态对象，如Object/Function/Array/String等），内置对象（静态对象，如Global/Math）,宿主对象（由浏览器提供，如BOM/DOM）；

#### 实例及代码
<iframe height='265' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/WxJpzZ/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/WxJpzZ/'>JavaScript29</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
利用继承的特点，用面向对象的方式重写拖拽的小程序。

---

### 《BOM应用》
#### 关键词：BOM基础
- BOM基础：
    1. window.open(a, b) 打开新的页面，b表示是打开的新窗口是显示在本页还是新的页面；
    2. window.close() FF中不能用这个去关闭非脚本打开的窗口；
    3. document.write() 先清空，然后写入；
    4. window.navigator.userAgent 表示的是浏览器的类型及版本；
    5. window.location 表示当前页面的地址；
    6. document.documentElement.clientWidth及document.documentElement.clientHeight：表示可视区的宽度及高度；
    7. document.documentElement.scrollTop(IE)及document.body.scrollTop（chrome）：表示滚动条高度；
    8. window.onscroll及window.onresize分别表示在页面滚动及更改窗口尺寸时发生的事件；
    9. alert/confirm/prompt: 系统对话框；

#### 代码及实例
<iframe height='250' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/dXZRXY/?height=250&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/dXZRXY/'>JavaScript30</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
由于本节课所学的大部分为基础知识，应用都较简单，所以可重写上例中的小程序，巩固知识点。

---

### 《COOKIES基础与应用》
#### 关键词：cookie、setDate()、读取cookie、删除cookie
- cookie：
    1. 页面用来保存信息；
    2. 同一个网站共享一套cookie；
    3. 数量、大小有限（一般数量小于50，大小不超过4k或10k）；
    4. 有过期时间；（expires）
    5. 使用方式`document.cookie='name=value'`;
- setDate(): 相对于getDate()获取系统时间，setDate()能够设置对象的时间；
- 读取cookie：需要利用字符串分割，具体见例子；
- 删除cookie：设置需要删除的cookie的有效期为'-1'即可；

#### 实例及代码
<iframe height='224' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/WxJOBL/?height=224&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/WxJOBL/'>JavaScript31</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
在FireFox浏览器的环境下尝试使用cookie的相关功能，具体写法可参考上面的实例。

---

### 《JS中的正则表达式》
#### 关键词：正则基础、正在表达式、写法、match、replace、元字符、转义字符、量词、test
- 正则基础：了解正则表达式需要从字符串操作开始，最常见的字符串操作如下
    1. name.search(a): 表示的是在name中查找a，并返回a的位置；如果不存在则返回-1；
    2. name.substring(value1, value2): 表示在name中截取从第value1到value2（不包括结束位置）的字符；如果只给一个参数，则返回至最后一位；
    3. name.charAt(value): 表示获取字符串的某一位；
    4. name.split(s):利用s来切分name，其中s可以是字符串或者符号；
- 正则表达式：舶来语，表示的是一套规则，这套规则是计算机可识别的；
- 写法：JS风格（新建对象，然后使用对象），Perl风格（正则最早是出现在perl语言中）；
- match: 提取所有复合条件的元素；`i`表示忽略大小写，`g`表示全局搜索；
- replace：替换复合要求的元素，用法为：`name.replace(a, b)`表示将name中的a替换成b（如果有多个，则只替换第一个，除非用正则匹配全局），常用于敏感词过滤；
- 元字符：用`[]`表示，`[abc]`表示a、b、c中的任意一个，`[a-z]`表示从所有字母，数字同理。`[^a]`表示出了a；
- 转义字符：
    1. \d  表示数字                    \D  表示除了数字
    2. \w  表示英文、数字和下划线       \W  表示除了英文、数字和下划线
    3. \s  空白字符                    \S  表示除了空白字符
    4. .   表示任意字符，很容易出错，不建议使用；
- 量词：表示个数，用{}
    1. {n}      表示正好出现n次；
    2. {n, m}   最少n次，最多m次；
    3. {n, }    最少n次，最多无限；
    4. +       相当于{1，}，即最少出现1次；
    5. ?       相当于{0，1}，即可有可无；
    6. *       相当于{0，}，表示可有可无，而且出现多少次都无所谓，很容易出错，不建议使用；
- test：`reg.test(name)`，用于检测name是否符合reg所表示的正则，如果符合则返回true；需要注意的是，只要name一部分符合reg的要求就会返回true，这时候就需要用到`^`及`$`，分别表示行首和行尾；

#### 实例及代码
<iframe height='335' scrolling='no' src='//codepen.io/Leon-Zhao/embed/preview/WxJrPO/?height=335&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Leon-Zhao/pen/WxJrPO/'>JavaScript32</a> by Leon (<a href='http://codepen.io/Leon-Zhao'>@Leon-Zhao</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

#### 测试题
根据本节所学的正则表达式，制作一个这样的小程序：
> 1. 能够识别输入的数字是否为电话号码；
2. 如果不是电话号码则弹出“输入的不是电话号码”；
3. 如果符合要求则弹出“输入成功”。

---

## 总结
&nbsp;&nbsp;&nbsp;&nbsp;从开始学习这门课程到今天正好两个月。当时虽然也已经花了将近一个月的时间去学习JS，但还是感觉很茫然，直到开始学习这门课程。最初是看视频跟着老师的讲解一步一步的写程序，学习完一遍以后，自知很多知识点掌握的还不是很牢固，然后果断作出了复习一遍，重写所有程序的决定。复习的时候，先是重新看一遍老师的讲解，巩固基础知识，然后将当节课的知识点尽量综合起来放在一个程序里面重写出来，这个过程就是举一反三的过程。举几个例子：
> 1. 第五节课制作日历，第一遍写的时候没有写任何布局相关的内容，重写时所有的css、js和html都是独立完成；
2. 第九节课制作超酷时钟，同样关系到布局问题，而且首次结合图床来写程序；
3. 第十三节课DOM高级应用，将这节课中所学的所有功能都集中在了一起，并且增加了按要求排序这个课程中并没有讲到的功能，而且没有bug；
4. 第十八节课仿flash运动，这个小程序是目前写过的功能最多的程序了，而且实现过程并非照搬老师的讲解，实现的效果也基本一致；
5. ……

&nbsp;&nbsp;&nbsp;&nbsp;在复习的过程中，对知识点的理解和掌握程度远远超过第一次学习。这个过程中积攒了些许经验，希望能和大家分享：
>1. 写程序之前先理清逻辑关系，否则debug的时候很难发现问题；
2. 动手写比脑子想更重要，看似很简单很套路的知识点，如果自己不去套路一遍，这个套路就不属于你；
3. 有足够的耐心。debug是个很烦人却又很让人兴奋的过程，程序成功运行的瞬间，所有debug的烦恼都消失了；
4. 善用搜索引擎。前端发展了这么多年，我们所踩得坑前人都已经踩烂了，只要有疑问，直接搜关键词基本上都能搜出相关的博客或者问题；
5. 不要好高骛远。基础知识永远不会过时。

&nbsp;&nbsp;&nbsp;&nbsp;毋庸置疑，本课程非常适合新手学习，但同时也不难发现课程中很少触及真正基础的知识，而且后面还有一部分内容并没有讲到。下一步，我将通过书本继续巩固基础知识，同时开始学习JS框架，准备开始做几个简单的项目。这些内容都会在之后的博客中更新。
&nbsp;&nbsp;&nbsp;&nbsp;最后，作为一个初学者，我深知在学习过程中的种种疑惑和迷茫，即使在现在，这份心情依然存在。然而，只要不放弃努力，就始终在进步，目标终将会越来越近。
 <h4>&nbsp;&nbsp;&nbsp;&nbsp;<em> The world is a fine place and worth fighting for !</em></h4>
