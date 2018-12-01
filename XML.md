## ------------------------------------------XML简介---------------------------------------- ##

#### :tropical_fish:简介 ####
* XML 指可扩展标记语言（eXtensible Markup Language）。

* XML 被设计用来传输和存储数据。

* XML 很重要，也很容易学习。

#### :tropical_fish:与Html的区别 ####

* XML 被设计用来传输和存储数据。

* HTML 被设计用来显示数据。

#### :tropical_fish:什么是XML
* XML 指可扩展标记语言（EXtensible Markup Language）。
* XML 是一种很像HTML的标记语言。
* XML 的设计宗旨是传输数据，而不是显示数据。
* XML 标签没有被预定义。您需要自行定义标签。
* XML 被设计为具有自我描述性。
* XML 是 W3C 的推荐标准。

## ---------------------------------------------XML用途---------------------------------- ##

* :fish: **把数据从 XMLHTML 分离**

如果您需要在 HTML 文档中显示动态数据，那么每当数据改变时将花费大量的时间来编辑 HTML。

通过 XML，数据能够存储在独立的 XML 文件中。这样您就可以专注于使用 HTML/CSS 进行显示和布局，并确保修改底层数据不再需要对 HTML 进行任何的改变。

通过使用几行 JavaScript 代码，您就可以读取一个外部 XML 文件，并更新您的网页的数据内容。

* :fish:  **XML简化数据共享**

在真实的世界中，计算机系统和数据使用不兼容的格式来存储数据。

XML 数据以纯文本格式进行存储，因此提供了一种独立于软件和硬件的数据存储方法。

这让创建不同应用程序可以共享的数据变得更加容易。

* :fish: **XML简化数据传输**

对开发人员来说，其中一项最费时的挑战一直是在互联网上的不兼容系统之间交换数据。

由于可以通过各种不兼容的应用程序来读取数据，以 XML 交换数据降低了这种复杂性。

* :fish: **XML使您的数据更有用**
结构
不同的应用程序都能够访问您的数据，不仅仅在 HTML 页中，也可以从 XML 数据源中进行访问。

通过 XML，您的数据可供各种阅读设备使用（掌上计算机、语音设备、新闻阅读器等），还可以供盲人或其他残障人士使用。
* :fish: **XML简化平台变更**

升级到新的系统（硬件或软件平台），总是非常费时的。必须转换大量的数据，不兼容的数据经常会丢失。

XML 数据以文本格式存储。这使得 XML 在不损失数据的情况下，更容易扩展或升级到新的操作系统、新的应用程序或新的浏览器。

## ----------------------------------XML树---------------------------------------- ##

一个XML文档实例：

```
<?xml version="1.0" encoding="UTF-8"?>
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
```
第一行是 XML 声明。它定义 XML 的版本（1.0）和所使用的编码（UTF-8 : 万国码, 可显示各种语言）。

下一行描述文档的根元素.与Html的body一样<note>是这个文档的主体。然后里面就是各种元素。像Html其他的标签一样，层层嵌套。
  
## ----------------------------------XML语法---------------------------------------- ##
#### XML 文档必须有根元素 ####
XML 必须包含根元素，它是所有其他元素的父元素，可以为root 或者 note 与Html一样为最外层的标签。
  
**:whale2:XML 声明**
  
XML 声明文件的可选部分，如果存在需要放在文档的第一行，如下所示：
  
```
  <?xml version="1.0" encoding="utf-8"?>
```
 以上实例包含 XML 版本（UTF-8 也是 HTML5, CSS, JavaScript, PHP, 和 SQL 的默认编码。
 
 **:whale2:所有的 XML 元素都必须有一个关闭标签**
 
 在 HTML 中，某些元素不必有一个关闭标签,在 XML 中，省略关闭标签是非法的。所有元素都必须有关闭标签;
 
 ```
 //Html支持,XMl中错误
 <p>This is a paragraph.
<br>
```
**:whale2:XML 标签对大小写敏感**

XML 标签对大小写敏感。标签 <Letter> 与标签 <letter> 是不同的。

必须使用相同的大小写来编写打开标签和关闭标签：

```
<Message>这是错误的</message>
<message>这是正确的</message>
```
**:whale2:XML 必须正确嵌套**

