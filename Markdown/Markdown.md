**声明**：本文参考<https://www.appinn.com/markdown/>，非原创，删除原文部分不常用功能，精简文字，为自己参考笔记，修改原文章部分错别字，如果有错漏，欢迎联系我，请多多指教！

<!-- TOC -->

- [概述](#概述)
  - [宗旨](#宗旨)
  - [兼容HTML](#兼容html)
  - [特殊字符自动转换](#特殊字符自动转换)
  - [区块元素](#区块元素)
    - [段落和换行](#段落和换行)
    - [标题](#标题)
  - [这是 H2](#这是-h2)
          - [这是 H6](#这是-h6)
  - [这是 H2](#这是-h2-1)
    - [这是 H3](#这是-h3)
    - [区块引用Blockquotes](#区块引用blockquotes)
    - [列表](#列表)
    - [代码区块](#代码区块)
    - [分隔线](#分隔线)
  - [区段元素](#区段元素)
    - [行内式链接](#行内式链接)
    - [参考式链接](#参考式链接)
  - [强调](#强调)
  - [代码](#代码)
  - [图片](#图片)
    - [行内式](#行内式)
    - [参考式](#参考式)
  - [其他](#其他)
    - [自动链接](#自动链接)
    - [反斜杠](#反斜杠)


<!-- /TOC -->

# 概述

## 宗旨

Markdown的目标是实现**易读易写**

* 可读性：以纯文本发布，不会像是由很多标签或是格式指令所构成
* 易编辑：语法由一些精挑细选的符号组成，其作用一目了然

## 兼容HTML

Markdown的语法目标是：成为一种适用**网络**的书写语言

* HTML是一种发布格式，Markdown是一种书写格式
* Markdown语法种类很少，只对应HTML标记的一小部分
* Markdown的格式语法只涵盖纯文本可以涵盖的范围
* 不在Markdown涵盖范围之内的标签，可以直接在文档里面用HTML撰写
* 在HTML区块标签间的Markdown语法将不会被处理。HTML区块便签必须在前后加上空行与其他内容区隔开，并且在开始与结束标签不能用制表符或空格来缩进
* 在HTML的区段（行内标签）间Markdown 语法是有效的，依照个人习惯，可以直接采用HTML标签来格式化，而不用Markdown提供的链接或者图像便签语法

## 特殊字符自动转换

* 在HTML文件中，有两个字符需要特殊处理：<code>&lt;</code> 和<code>&amp;</code> 。<code>&lt;</code>符号用于起始便签，<code>&amp;</code>符号用于标记HTML实体，如果想要显示原型，要写成<code>&amp;lt;</code>和<code>&amp;amp;</code>

在HTML文件链接标签在href属性里，如果你要链接到:
<pre>
<code>http://images.google.com/images?num=30&q=larry+bird</code>
</pre>
你必须把网址转换成
<pre>
<code>http://images.google.com/images?num=30&amp;amp=larry+bird</code>
</pre>

* Markdown会自动将<code>&lt;</code> 和<code>&amp;</code>转化为<code>&amp;lt;</code>和<code>&amp;amp;</code>；如果要在文档中插入一个版权符号<code>&copy;</code>，可以写成<code>&amp;copy;</code>
* 在code范围内，不论是行内和区块，<code>&lt;</code>和<code>&amp;</code>两个符号都一定会被转化成HTML实体，这项特性让你可以很容易地用Markdown写HTML code

## 区块元素

### 段落和换行

* 一个Markdown段落是由一个或多个连续的文本行组成，前后默认各有一个空行,如果想要需要自定义插入空行，在插入初先按两个以上的空格然后回车

### 标题

Markdown支持两种标题的语法，类Setext和类atx形式

* 类Setext利用<code> = </code>(最高阶标题)和<code> - </code>(第二阶阶标题)，任何数量的<code> = </code>和<code> - </code>都可以有效果，例如：

<pre>
<code>This is an H1
=============</code>
<code>This is an H2
-------------</code>
</pre>

* 类 Atx 形式则是在行首插入 1 到 6 个<code> # </code>，对应到标题 1 到 6 阶，例如：

<pre><code># 这是 H1

## 这是 H2

###### 这是 H6
</code></pre>
可以选择性地「闭合」类 atx 样式的标题
<pre><code># 这是 H1 #

## 这是 H2 ##

### 这是 H3 ######
</code></pre>

### 区块引用Blockquotes

* 在 Markdown 文件中建立一个区块引用,在每行的最前面加上<code> &gt; </code>：

<pre><code>&gt; This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
&gt; consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
&gt; Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
&gt;
&gt; Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
&gt; id sem consectetuer libero luctus adipiscing.
</code></pre>

* Markdown 也允许你偷懒只在整个段落的第一行最前面加上<code> &gt; </code>：

<pre><code>&gt; This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

&gt; Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.
</code></pre>

* 区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的<code> &gt; </code> ：

<pre><code>&gt; This is the first level of quoting.
&gt;
&gt; &gt; This is nested blockquote.
&gt;
&gt; Back to the first level.
</code></pre>

* 引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

<pre><code>&gt; ## 这是一个标题。
&gt;
&gt; 1.   这是第一行列表项。
&gt; 2.   这是第二行列表项。
&gt;
&gt; 给出一些例子代码：
&gt;
&gt;     return shell_exec("echo $input | $markdown_script");
</code></pre>

### 列表

Markdown支持有序列表和无序列表

* 有序列表（使用*、+、-作为列表标记）

<pre><code>* Red
* Green
* Blue
</code></pre>

<pre><code>+ Red
+ Green
+ Blue
</code></pre>

<pre><code>- Red
- Green
- Blue
</code></pre>

* 无序列表（使用数字接着一个英文句点）

<pre><code>1.  Bird
2.  McHale
3.  Parish
</code></pre>
上面列表使用的数字并不会影响输出的HTML结果，上面的列表所产生的HTML标记为：
<pre><code>&lt;ol&gt;
&lt;li&gt;Bird&lt;/li&gt;
&lt;li&gt;McHale&lt;/li&gt;
&lt;li&gt;Parish&lt;/li&gt;
&lt;/ol&gt;
</code></pre>

**注意：**

* 有序列表数字不会影响输出结果，但建议最好按照数字顺序来，不仅是可读性和美观，更因为Markdown未来可能支持有序列表的start属性。
* 列表项目标记通常是放在最左边，最多可以缩进3个空格，项目标记后面则一定要接着至少一个空格或制表符
* 要让列表看起来更漂亮，最好把内容用固定的缩进整理好，如果你懒，那也行
* 如果列表项目间用空行分开，在输出HTML时Markdown就会自动将项目内容用<code>&lt;p&gt;</code>标签包起来
* 列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符，每行都缩进会美观好多，如果你懒惰，也允许不缩进，但是段落第一行必须缩进
* 如果要在列表项目内放进引用，那<code> &gt; </code>就需要缩进：
<pre><code>*   A list item with a blockquote:

    &gt; This is a blockquote
    &gt; inside a list item.
</code></pre>
* 如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符：
<pre><code>*   一列表项包含一个列表区块：

        &lt;代码写在这&gt;
</code></pre>

* 当然，项目列表很可能会不小心产生，像是下面这样的写法：

<pre><code>1986. What a great season.
</code></pre>
* 换句话说，也就是在行首出现数字-句点-空白，要避免这样的状况，你可以在句点前面加上反斜杠。

<pre><code>1986\. What a great season.
</code></pre>

### 代码区块

在 Markdown 中建立代码区块，只要缩进 4 个空格或是 1 个制表符
<pre><code>这是一个普通段落：

    这是一个代码区块。
</code></pre>
Markdown 会转换成：
<p>Markdown 会转换成：</p>

<pre><code>&lt;p&gt;这是一个普通段落：&lt;/p&gt;

&lt;pre&gt;&lt;code&gt;这是一个代码区块。
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）

使用 Markdown 插入范例用的 HTML 原始码
<pre><code>    &lt;div class="footer"&gt;
        &amp;copy; 2004 Foo Corporation
    &lt;/div&gt;
</code></pre>
会被转换为：
<pre><code>&lt;pre&gt;&lt;code&gt;&amp;lt;div class="footer"&amp;gt;
    &amp;amp;copy; 2004 Foo Corporation
&amp;lt;/div&amp;gt;
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
代码区块中，一般的 Markdown 语法不会被转换，像是星号便只是星号，这表示你可以很容易地以 Markdown 语法撰写 Markdown 语法相关的文件。
### 分隔线
用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：
<pre><code>* * *

***

*****

- - -

---------------------------------------
</code></pre>
## 区段元素
### 行内式链接
要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：
<pre><code>This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.
</code></pre>
会产生：
<pre><code>&lt;p&gt;This is &lt;a href="http://example.com/" title="Title"&gt;
an example&lt;/a&gt; inline link.&lt;/p&gt;

&lt;p&gt;&lt;a href="http://example.net/"&gt;This link&lt;/a&gt; has no
title attribute.&lt;/p&gt;
</code></pre>
### 参考式链接
在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：（可以选择性地在两个方括号中间加上一个空格）
<pre><code>This is [an example] [id] reference-style link.
</code></pre>
接着，在文件的任意处，你可以把这个标记的链接内容定义出来：
<pre><code>[id]: http://example.com/  "Optional Title Here"
</code></pre>
链接内容定义的形式为：
* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
* 接着一个冒号
* 接着一个以上的空格或制表符
* 接着链接的网址
* 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着

下面这三种链接的定义都是相同：
<pre><code>[foo]: http://example.com/  "Optional Title Here"
[foo]: http://example.com/  'Optional Title Here'
[foo]: http://example.com/  (Optional Title Here)
</code></pre>
参考式链接比较好读，可以让文件更像是浏览器最后产生的结果，让你可以把一些标记相关的元数据移到段落文字之外，你就可以增加链接而不让文章的阅读感觉被打断。
## 强调
Markdown使用星号（*）和底线（_）作为标记强调字词的符号

* 被 <code>*</code> 或 <code>_</code> 包围的字词会被转成用 <code>&lt;em&gt;</code> 标签包围
* 用两个 <code>*</code> 或 <code>_</code> 包起来的话，则会被转成 <code>&lt;strong&gt;</code>
<pre><code>*single asterisks*

_single underscores_

**double asterisks**

__double underscores__
</code></pre>

会转成：

<pre><code>&lt;em&gt;single asterisks&lt;/em&gt;

&lt;em&gt;single underscores&lt;/em&gt;

&lt;strong&gt;double asterisks&lt;/strong&gt;

&lt;strong&gt;double underscores&lt;/strong&gt;
</code></pre>
**如果你的 <code>*</code> 和 <code>_</code> 两边都有空白的话，它们就只会被当成普通的符号**
如果要在文字前后直接插入普通的星号或底线，你可以用反斜线：
<pre><code>\*this text is surrounded by literal asterisks\*
</code></pre>
## 代码
如果要标记一小段行内代码，你可以用反引号把它包起来（<code>`</code>），例如：
<pre><code>Use the `printf()` function.
</code></pre>
会产生：
<pre><code>&lt;p&gt;Use the &lt;code&gt;printf()&lt;/code&gt; function.&lt;/p&gt;
</code></pre>
如果要在代码区段内插入反引号，你可以用多个反引号来开启和结束代码区段

代码区段的起始和结束端都可以放入一个空白，起始端后面一个，结束端前面一个，这样你就可以在区段的一开始就插入反引号

## 图片

###行内式

<pre><code>![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
</code></pre>
详细叙述如下：
* 一个惊叹号 !
* 接着一个方括号，里面放上图片的替代文字
* 接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。

###参考式
<pre><code>![Alt text][id]
</code></pre>
「id」是图片参考的名称，图片参考的定义方式则和链接参考一样
<pre><code>[id]: url/to/image  "Optional title attribute"
</code></pre>

## 其他

### 自动链接

用方括号包起来， Markdown 就会自动把它转成链接
<pre><code>&lt;http://example.com/&gt;
</code></pre>
Markdown 会转成：
<pre><code>&lt;a href="http://example.com/"&gt;http://example.com/&lt;/a&gt;
</code></pre>

### 反斜杠
Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：

<pre><code>\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
</code></pre>