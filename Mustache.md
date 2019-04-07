# :black_joker:Mustache模板语言 #

>Web 模板引擎是为了使用户界面与业务数据（内容）分离而产生的，它可以生成特定格式的文档，通常是标准的 HTML 文档。当然不同的开发语言有不同模板引擎，如 Javascript 下的 Hogan 、ASP 下的 aspTemplate、以及 PHP 下的 Smarty，这里主要介绍基于 Javascript 语言的模板引擎，目前流行有 Mustache、Hogan、doT.js、JsRender、Kendo UI Templates等，jsperf.com 上可以看到它们的性能对比，首先先介绍下 Mustache。


:arrow_double_down: [`1.Mustache 简介`](#one) 

:arrow_double_down: [`2.Mustache使用`](#two) 

:arrow_double_down: [`3.Mustache条件和循环`](#three) 

:arrow_double_down: [`4.其他用途`](#other) 

<b id="one"></b>

### :flower_playing_cards:Mustache 简介 ### 

Mustache 是一个 logic-less （轻逻辑）模板解析引擎，它的优势在于可以应用在 Javascript、PHP、Python、Perl 等多种编程语言中。

下面是一个简单的示例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<link rel="stylesheet" href="http://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css">  
        <link rel="stylesheet" href="css/focus.css" >
		<script src="Hello.js" defer="defer"></script>
		<script src="https://cdn.bootcss.com/mustache.js/3.0.1/mustache.js"></script>
	</head>
	<body>
		<div id="stuInfor">
			<h4>{{name}}</h4><br>
			<p>{{age}}</p>
			<p>{{id}}</p>
			<p>{{sex}}</p>
			<p>加载完成</p>
		</div>
	</body>
	<script>
			var  student = {
				name : "小刘",
				age : 19,
				id : '2017110329',
				sex :'男'
			}

			var stuInfor =document.getElementById("stuInfor").innerText;
			Mustache.parse(stuInfor);
			var result = Mustache.render(stuInfor,student);
			document.getElementById("stuInfor").innerText = result;
	</script>
</html>
```

点击运行就可以查看到内容已被对象数据取代。

下面我们来介绍这一实现：

首先我们将需要输入的文本dom取到，即上面的div，然后使用`Mustache.parse()`方法将文本进行编译，即读取{{}}中的内容编码等，然后再使用`Mustache.render()`方法加载数据进文本，最后进行将编译好的文本再传入dom中，即完成显示。可见整个过程就是字符串的解析与编译完成了这个过程。

<b id="two"></b>

### :flower_playing_cards:2.Mustache使用 ### 

首先需要引入这个模板的js库，可以使用下面这个在线js库：

```html
<script src="https://cdn.bootcss.com/mustache.js/3.0.1/mustache.js"></script>
```

**语法**

使用`{{}}`可以向dom中插入数据，`{{!}} `表示注释.

我们使用原生js来进行操作，前面说过首先需要一个需要添加的数据的dom，如下一个简单的添加：

```html

<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<link rel="stylesheet" href="http://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css">  
        <link rel="stylesheet" href="css/focus.css" >
		<script src="Hello.js" defer="defer"></script>
		<script src="https://cdn.bootcss.com/mustache.js/3.0.1/mustache.js"></script>
	</head>
	<body>
		<div id="data">
			<h2 style="color:red;">{{name}}</h2>
		</div>
	</body>
	<script>
			var data = {
				name : 'Lumnca'
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
	</script>
</html>
```

点击运行可见Lumnca内容并且还具有css样式。这就说明了Mustache解析html的DOM是完全解析的包含所有的信息。那么我们一定要使用对象传入吗？下面我们就行尝试：

```javascript
			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,"lumnca");
			document.getElementById("data").innerHTML = result;
```

我们会发现不行，那我们改为一个对象的属性：

```javascript
			var data = new Object();
			data.name = "Lumnca";
			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
```

点击运行，可以显示，这就说明了必须要为对象的一个属性。可以看出Mustache解析是通过对象类型来引入的。所以需要我们传入类对象。

**Html字符转义**

在字符串含有html标签不会被解析为标签，而是直接显示

```html

<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<link rel="stylesheet" href="http://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css">  
        <link rel="stylesheet" href="css/focus.css" >
		<script src="Hello.js" defer="defer"></script>
		<script src="https://cdn.bootcss.com/mustache.js/3.0.1/mustache.js"></script>
		<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
	</head>
	<body>
		<div id="data">
			{{name}}
		</div>
	</body>
	<script>
			var data = {
				name : '<h2>Lumnca</h2>'
			}
			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
	</script>
</html>
```
运行可见并不会输出h2标签，即使使用Hello &lt;b&gt;JxKicker&lt;/b&gt也不能变成html标签，这也是为了防止xss攻击。所以不会转义为标签。

**插入位置不受限**

你可以在dom中任意位置插入需要填充的值，如下，还可以设置css值：

```html
	<body>
		<div id="data">
			<h2 style="color:{{color}};">{{name}}</h2>
		</div>
	</body>
	<script>
			var data = {
				name : 'Lumnca',
				color : 'blue'
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
	</script>
```

<b id="three"></b>

### :flower_playing_cards:3.Mustache条件和循环 ### 

通过`{{#param}} {{/param}} `我们可以完成很多的功能

**if判断**

我们可以使用判断语法来让这个数值是否显示：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<link rel="stylesheet" href="http://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css">  
        <link rel="stylesheet" href="css/focus.css" >
		<script src="Hello.js" defer="defer"></script>
		<script src="https://cdn.bootcss.com/mustache.js/3.0.1/mustache.js"></script>
		<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
	</head>
	<body>
		<div id="data">
			<h2 style="color:red;">{{#flag}}  用户名:{{name}}  {{/flag}}</h2>
		</div>
	</body>
	<script>
			var data = {
				flag : true,
				name : 'Lumnca'
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
	</script>
</html>
```

`{{#flag}}  用户名:{{name}}  {{/flag}}`即为条件语句，两边的`{{#flag}}    {{/flag}}`即为条件判断的范围，即起始#到结束/。中间为条件为真的时候需要显示的内容。而#falg和/falg则是监听是否为真的的条件。为true就显示，是空或者null，或者是false 都不显示。如果你想取反即条件为错显示时只需要使用取反操作符即可。将{{#flag}}替换为{{^flag}}即可。

```html
	<body>
		<div id="data">
			<h2 style="color:red;">{{^flag}}  用户名:{{name}}  {{/flag}}</h2>
		</div>
	</body>
	<script>
			var data = {
				flag : false,
				name : 'Lumnca'
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,data);
			document.getElementById("data").innerHTML = result;
	</script>
```

**循环**

如果你需要按照一定的形式传入，可以将数据类型数组化，再循环导入：

```html
	<body>
		<div id="data">
			<h2 style="color:red;">家族：{{family}}</h2>
			{{#people}}<p>姓名： {{name}} -- 年龄：{{age}} </p>{{/people}}
		</div>
	</body>
	<script>
			var datas = {
				family : "LIU",
				people : [
					{name : "lbh",age : 48},
					{name : "cxq",age : 47},
					{name : "lmc",age : 21}
				]
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,datas);
			document.getElementById("data").innerHTML = result;
	</script>
```

这里并没有看到循环的语法，但是我们有`{{#people}}  {{/people}}`这个判断，这里可以理解为，这个判断的为这个类型的长度，由于这个类型有3个对象，所以只执行3次并且输出里面的内容。我们可以利用这种来输出多数据类型相同的数据。如果类型不是对象而是数组，则需要使用数组专用的访问方法：

```html
	<body>
		<div id="data">
			{{#names}}<p>姓名：{{.}} </p>{{/names}}
		</div>
	</body>
	<script>
			var datas = {
				names : ["Lumnca","Kailly","Reblim"]
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,datas);
			document.getElementById("data").innerHTML = result;
	</script>
```

值得注意的是数组也必须写在对象里面，然后去判断数组，使用`{{.}}`访问当前元素。


**函数**

你可以通过编写函数来修改数值传入：

```html
	<body>
		<div id="data">
			{{#user}}<p>ID:{{id}} </p>{{/user}}
		</div>
	</body>
	<script>
			var datas = {
				
				user : [
					{name : "lumnca" ,age : 12},
					{name : "kay" ,age : 17},
					{name : "tom" ,age : 15}
				],

				id : function(){
					return "user"+this.age+this.name;
				}
			}

			var dataText =document.getElementById("data").innerHTML;
			Mustache.parse(dataText);
			var result = Mustache.render(dataText,datas);
			document.getElementById("data").innerHTML = result;
			
	</script>
```

<b id="other"></b>

### :flower_playing_cards:Mustache其他用途 ### 

Mustache可以将json文件转化为类对象再格式化输出，这样就可以很方便输出表格式文件，包括数据库的表，表格等处理十分有用。






