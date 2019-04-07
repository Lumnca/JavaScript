# :black_joker:Mustache模板语言 #

>Web 模板引擎是为了使用户界面与业务数据（内容）分离而产生的，它可以生成特定格式的文档，通常是标准的 HTML 文档。当然不同的开发语言有不同模板引擎，如 Javascript 下的 Hogan 、ASP 下的 aspTemplate、以及 PHP 下的 Smarty，这里主要介绍基于 Javascript 语言的模板引擎，目前流行有 Mustache、Hogan、doT.js、JsRender、Kendo UI Templates等，jsperf.com 上可以看到它们的性能对比，首先先介绍下 Mustache。


:arrow_double_down: [`1简介`](#one) 
:arrow_double_down: [`2.编译说明`](#parse) 
:arrow_double_down: [`3.条件和循环`](#ifelsefor) 
:arrow_double_down: [`4.其他用途`](#other) 


### :flower_playing_cards:Mustache 简介 ### <b id="one"></b>

Mustache 是一个 logic-less （轻逻辑）模板解析引擎，它的优势在于可以应用在 Javascript、PHP、Python、Perl 等多种编程语言中。

### :flower_playing_cards:Mustache示例 ###

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





