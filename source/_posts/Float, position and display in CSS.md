---
title: Float, Position and Display in CSS
date: 2016-06-27
updated: 2016-06-28
categories: CSS
tags:
    - CSS
    - 前端
    - 基础

---

##  前言
&nbsp;&nbsp;&nbsp;&nbsp;目前是第二遍学习CSS，第一遍学习的时候只是看了一遍教材，当时感觉还行，但是在之后学习JS的过程中就愈发感觉到没有学好这一章节的严重性，所有在第二遍学习的时候，一定要将这个知识点彻底的弄清楚才会进入到下一阶段，这也就是为什么我会花3天的时间来弄清楚这个知识点的原因了。
&nbsp;&nbsp;&nbsp;&nbsp;为了搞懂这个问题，首先能想到的当然是先多看几遍教材，然后直接Google，搜索到几篇中文博客，之后在StackOverFlow上搜索与Float相关的问题，这一遍下来，搜索的资料让我看了好久，而我所理解的都将在下面的文章中通过图文来表述。

<!-- more -->

##  知识点
1. normal flow:
> Boxes in the normal flow belong to a formatting context, which may be block or inline, but not both simultaneously. Block-level boxes participate in a block formatting context. Inline-level boxes participate in an inline formatting context.
> &nbsp;&nbsp;正常流：在正常流的盒子就属于格式化上下文，而这个格式化上下文可能是块级的也可能是行间的，但这两者不会同时存在。块级别的盒子参与到块级格式化上下文。行间级别的盒子参与到行间格式化上下文。
2. relative positioning:
> Once a box has been laid out according to the normal flow or floated, it may shifted relative to this position. This is called relative positioning.
> &nbsp;&nbsp;相对定位：如果一个盒子按照正常流或者浮动来进行布局，那么它可能会相对这个位置进行移动。这就是所谓的相对定位。
3. floating:
> A float is a box that is shifted to the left or right on the current line. The most interesting characteristic of a float is that content may flow along its side(or be prohibited from doing so by the 'clear' property).
> 浮动：浮动就是一个被转移到所在行的左边或者右边的盒子。它最有意思的一个性质就是内容会沿着它的边缘流动（或者是因为有‘clear’属性而导致不能沿着它的边缘流动）
4. clear:
> This property indicates which sides of an element's box(es) may not be adjacent to an earlier floating box. The 'clear' property does not consider floats inside the element itself or in other block formatting context.
> &nbsp;&nbsp;清除：这个属性是用来规定元素盒子的哪一边不能和浮动盒子相邻。‘清除’属性不会作用在浮动元素的本身也不会作用在其他块级层叠上下文中。
5. absolute positioning:
> In the absolute positioning model, a box is explicitly offset with respect to its containing block. It is removed from the normal flow entirely (it has no impact on later siblings). An absolutely positioned box establishes a new containing block for normal flow children and absolutely (but not fixed) positioned descendants. The containing block for a positioned box is established by the nearest positioned ancestor.
> &nbsp;&nbsp;绝对定位：在绝对定位模型中，盒子相对其被包含块的偏移量会被明确的设定。在正常流中它会被完全剔除（对之后的兄弟元素没有影响）。绝对定位的盒子会为其中的正常流子元素产生一个包含块以及绝对（不是固定）定位的后代元素。被定位元素盒子的包含块是由最近的被定为的祖先元素来产生。
6. block formatting context:
> Floats, absolutely positioned elements, block containers (such as inline-block, table-cells, and table-captions) that are not block boxes, and block boxes with 'overflow' other than 'visible' (except when that value has been propagated to the viewport) establish new block formatting context for their contents.
> &nbsp;&nbsp;块级格式化上下文：浮动，绝对定位元素，非块级盒子以及块级盒子但拥有“overflow”属性不是“visible”（除了当那个值已经被传到视窗的时候）的块级包含者（例如行内块、表格单元以及表格头）会为它们的内容产生一个新的块级格式化上下文。
7. Block-level elements and block boxes:
> Block-level elements are those elements of the source document that are formatting visually as blocks. The following values of the 'display' property make an element Block-level:'block', 'list-item', and 'table'.
> Block-level boxes are boxes that participate in a block formatting context. Each Block-level element generates a principal block-level box that contains descendant boxes and generated content and is also the box involved in any positioning scheme.Except for table boxes, which are described in a later chapter, and replaced elements, a block-level box is also a block container box. A block container box either contains only block-level boxes or establishes an inline formatting context and thus contains only inline-level boxes. Not all block container boxes are block-level boxes: non-replaced inline blocks and non-replaced table cells are block containers but not block-level boxes. Block-level boxes that are also block containers are called block boxes.
> &nbsp;&nbsp;块级元素以及块级盒子：块级元素指的是源文件中按照块级来进行可见的格式化的元素。下面关于“display”属性的值能够让一个元素变成块级元素：block，list-item 以及 table。
> 块级盒子指的是参与块级格式化上下文的盒子。每个块级元素会生成一个自己的块级盒子，这个块级盒子都包含后代盒子和内容，同时也是这个盒子参与到所有的定位中。除了将在下一节中将要讲到的表格盒子以及替代元素，块级盒子也是块包含盒子。块包含盒子中要么只包含块级盒子要么产生一个行内格式化上下文然后只包含行内盒子。并不是所有的块包含盒子都是块级盒子：不可替代的行内快以及不可替代的表格单元都是可以包含块，但并不是块级盒子。块级盒子，同时也是块包含者被称之为块盒子。
8. Relationships between 'display', 'position', and 'float':
> The three properties that affect box generation and layout interact as follows:
> 1. If 'display' has the value 'none', then 'position' and 'float' do not apply. In this case, the element generates no box.
> 2. Otherwise, if 'position' has the value 'absolute' or 'fixed', the box is absolutely positioned, the computed value of 'float' is 'none', and display is set according to the table below. The position of the box will be determined by the 'top', 'right', 'bottom' and 'left' properties and the box's containing block.
> 3. Otherwise, if 'float' has a value other than 'none', the box is floated and 'display' is set according to the table below.
> 4. Otherwise, if the element is the root element, 'display' is set according to the table below, except that it is undefined in CSS 2.1 whether a specified value of 'list-item' becomes a computed value of 'block' or 'list-item'.
> 5. Otherwise, the remaining 'display' property values apply as specified.


