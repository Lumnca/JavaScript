## :beginner:JSON ##

<p id="title"></p>

### 目录点击链接 ###
:point_right:<a href="#one" >JSON简介<a><br>
:point_right:<a href="#two" >JSON语法<a><br>
:point_right:<a href="#three" >JSON解析<a><br>
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

<p id = "two"></p>

### ---------------------------------------------------JSON语法--------------------------------------------- ###

<a href="#title">:arrow_up:返回目录</a>

JSON 语法是 JavaScript 对象表示语法的子集。

 * 数据在名称/值对中
 * 数据由逗号分隔
 * 大括号保存对象
 * 中括号保存数组

**:memo:JSON 名称/值对**

JSON 数据的书写格式是：名称/值对。

名称/值对包括字段名称（在双引号中），后面写一个冒号，然后是值：

`"name" : "lumnca"`

这很容易理解，等价于这条 JavaScript 语句：

`name = "lumbnca"`

与JavaScript字符串与JSON字符串不同的是，JSON必须使用双引号，要不然会有语法错误。

**:memo:JSON 对象**

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

```JavaScript
{
	"name" : "LMC",
	"age" : 20,
	"family" : {
		"name" : "LBH",
		"age" : 47
	}
}
```
这里虽然有两个name属性,但是由于两个是不同的类型，所以这样没有错误，如果是同一对象，就不能出现两个属性。

**:memo:JSON 数组**

与对象一样，数组也是复杂类型，在JavaScript中的数组：

```
    var values = ["NHA",56,true];
```
在JSON中可以用同样的方法命名：

```
    [25,"Hi",true]
```
同样要注意JSON没有变量与分号，把数组与对象结合起来，可以构成更复杂的数据结构集合：

```JavaScript
[
	{
		"name" : "LMC",
		"Infor" : ["CS",2017],
		"age" : 20
		
	},
	{
		"name" : "JX",
		"Infor" : ["CS",2016],
		"age" : 20
	},
	{
		"name" : "LJK",
		"Infor" : ["CS",2016],
		"age" : 20
	}
]
```
像上面这样，首先是一个数组，但是元素又是对象，对象里面又是数组，这样就构成复杂类型数据。

<p id = "three"></p>

## -----------------------------------JSON解析---------------------------------- ##

<a href="#title">:arrow_up:返回目录</a>

**:memo:JSON.parse()**

JSON 通常用于与服务端交换数据。在接收服务器数据时一般是字符串。我们可以使用 JSON.parse() 方法将数据转换为 JavaScript 对象。

语法：`JSON.parse(text, reviver)`

参数说明：

 * text:必需， 一个有效的 JSON 字符串。
 * reviver: 可选，一个转换结果的函数， 将为对象的每个成员调用此函数。
 
如下：
```JavaScript
    var jsonValue = JSON.parse('{"name" : "LMC","age" : 20}');
		document.getElementById("a3").innerHTML = jsonValue.name+"<br>"+jsonValue.age;
 ```
如果想加入函数，可以向下面这样：

```JavaScript 
		    var jsonValue = JSON.parse('{"name" : "LMC","age" : 20}',ShowData);  
		    function ShowData(key,value){
				alert(key+":"+value);		
		    }
```

值的注意的是，该函数有两个参数，分别是键类型，和值类型。所以我们使用key和value来代替。键类型是对应的属性名，value对应的是属性的值，像上面会弹出
name: LMC和age : 20这样的信息。

**:memo:JSON.stringify()**

JSON 通常用于与服务端交换数据。在向服务器发送数据时一般是字符串。我们可以使用 JSON.stringify() 方法将 JavaScript 对象转换为字符串。

语法:`JSON.stringify(value, replacer, space)`

参数说明：

 * value:
必需， 一个有效的 JSON 对象。

 * replacer:
 可选。用于转换结果的函数或数组。

 * 如果 replacer 为函数，则 JSON.stringify 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回 undefined，则排除成员。根  对象的键是一个空字符串：""。如果 replacer 是一个数组，则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。当 value 参数也为数组时，将忽略 replacer 数组。

 * space:
可选，文本添加缩进、空格和换行符，如果 space 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 space 大于 10，则文本缩进 10 个空格。space 有可以使用非数字，如：\t。

最简单就像下面这样，返回一个JSON的字符串：

```JavaScript
	var jsonValue = JSON.parse('{"name" : "LMC","age" : 20}');		    
	var Text = JSON.stringify(jsonValue);	    
	alert(Text);
```


如果第二参数为数组，那么数组里的参数要为属性名，表示要返回这些数据。如下只想返回关于姓名的属性：

```JavaScript
	var jsonValue = JSON.parse('{"name" : "LMC","age" : 20}');	    
	var Text = JSON.stringify(jsonValue,["name"]);
	alert(Text);
```

同理如果要加入函数，函数需要两个参数分别为键和值，对应的key返回值为key的值：

```JavaScript
		    var jsonValue = JSON.parse('{"name" : "LMC","age" : 20}');
		    var Text = JSON.stringify(jsonValue,ShowData);
		    alert(Text);		    
		    function ShowData(key,value){
		    	if(key=="name"){
		    		return "liuminchaun";
		    	}
		    	else if(key=="age"){
		    		return "19980317";
		    	}
		    	else{
		    		return value;
		    	}
		    }

```
上面就会返回 {"name":"liuminchaun","age":"19980317"} 因为我们对值进行了修改。第三个参数是对文本进行字符串缩进，其实就是对空格处理，如果是数字
代表着对于空格进行多少个空格,如果是字符串，这就显示字符串，对于数字并不一定会转换为空格，因为他要满足一定条件才能进行缩进。推荐使用字符串：

```JavaScript
		    var jsonValue = JSON.parse('{ " name " : "LMC" ," age " : 20 }');
		    
		    var Text = JSON.stringify(jsonValue,ShowData,"--SPACE--");
		    
		    document.getElementById("a3").innerHTML = Text;

```

会显示如下结果：{ --SPACE--" name ": "LMC", --SPACE--" age ": 20 }

**:memo:toJSON()**

toJSON()是对解析的字符串进行重新解析的方法，如下：

```javascript
var book = {
    "bookname" : "三国志",
    "authors" : "陈寿",
    "year" : "晋朝",
    toJSON :function(key,value){
        return "{" + "bookname : "+this.bookname + " authors : " + this.authors+"}"
    }
};

var jsonText = JSON.stringify(book);

alert(jsonText);
```

上面结果会解析成return的字符串。也就是说对象如果存在toJSON方法则会将这个函数的返回值作为解析结果。如果stringify方法第二个参数为函数，则会将toJSON的返回值转入过滤函数中，同理格式化对象也是toJSON的返回值。

