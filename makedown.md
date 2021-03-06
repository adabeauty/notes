Makedown是一种轻量级的标记语言, 它的目标就是实现: 易读易写, 成为一种适合于网络书写的语言.

Markdown的语法全由一些符号所组成, 并受到一些 text-to-HTML 格式的影响，包括 Setext、atx、Textile、reStructuredText、Grutatext 和 EtText，而最大灵感来源其实是纯文本电子邮件的格式。

Makedown是兼容HTML的, 它没有想要超过HTML, 它只涵盖了HTML的一小部分. 所以不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown, 只要直接加标签就可以了.

1. 请注意，在 HTML 区块标签间的 Markdown 格式语法将不会被处理。比如，你在 HTML 区块内使用 Markdown 样式的`*强调*`会没有效果。
2. 和处在 HTML 区块标签间不同，Markdown 语法在 HTML 区段标签间是有效的。

### 特殊字符自动转换

1. 在 HTML 文件中，有两个字符需要特殊处理： < 和 & 。 < 符号用于起始标签，& 符号则用于标记 HTML 实体，如果你只是想要显示这些字符的原型，你必须要使用实体的形式，像是 &lt; 和 &amp;。

   例如:如果你要打`AT&T` ，你必须要写成`AT&amp;T`。  
   而网址中的 & 字符也要转换。比如你要链接到：  
   `http://images.google.com/images?num=30&q=larry+bird`  
   你必须要把网址转换写为：  
   `http://images.google.com/images?num=30&amp;q=larry+bird`
2. Markdown 让你可以自然地书写字符，需要转换的由它来处理好了。如果你使用的 & 字符是 HTML 字符实体的一部分，它会保留原状，否则它会被转换成 &amp;。

   例如: 书写AT&T, Markdown 就会将它自动转为：AT&amp;T

### 常用语法:
#### 区块元素  
##### 标题

  支持两种格式: Setext 和 Atx. 对于Setext, 在文本下一行划入不限数量个====和-----分别来生成最高级标题(h1)和第二级标题(h2). 而对于Atx, 则使用1~6个#在文本之前来生成1~6级标题(h1~h6).  

  `这是标题h1`  
  `================`  
  `这是标题h2`  
  `------------------`  
  `###这是标题h3`  
  `######这是标题h6`

##### 段落，换行，加粗，斜体

  段落：常规输入生成p标签；  
  换行：行尾空两格或tab缩进生成br标签；  
  斜体：单个 * 或 _ 开头，衔接文本，对应的 * 或 _ 结尾；  
  加粗：一对 * 或 _ 开头，衔接文本，对应的一对 * 或 _ 结尾；  

  `注意：如果你的 * 和 _ 两边都有空白的话，它们就只会被当成普通的符号；也可通过"\"转义，让*和\作为普通字符.`  

  `这是普通文本。`  这是普通文本。  
  `**这是粗体** `  <strong>这是粗体</strong>  
  `*这是斜体*`   <em>这是斜体</em>

##### 引用

`> 这是一个引用块；`  
`也可以这样写,断行可以不用添加">"符号；`  
`>>这是子引用。 `  

> 这是一个引用块；
也可以这样写,断行可以不用添加">"符号；  
>>这是子引用。

##### 代码块

    缩进4个空格或一个tab制表符就能生成代码块，MD会用\<pre\>和\<code\>标签来把代码区块包起来。只要某一行未缩进，文本就变成普通的文本行。  

  `这是一个标准的代码块，由pre包裹code组合而成。效果如下:`  

    这是一个标准的代码块，由pre包裹code组合而成。  

##### 分割线

    用三个以上的星号(*)、减号(-)、底线( _ )来建立一个分隔线，行内不能有其他东西;也可以在星号或是减号中间插入空格。

  `***`  
  `* * *`  
  `*******`  
  `- - -`  
  `----------------------`  
  `均可产生如下所示的分割线:`

  ----------------------  

##### 列表

    无序列表：使用星号(*)、加号(+)或减号(-)作为列表标记，标记类型为实心原点。

    有序列表：使用数字+英文句点+空格作为列表标记。注意：在列表标记上使用的数字并不会影响输出的 HTML 结果，数值可相同也可不连续。

  `*   列表1`  
  `*   列表2`  
  `*   列表3`

    *   列表1
    *   列表2
    *   列表3

  `1.  列表1`  
  `3.  列表2`  
  `2.  列表3`  

    1.  列表1
    3.  列表2
    2.  列表3

#### 区段元素

##### 链接
    支持两种形式的链接语法: 行内式和参考式. 不管是哪一种链接文字都用[方括号]来标记.

  行内式格式：在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，
  用双引号把 title 文字包起来即可。即：[链接文本](链接网址 "title")；  
  参考式格式：在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记。  
  即：[链接文本][id值]；[id值]:链接网址 "title"；

`[百度](http://www.baidu.com/)`  
[百度](http://www.baidu.com/)  


`[百度][baidu]`  
`[baidu]:http://www.baidu.com "这是百度的链接"`  
[百度][baidu]  
[baidu]:http://www.baidu.com "这是百度的链接"  


##### 图片

    MD使用一种和链接很相似的语法来标记图片，同样也允许两种样式：行内式和参考式。目前还无法为图片设置宽高！  

  `行内式：![图片替代文本](图片地址 "title")`  

  `参考式：![alt 图片替代文本][id]`  
  `[id]：图片地址 "title"`  
