## :beginner:JSON ##

<p id="title"></p>

### 目录点击链接 ###
:point_right:<a href="#one" >JSON简介<a><br>
:point_right:<a href="#two" ><a>JSON语法<br>
:point_right:<a href="#three" ><a><br>
<p id = "one"></p>

### ---------------------------------------------------JSON简介--------------------------------------------- ###

<a href="#title">:arrow_up:返回目录</a>

* JSON: JavaScript Object Notation(JavaScript 对象表示法)

* JSON 是存储和交换文本信息的语法。类似 XML。

* JSON 比 XML 更小、更快，更易解析。

JSON实例：

```
{
    "sites": [
    { "name":"BCS组" , "url":"www.lumnca.com" }, 
    { "name":"谷歌" , "url":"www.google.com" }, 
    { "name":"百度" , "url":"www.baidu.com" }
    ]
}
```
**:memo:什么是 JSON ？**

  * JSON 指的是 JavaScript 对象表示法（JavaScript Object Notation）
  * JSON 是轻量级的文本数据交换格式
  * JSON 独立于语言：JSON 使用 Javascript语法来描述数据对象，但是 JSON 仍然独立于语言和平台。JSON 解析器和 JSON 库支持许多不同的编程语言。 目前非常多的动态（PHP，JSP，.NET）编程语言都支持JSON。
JSON 具有自我描述性，更易理解

**:memo:JSON - 转换为 JavaScript 对象**

JSON 文本格式在语法上与创建 JavaScript 对象的代码相同。由于这种相似性，无需解析器，JavaScript 程序能够使用内建的 eval() 函数，用 JSON 数据来生成原生的 JavaScript 对象。

**:memo:JSON与XML相同点**

  * JSON 是纯文本
  * JSON 具有"自我描述性"（人类可读）
  * JSON 具有层级结构（值中存在值）
  * JSON 可通过 JavaScript 进行解析
  * JSON 数据可使用 AJAX 进行传输
 
**:memo:与 XML 不同之处**

  * 没有结束标签
  * 更短
  * 读写的速度更快
  * 能够使用内建的 JavaScript eval() 方法进行解析
  * 使用数组
  * 不使用保留字
  
**:memo:为什么使用 JSON？**

对于 AJAX 应用程序来说，JSON 比 XML 更快更易使用：

 `使用 XML`
 
  * 读取 XML 文档
  * 使用 XML DOM 来循环遍历文档
  * 读取值并存储在变量中
  
 `使用 JSON`
 
  * 读取 JSON 字符串
  * 用 eval() 处理 JSON 字符串
  
### ---------------------------------------------------JSON语法--------------------------------------------- ###

<a href="#title">:arrow_up:返回目录</a>

JSON 语法是 JavaScript 对象表示语法的子集。

 * 数据在名称/值对中
 * 数据由逗号分隔
 * 大括号保存对象
 * 中括号保存数组

**JSON 名称/值对**

JSON 数据的书写格式是：名称/值对。

名称/值对包括字段名称（在双引号中），后面写一个冒号，然后是值：

`"name" : "菜鸟教程"`

这很容易理解，等价于这条 JavaScript 语句：

`name = "菜鸟教程"`

与JavaScript字符串与JSON字符串不同的是，JSON必须使用双引号，要不然会有语法错误。

**JSON 对象**

首先看下JavaScript中的对象写法：

```JavaScript
	var people = {
	  name : "LMC",
	  "age" : 20
	};
```
但是JSON要求给对象加上双引号，所以上述改写成JSON为：

```JSON
{
	"name" : "LMC",
	"age" : 20
}
```
与上面的相比可以看出JSON没有声明对象名，其次末尾没有分号。一定要注意对象属性必须加双引号，关于属性值可以是简单值也可以是复杂值，因此可以在对象中
添加对象：

```
{
	"name" : "LMC",
	"age" : 20,
	"family" : {
		"name" : "LBH",
		"age" : 47
	}
}
```






