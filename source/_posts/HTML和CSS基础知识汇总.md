---
title: HTML和css基础知识汇总（长期更新）
date: 2016-06-30
updated: 2016-07-01
categories: 前端
tags:
    - CSS
    - HTML
    - 前端
    - 基础

---

## HTML部分

### 简介：
- HTML 指的是超文本标记语言 (Hyper Text Markup Language)；
- HTML 不是一种编程语言，而是一种标记语言 (markup language)；
- 标记语言是一套标记标签 (markup tag)；
- HTML使用标记标签来描述网页；

<!--- more --->


### 知识点：
- HTML：Hyper Text Markup Language；
- 标签：h1-h6; p; a; img; hr; strong; big; small; em; i; sub; sup; pre; code; kbd; tt; samp; var; address; abbr; acronym; bdo; blockquote; q; del; ins; map; area; table; tr; td; th; caption; thead; tbody; tfoot; dl; dt; dd; span; form; input; select ; option; textarea; fieldset; legend; optgroup; frameset(不与body同用); iframe; frameborder; object; embed; audio; video;
- 属性：align; bgcolor; dir；text-decoration; target; name; alt; background; align; rowspan; colspan; cellpadding; cellspacing; frame; raido; checkbox; action; method; selected; rows; cols; label; noresize;



> HTML5部分网站上讲的太笼统了，之后在做项目的过程中再做具体的了解，其中canves这个属性被广泛应用；这两天把html和css复习一遍之后开始复习js，同时开始看书+做项目+写博客。按照这种速度的话,下个月底之前应该能够取得很大的进步。

## CSS 部分

### 简介：
- CSS 指层叠样式表 (Cascading Style Sheets);
- 样式定义如何显示 HTML 元素;
- 样式通常存储在样式表中;
- 把样式添加到HTML4.0中，是为了解决内容与表现分离的问题;
- 外部样式表可以极大提高工作效率;
- 外部样式表通常存储在 CSS 文件中;
- 多个样式定义可层叠为一。