在 HTML 中，常会看到没有正确嵌套的元素：

```
<b><i>This text is bold and italic</b></i>
```
在 XML 中，所有元素都必须彼此正确地嵌套：

```
<b><i>This text is bold and italic</i></b>
```
**:whale2:XML 属性值必须加引号**

与 HTML 类似，XML 元素也可拥有属性（名称/值的对）。在 XML 中，XML 的属性值必须加引号。请研究下面的两个 XML 文档。 第一个是错误的，第二个是正确的：

```
//没有加引号错误
<note date=12/11/2007>
<to>Tove</to>
<from>Jani</from>
</note>
```

```
//正确
<note date="12/11/2007">
<to>Tove</to>
<from>Jani</from>
</note>
```
对于多个属性运用可以像下面一样：
```
<元素名 属性名1="属性值1" 属性名2="属性值2">
```
特定的属性名称在同一个元素标记中只能出现一次

**:whale2:实体引用**

在 XML 中，一些字符拥有特殊的意义。如果您把字符 "<" 放在 XML 元素中，会发生错误，这是因为解析器会把它当作新元素的开始。与Html一样
需要转码或者实体引用。

**:whale2:XML 中的注释**

在 XML 中编写注释的语法与 HTML 的语法很相似。

```
<!-- This is a comment -->
```
**:whale2:在 XML 中，空格会被保留**

HTML 会把多个连续的空格字符裁减（合并）为一个,在 XML 中，文档中的空格不会被删减。

## --------------------------------------------XML 元素--------------------------------- ##

通过下面这个例子来说明

```
<bookstore>
    <book category="CHILDREN">
        <title>Harry Potter</title>
        <author>J K. Rowling</author>
        <year>2005</year>
        <price>29.99</price>
    </book>
    <book category="WEB">
        <title>Learning XML</title>
        <author>Erik T. Ray</author>
        <year>2003</year>
        <price>39.95</price>
    </book>
</bookstore>
```

```在上面的实例中，<bookstore> 和 <book> 都有 元素内容，因为他们包含其他元素。<book> 元素也有属性（category="CHILDREN"）。<title>、<author>、<year> 和 <price> 有文本内容，因为他们包含文本。```

## ----------------------------------XML 属性-------------------------------------------- ##

**XML 属性**

XML元素具有属性，类似 HTML。属性（Attribute）提供有关元素的额外信息。

在 HTML 中，属性提供有关元素的额外信息：

```
<img src="computer.gif">
<a href="demo.html">
```
属性通常提供不属于数据组成部分的信息。在下面的实例中，文件类型与数据无关，但是对需要处理这个元素的软件来说却很重要：

```
<file type="gif">computer.gif</file>
```

**XML属性必须加引号**

属性值必须被引号包围，不过单引号和双引号均可使用。比如一个人的性别，person 元素可以这样写：

`<person sex="female"> `
或者这样也可以：

`<person sex='female'>`
如果属性值本身包含双引号，您可以使用单引号，就像这个实例：

`<gangster name='George "Shotgun" Ziegler'>`
或者您可以使用字符实体：

`<gangster name="George &quot;Shotgun&quot; Ziegler">`

`XML 元素 vs. 属性`
请看这些实例：

```
<person sex="female">
<firstname>Anna</firstname>
<lastname>Smith</lastname>
</person>
```
```
<person>
<sex>female</sex>
<firstname>Anna</firstname>
<lastname>Smith</lastname>
</person>
```
在第一个实例中，sex 是一个属性。在第二个实例中，sex 是一个元素。这两个实例都提供相同的信息。

没有什么规矩可以告诉我们什么时候该使用属性，而什么时候该使用元素。我的经验是在 HTML 中，属性用起来很便利，但是在 XML 中，您应该尽量避免使用属性。如果信息感觉起来很像数据，那么请使用元素吧。

**避免 XML 属性？**

因使用属性而引起的一些问题：

   * 属性不能包含多个值（元素可以）
   * 属性不能包含树结构（元素可以）
   * 属性不容易扩展（为未来的变化）
   * 属性难以阅读和维护。请尽量使用元素来描述数据。而仅仅使用属性来提供与数据无关的信息。