## 浮动（Float）
&nbsp;&nbsp;&nbsp;&nbsp;浮动属性可以施加给任何元素（只要此元素不是绝对定位），设定浮动属性的元素从普通流中脱离，形成块级格式化上下文（BFC），而普通流中的元素则表现的此浮动元素不存在一样（除了会使行框变短，从而形成文本绕浮动元素的现象）。浮动属性具有以下几个特点：
1. 只有横向浮动，没有纵向浮动；（属性值只有none、left及right）
2. 浮动元素的上外边框不能超过其包含块的上边框；
3. 浮动元素脱离普通流后其包含容器将得不到此元素的高度属性（然后就有了关于clearfix方法的讨论）；
4. 更多特点见[Float说明。](https://www.w3.org/TR/CSS21/visuren.html#propdef-float)

## 定位（Position）
&nbsp;&nbsp;&nbsp;&nbsp;定位属性比较好理解，其值有 inhert, static, relative, absolute, fixed 这五种。其中static为默认值，表示没有定位，根据位置出现在文档的普通流中；inhert 为继承父元素的position属性；relative 为相对定位，相对的是其本身在普通流中的位置，而且设定为相对浮动后，元素仍然占据原来普通流中的位置；absolute 为绝对定位，定位基准是最靠近的定位属性不为static的祖先元素，当设置为未绝对定位后，元素的位置就与普通流无关了，同时也不占据文档流空间，而且在设置为绝对定位后，元素会形成一个新的块级格式化上下文（BFC），原来是行内元素的会变成块级元素，而块级元素的宽度则由其本身的内容决定，而不再是默认的100%了；fixed可以说是absolute的特殊类，它也是固定定位，但是它的定位基准为视窗（viewport），除此之外，与决定定位没有区别。

## 显示类（Display）
&nbsp;&nbsp;&nbsp;&nbsp;Display属性主要决定元素是块级元素还是行间元素。属性值主要有block、inline-block、inline、list-item和none。块级元素为垂直排列，块级元素会自动换行，可设置块的宽高信息；行间元素为水平排列，宽高由内容决定，外部设置对其无效。

## Float、Position 和 Display 之间的关系：
1. 如果display的值为none，那么后两者就不会产生作用，也不会有任何的盒子产生；
2. 除此之外，如果元素为absolute或者fixed定位，那么浮动的属性值相当于‘none’，display的属性如下面的表格所示。元素的位置就由设定决定定位时的值以及所包含容器来决定；
3. 除此之外，如果float属性的值为不是none，那么元素将会浮动，元素的display属性将如下表所示；
4. 除此之外，如果元素是根元素，那么元素的属性如下表所示；
5. 除此之外，元素的display属性则根据设定来取值。

| specified value               | computed value    |
| :---------------------------- | :---------------- |
| inline-table                  | table             |
| inline, table-x, inline-block | block             |
| others                        | same as specified |

## 清除浮动（Clearfix）
&nbsp;&nbsp;&nbsp;&nbsp;容器内如果只存在浮动元素，那么则会因为浮动元素不在普通流中而造成父级容器高度塌陷且无法获取浮动元素高度的情况，为了解决这个问题，除了了各种各样的清除浮动的方法，下面简单介绍几种：
1. 利用伪类及伪元素来清除，代码如下：
```
.container::after {
    content:"";
    display:block;
    clear:both;
}
```
2. 利用overflow属性，代码如下：
```
.container {
    overflow: hidden; /* 或者是auto */
    display: inline-block; /* Necessary to trigger "hasLayout" in IE */
    display: block; /* Sets element back to block */
}
```
  或者是：
```
.container {
    overflow: hidden; /* Clearfix! */
    zoom: 1;  /* Triggering "hasLayout" in IE */
    display: block; /* Element must be a block to wrap around contents. Unnecessary if only using block-level elements. */
}
```
3. 利用clear属性，代码如下：
```
<br style="clear:both" /> <!-- So dirty! -->
```
&nbsp;&nbsp;&nbsp;&nbsp;这种增加```<br>```同时结合clear属性的方法虽然看起来非常简单，但非常不推荐使用。主要原因有：如果后期有更好的清除方式，你不想有```<br>```元素存在那么将存在很大的问题；而且这种增加也不是语义上的增加。


> #### **由于笔者水平有限，本文有很多需要完善的地方，将长期保持更新；如阅读发现任何问题，欢迎批评指正！**

#### 参考文章(Reference)：
- [Stackoverflow--What methods of ‘clearfix’ can I use?](http://stackoverflow.com/questions/211383/what-methods-of-clearfix-can-i-use/1633170#1633170)
- [Blog--Clearing floats](http://www.quirksmode.org/css/clearing.html#top)
- [Blog--CSS 101: Block Formatting Contexts](http://yuiblog.com/blog/2010/05/19/css-101-block-formatting-contexts/)
- [W3C--Relationships between 'display', 'position', and 'float'](https://www.w3.org/TR/CSS21/visuren.html#dis-pos-flo)
- [Blog--CSS浮动float详解](http://www.jianshu.com/p/07eb19957991#)
- [Blog--CSS布局 ——从display，position， float属性谈起](http://www.cnblogs.com/dolphinX/archive/2012/10/13/2722501.html)
- [Blog--对CSS中的Position、Float属性的一些深入探讨](http://www.cnblogs.com/coffeedeveloper/p/3145790.html)