### 知识点：
- **派生选择器**：也被称为上下文选择器（contextual selector），根据元素在其位置的上下文关系来定义样式，是的标记更简洁；
- **id选择器**：用“#”来定义 （注意：id属性只能在每个HTML文档中出现一次）
- **类选择器**：以一个“.”显示；
- **属性选择器**：以“[属性]”的方式显示；（还有属性和值选择器）-- 对于属性值有多重不同的选择方式，具体可参照w3school上的说明；
- **背景**：背景色；背景图像（不能继承）；背景重复（background-repeat）；背景定位（background-position--主要是针对当背景是图像的时候使用，如果只出现一个位置信息，则另一个默认为center）；背景关联（background-attachment，可将背景图像固定在可视区域）；
- **文本**：缩进文本（text-indent：一般来说，可以为所有块级元素应用text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用 text-indent 属性。不过，如果一个块级元素（比如段落）的首行中有一个图像，它会随该行的其余文本移动。如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果。它的值可为**负数或者百分比**。此属性可继承。）；水平对齐（text-align：justify可实现两端对齐——谨慎使用，因为各浏览器增加空间的方式不同造成效果各异；文字间隔（word-spacing）；字母间隔（letter-spacing）；字符转换（text-transform：uppercase、lowercase、capitalize）；文本装饰（text-decoration：underline、overline、line-through及blink；）；空白字符（white-space：pre、nowrap、pre-wrap及pre-line）；文本方向（direction：ltr、ltr；）
- **字体**：五种通用字体（font-family）——Serif、Sans-serif、Monospace、Cursive和Fantasy；字体风格（font-style：normal、italic和oblique）；字体变形（font-variant：小型大写字母）；字体加粗（font-weight：bold、bolder、lighter等）；字体大小（font-size：px、em和百分比，其中第一个是静态测量单位，后两者则是相对测量单位）；
- **链接**：链接的四种状态（link、visited、hover和active，设置时需要注意顺序问题。通过改变连接访问前后及鼠标是否悬停在链接上的属性设置的不同来达到改变样式的目的）；
- **列表**：列表类型（list-style-type）、列表项图像（list-style-image）、列表标志位置（list-style-position）（注意，这些属性一般都是作用在ul或者ol上的，但根据网站上的例子可以知道有时——比如list-style-image也可以施加到list上。）
- **表格**：表格边框（border），折叠边框（border-collapse：将表格边框折叠为单一边框），表格文本对齐（水平方向：text-align；垂直对齐方式：vertical-align），表格内边距（padding），表格颜色（background-color）；
- **轮廓**：（outline，区别于border，轮廓指的是边缘外框的外围，可以起到突出元素的作用。）
- **框模型**：![image](http://www.w3school.com.cn/i/ct_boxmodel.gif)元素框的最内部分是实际的内容，直接包围内容的是内边距。内边距呈现了元素的背景。内边距的边缘是边框。边框以外是外边距，外边距默认是透明的，因此不会遮挡其后的任何元素。背景应用于由内容和内边距、边框组成的区域。内边距、边框和外边距都是可选的，默认值是零。但是，许多元素将由用户代理样式表设置外边距和内边距。在 CSS 中，width 和 height 指的是内容区域的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。
- **内边距（padding）**：属性定义元素边框与元素内容之间的空白区域。CSSpadding属性定义元素的内边距。padding属性接受长度值或百分比值，**但不允许使用负值**。单位可以有 [EM, PX, PT, CM](https://www.w3.org/Style/Examples/007/units.en.html#units)。如果使用百分比设置的内边距，那么这个百分比的基数是**其父元素的width来计算的**，这一点也同样适用在外边距（而且不管是左右边距还是上下边距）。
- **边框（border）**：围绕元素内容和内边距的一条或多条线，允许规定元素边框的样式、宽度和颜色；CSS 规范指出，边框绘制在“元素的背景之上”。这很重要，因为有些边框是“间断的”（例如，点线边框或虚线框），元素的背景应当出现在边框的可见部分之间。CSS2 指出背景只延伸到内边距，而不是边框。后来 CSS2.1 进行了更正：元素的背景是内容、内边距和边框区的背景。边框的样式（border-style：一共有十种，效果各不相同，而且可以分别为不同的边框设置不同的样式）；边框宽度（border-width：可以指定长度或者使用thin，medium或者thick中的任意一个，但是后面这三个关键词的具体宽度可能会根据不同的用户代理有不同的值）。因此，如果希望边框出现，就必须声明一个边框样式。然后设置边框的宽度才有意义。边框的颜色（border-color）：默认的边框颜色是元素本身的前景色。如果没有为边框声明颜色，它将与元素的文本颜色相同。另一方面，如果元素没有任何文本，假设它是一个表格，其中只包含图像，那么该表的边框颜色就是其父元素的文本颜色（因为 color 可以继承）。这个父元素很可能是body、div 或另一个 table。透明边框（transparent）：CSS2引入了边框颜色值transparent。这个值用于创建有宽度的不可见边框。
- **外边距（margin）**：围绕在元素边框的空白区域是外边距。设置外边距会在元素外创建额外的“空白”。这个属性接受任何长度单位、百分数值甚至负值。margin的默认值是 0，所以如果没有为margin声明一个值，就不会出现外边距。但是，在实际中，浏览器对许多元素已经提供了预定的样式，外边距也不例外。块级元素的垂直相邻外边距会合并，而行内元素实际上不占上下外边距。行内元素的的左右外边距不会合并。同样地，浮动元素的外边距也不会合并。允许指定负的外边距值，不过使用时要小心。
- **外边距合并**：当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。除此之外，父元素与子元素之间，空块元素，也会发生合并，[具体可参考MDN上的内容](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)。**（这个点可以写一篇博客了。）**
- **定位和浮动**：1. 一切都为框-块框、行内框或者无名块框；2. css中有三种基本的定位机制——普通流、浮动和绝对定位，默认都为普通流中定位；3. 位置属性（position）：包括static、relative、absolute和fixed。具体情况可以参考[w3school上面关于position的内容](http://www.w3schools.com/css/css_positioning.asp)。**这个相关内容也可以写一篇剪短的博客了，:-D。**
- **浮动（float）**：浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。**浮动及浮动清除理解起来也有难度啊，搞清楚后也可以写博客了**。
  (关于浮动的博客已写，但是还是没有弄的太明白，之后再买书看吧）
- **元素选择器**：最常见的为元素选择器，在w3c中元素选择器也叫作类型选择器（type selector），类型选择器匹配文档语言元素类型的名称，可以匹配文档树中该元素类型的每一个实例。类型选择其也可适用在XML文档中。
- **选择器分组**：可以把具有同样样式的元素放在样式的左边，**并且用逗号隔开**，选择器的数量没有限制，可以有任意多组；如：h1，p，span { corlor：white；}；
- **通配符选择器**：css2中引入了一种新的简单选择器，叫做通配符选择器（universal selector），符号为*，可以与任何元素匹配；
- **声明分组**：对于同一个元素的不同样式，可以将样式声明在此元素后面，**并用分号隔开**，例如：h1 {corlor：black；background：yellow；font-size：strong；}；
- **类选择器**：要应用样式而不考虑具体设计的元素，最常用的方法就是使用类选择器，它允许以一种独立于文档元素的方式来指定样式；使用语法为：.className {porperty: value; };类选择器可结合元素选择器，选择出某一种元素中具有某个类名的个体，然后赋予其属性和值，例如：p.important {corlor：red；}；多类选择器指的是一个元素可以有多个类，类与类之间用空格分隔，例如：<p class="important warning">其中类名无顺序之分，通过把两个类选择器链接在一起，可以选择出同时包含这些类名的元素；
- **ID选择器**：ID选择器允许一种独立于文档元素的方式来指定样式，例如：#intro {font-size：14px；}指的是ID为intro的元素的字体大小为14px；与类选择器不同的是，ID选择器：1.只能在文档中出现一次；2. 不能结合使用；3. ID能包含更多含义；**需要注意的是：选择器是区分大小写的，因此写的时候务必要注意！**
- **属性选择器**：属性选择器可以根据元素的属性及属性值来选择元素。属性选择器是在css2中引入的。如：[title] {color:red} （表示：把含有标题的所有元素变成红色）；再如：a[href] {color:red} (表示对有href属性的锚应用属性)；还可以结合起来使用，如：a[href][title] {color:red} (表示将同时具有href和title属性的锚的文本设置成红色）；除此之外，还可以规定具体的属性值，例如：```a[href="http://www.w3school.com.cn/about_us.asp"] {color: red;}```（表示只有带有超链接且了解为上述的时候才会变红），而且每个属性选择器都可以对相应的属性赋值；而且需要注意，此时选择器中的属性值和必须完全匹配（注意：如果需要选择不完全匹配，则可以用约等号来选择，如：p[class~="important"] {color: red;}）；字串匹配属性选择器，在css2完成之后发布，可以匹配属性值以某些字符串开头、结尾或者只是包含的情况，具体见[字串属性选择器](http://www.w3school.com.cn/css/css_selector_attribute.asp); 特殊属性选择器，如```*[lang|="en"] {color: red;}```，表示只选择lang属性等于en或者以en-开头的所有元素；（这种用法常见于匹配语言值）。
- **后代选择器（descendant selector）**，又称为包含选择器；比如```h1 em {color:red;}```，需要注意的是，后代选择器中两个元素之间的层级间隔可以是无限的（区别于后面要讲到的子元素选择器）；
- **子元素选择器（Child selector）**：只能选择作为某元素子元素的元素。比如下面的例子：```h1 > strong {color:red;}```，子结合符为“>”，结合符两边的空格是可选的；
- 相邻兄弟选择器（Adjacent sibling selector）：可选择紧接在一个元素后面的元素，且两者有相同的父元素；写法如下：```h1 + p {margin-top:50px;}```，表示的是“选择紧接在h1元素后面的段落增加边距，并且这两者有相同的父元素”；相邻兄弟选择器作用的对象是“+”号后面的元素，对前一个元素没有影响；
- **伪类（Pseudo-classes）**：用于向某些选择器添加特殊的效果；比如超链接中的a:link, a:visited, a:hover, a:active,(注意超链接使用伪类的时候有顺序问题）；:focus 伪类用于引起注意，一般用于[输入框](http://www.w3school.com.cn/tiy/t.asp?f=csse_link_focus)；除此之外，还有:first-child, :lang等伪类；其中:first-child伪类表示用来选择某元素的第一个子元素；
- **伪元素（Pseudo-elements）**：用于向某些选择器设置特殊效果；语法为：```selector:pseudo-element{property:value;}```，主要有```:first-line, :first-letter```, 在css2中引入了：```:before, :after ```，表示的是在某元素前面（后面）插入新内容（这一点在清除浮动那一章节有重点应用）；
- **css水平对齐**：1. 使用margin属性（将左边距和右边距都设置为auto，则左右均等分配可用外边距，达到居中的效果。注意：如果宽度为100%，对齐则没有效果）；2. 利用Position属性（当使用绝对定位属性来定位时，元素将从正常流中删除，从而可能产生交叠元素）；3. 使用float属性进行左右对齐；**注意：使用所有属性进行对齐时都应该声明```!DOCTYPE html```，否则在IE8及以下版本会在右侧增加17px的外边距（为滚动条预留空间）。**
- **css尺寸（Dimension）**：尺寸属性允许控制元素的高度和宽度。同样，也允许增加行间距。除了width，height之外，还有max-height，min-height，max-width，min-height，line-height等；且这些尺寸都可以用像素、百分比来设置；
- **css分类（Classification）**：css分类属性允许规定如何以及在何处显示元素；有inline，block等，其实就是display属性的值，然后这个值就和css的布局有很大的关联，同样影响布局的还有float以及position，它们之间的关系见我之前写的一篇博客[Float, Position and Display in CSS](http://detachment.club/2016/06/27/Float,%20position%20and%20display%20in%20CSS/);本节还讲到了一个很有意思的属性：cursor，用来实现不同 的光标，使用语法为```element {cursor:value; }```；
- **导航栏**：实现导航栏的关键在于对浮动的理解，其他属性都比较简单，实现过程可见：[导航条的实现](http://www.w3school.com.cn/css/css_navbar.asp)；
- **图片库**：其实也不是什么图片库，就是把相同的布局，运用在了几张尺寸一样的图片上罢了。在设定任何css属性之前，都需要认真弄清楚需求，一步一步的将布局分解到每一个```div```中，然后思考每个```div```中的布局，最终形成整体布局。
- **图像透明**：属性为```opacity; filter:alpha(opacity=value)```，如果需要用```:hover```属性来设置鼠标移入之后的效果，那么一定要声明```<!DOCTYPE html>```，否则不能应用在除了a以外的其他元素；
- **css2媒介类型**：媒介类型允许定义以何种媒介来提交文档，文档被显示在显示器、纸媒介或者听觉浏览器上等等；语法为```@media class```，类别中有screen、print、tv、handheld等等（然后就出现了Bootstrap的自适应？）










> ## 注：
> #### 本文内容主要来源为[w3school](http://www.w3school.com.cn/index.html)，相关知识点都在在此网站找到更详细的说明，本博客仅供复习总结用。