不要做这样的蠢事（这不是 XML 应该被使用的方式）：

**针对元数据的 XML 属性**

有时候会向元素分配 ID 引用。这些 ID 索引可用于标识 XML 元素，它起作用的方式与 HTML 中 id 属性是一样的。这个实例向我们演示了这种情况：

```
<messages>
<note id="501">
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
<note id="502">
<to>Jani</to>
<from>Tove</from>
<heading>Re: Reminder</heading>
<body>I will not</body>
</note>
</messages>

```
上面的 id 属性仅仅是一个标识符，用于标识不同的便签。它并不是便签数据的组成部分。

在此我们极力向您传递的理念是：元数据（有关数据的数据）应当存储为属性，而数据本身应当存储为元素。

## -------------------------------------XML DOM----------------------------------------- ##

其实还有对于XML的验证与查看这里就没有一一排列，这里没有对这些进行演示。重点来了，前面说了那么多，相信你们总会有疑问，我该怎么用？，下面介绍
对XML中数据的显示。

首先是定义一个XMl文档取名叫做 my.xml 类容如下

```
<note>
	<people>
		<name>Lumnca</name>
		<age>20</age>
		<sex>男</sex>
	</people>
	<people>
		<name>Jgxg</name>
		<age>20</age>
		<sex>男</sex>
	</people>
</note>
```

一般XML DOM我们使用JavaScript来获取，在网页中添加脚本：

```Javascript
	<body>

		<div>
			<ul>
				<li></li>
				<li></li>
				<li></li>
			</ul>
		</div>
		<a href="my.xml">查看文档</a>
		<script>
			if (window.XMLHttpRequest)
			{// code for IE7+, Firefox, Chrome, Opera, Safari
				xmlhttp=new XMLHttpRequest();
			}
			else
			{// code for IE6, IE5
				xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
			}
     			 //请求需要为异步方式为false
			xmlhttp.open("GET","my.xml",false);
			xmlhttp.send();
			xmlDoc=xmlhttp.responseXML;
			
			document.getElementsByTagName("li")[0].innerHTML =
			//取第一个name标签
			xmlDoc.getElementsByTagName("name")[0].childNodes[0].nodeValue;
			
			document.getElementsByTagName("li")[1].innerHTML =
			//取第一个age标签
			xmlDoc.getElementsByTagName("age")[0].childNodes[0].nodeValue;
			
			document.getElementsByTagName("li")[2].innerHTML =
			xmlDoc.getElementsByTagName("sex")[0].childNodes[0].nodeValue;

		</script>
	</body>
```

像上面最终会生成XML里面的数据，XML中DOM对象与Html中Dom对象是一样的取法。但是要注意的是要显示输出要写全`childNodes[0].nodeValue`才能访问到元素
上面是JavaScript访问XMl文档，反过来还可以使用JavaScript创建一个XML文档：

```Javascript
<script>
			txt="<note>";
			txt=txt+"<name>Tove</name>";
			txt=txt+"<age>23</age>";
			txt=txt+"<sex>女</sex>";
			txt=txt+"</note>";
			
			if (window.DOMParser)
			{
				//生成XML文档
				Newparser = new DOMParser();
				xmlDoc = Newparser.parseFromString(txt,"text/xml");
			}
			else // Internet Explorer
			{
				//生成XML文档
				xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
				xmlDoc.async=false;
				xmlDoc.loadXML(txt);
			}	
			
			document.getElementsByTagName("li")[0].innerHTML =
			xmlDoc.getElementsByTagName("name")[0].childNodes[0].nodeValue;
			
			document.getElementsByTagName("li")[1].innerHTML =
			xmlDoc.getElementsByTagName("age")[0].childNodes[0].nodeValue;
			
			document.getElementsByTagName("li")[2].innerHTML =
			xmlDoc.getElementsByTagName("sex")[0].childNodes[0].nodeValue;

</script>
```
像这样我们可以自行写入一个XML文档，但这个并不会保存在文件上，而而是一个字符串上。关于XML还有许多，但我们只针对JavaScript所以只介绍这些，想了解XML的应用实例与更多知识可以继续学习，参考网站[XML学习](http://www.runoob.com/xml/xml-real-life.html)
