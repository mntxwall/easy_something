<h1 id="head">markdown简单语法</h1>

+ [标题](#title)

+ [列表](#list)

+ [链接跳转](#linkjump)

+ [显示图片](#photo)

+ [引用](#quote)

+ [代码风格](#codestyle)

+ [其它](#other)

<h2 id="title">标题</h2>

\#  在html里是h1,也就是一级标题

\## 在html里是h2,也就是二级标题

\#号数量越多,表示相应html标题级数也增加,最多到六级标题


**\#号和标题之间是有一个空格**

还有一种表示标题的方式:在文字底下加上===或者是---

如:

```
Markdown
========

Markdown
--------

```

===与#一样,表示一级标题

---与##一样,表示二级标题

<h2 id="list">列表</h2>

列表分为**有序列表**和**无序列表**

**有序列表**只有一种写法:

在所要列举的内容前有序得加上`1. 2. 3.`

如:

```
1. 苹果
2. 香蕉
6. 桔子
```

1. 苹果
2. 香蕉
3. 桔子

**无序列表**有很多种表示方式

```
+ 苹果
+ 香蕉
- 桃子
* 梨
```

+ 苹果
+ 香蕉
- 桃子
* 梨

不论是`1.`还是`+ - *`与列表内容之间都有一个**空格**

列表可以嵌套

```
1. 项目
2. 内容
    + 内容1
    + 内容2
3. 进度
```

1. 项目
2. 内容
    + 内容1
    + 内容2
3. 进度

嵌入列表与行首是有**四个空格**的间距

<h2 id="linkjump">链接跳转</h2>

### 页面间跳转

点击[百度](http://www.baidu.com "百度")可以跳转到百度。

需要跳转的文字写在\[]号内,后面紧跟着的括号内填入要跳转的链接。页面间的跳转就完成了

上述跳转百度的语法如下：

```HTML
[百度](http://www.baidu.com)
```

还有另外一种*引用式*的语法格式

```HTML
[google][1]

[1]: http://www.google.com "Google"
```

[google][1]

[1]:http://www.google.com "Google"

引用式是在需要跳转的文字的\[]号后再接上另外的\[]号\(称这个\[]为引用\[])

引用\[]号填入内容可以认做是标记。

标记的具体内容可以写在页面的其他位置,只要满足标记的语法就可以了(标记的语法见上述语法块中的内容)。


如果你仔细观察会发现,这个链接是在当前页面里打开的,目前markdown不能实现在新的页面中打开链接。

如果要实现在新的页面中打开链接，我们就得使用HTML语法。

```HTML
<a href="http://www.baidu.com" target="_blank">百度</a>
```

<a href="http://www.baidu.com" target="_blank">百度</a>

### 页面内跳转

教会你新的知识**页面内跳转**

比如点击[回到行首](#head)会跳回到页面顶部

markdown实现这个功能也是需要加入HTML语法，借助HTML里的页面内跳转功能

```HTML

<span id="begin">开始</span>

[跳转到开始](#begin)

```
把`<span id="begin">开始</span>`放在页面的某个地方

`[跳转到开始](#begin)`就能跳转到相应的地方

语法与页面间跳转相差无几,\()内填入相就的ID就可以了。

<h2 id="photo">显示图片</h2>

```
![图片无法显示时显示的文字](/path/to/img.jpg "鼠标放到图片上后显示的文字")
```

```
![github 图片](http://github.global.ssl.fastly.net/images/modules/logos_page/Octocat.png "github")
```

![github 图片](http://github.global.ssl.fastly.net/images/modules/logos_page/Octocat.png "github")

显示图片也支持**引用式**

```HTML
![图片无法显示时显示的文字][引用式标识]

[引用式标识]: 图片地址 "鼠标放到图片上后显示的文字"
```

```
![github 图片][1]

[1]: http://github.global.ssl.fastly.net/images/modules/logos_page/Octocat.png "github"

```
![github][2]

[2]:http://github.global.ssl.fastly.net/images/modules/logos_page/Octocat.png

<h2 id="quote">引用</h2>

```
>鲁迅
>>狂人日记
```

>鲁迅
>>狂人日记

用\>来表示引用

\>>来表示引用的嵌套

<h2 id="codestyle">代码风格</h2>

代码风格分为两种**行内代码**和**代码段**

行内代码：

把需要以代码风格显示的文字放入\`\`号内,\`\`内的文字就会以代码风格的样式呈现在页面上。

```
这行内有`代码`
```
这行内有`代码`

代码段:

在代码的前一行和后一行分别加上\`\`\`,\`\`\`符号内的内容就会以代码段的形式呈现在页面上

```
\```
int main(char* args)
{
    printf("HelloWorld!");
    return 0;
}
\```
```

```
int main(char* args)
{
    printf("HelloWorld!");
    return 0;
}
```

<h2 id="other"> 其它</h2>

内容的前后加上\*或是\_表示斜体

\**或是\__表示粗体

\~~表示删除

```
*这是斜体*,_这也是斜体_

**这是粗体**,__这也是粗体__

~~这是删除~~

```
*这是斜体*,_这也是斜体_

**这是粗体**,__这也是粗体__

~~这是删除~~
