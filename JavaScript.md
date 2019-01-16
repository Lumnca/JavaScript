## :gem: JavaScript语言 ## 

JavaScript 是一种专为与网页交互而设计的脚本语言，由以下三个部分组成：

  * ECMAScript，由ECMA-262定义，提供核心语言功能；
  
  * 文档对象模型（DOM），提供访问和操作网页内容的方法和接口；
  
  * 浏览器对象模型（BOM），提供与浏览器交互的方法和接口；
  
 在实际网页开发中，JavaScript主要是用于网页动态效果渲染，以及一些数据交互。当然现在JavaScript也能够开发后台，甚至还可以做很多东西，比如H5游戏（网页游戏），和一些游戏引擎（LayAir，Unity）等都支持JavaScript语言，JavaScript语言也从只能做网页扩展了出来，连大家熟悉的Vscode也是JavaScript写出来的编译软件，而且在前端方面，JavaScript是十分重要的核心。所以这门语言建议大家都去掌握一下。
 
## :gem: JavaScript编译 ##

JavaScript编译和Html基本一致，我们使用JavaScript也是基于Html上使用，所以能够支持Html编译的，JavaScript也就能够编译，最最简单的是直接使用浏览器编译，也就是在浏览器的开发者工具中的控制台（Console）使用（F12）,如下所示，在控制台上显示Hello World：

![](https://github.com/Lumnca/StudyJS/blob/master/Images/a1.png)

当然我们不推荐这样练习JavaScript，还是需要一个编译器，可以使用Vscode以及其他支持Html编译的软件。但是控制台一般是我们用来验证数据和debug用的。JavaScript属于弱语言，也就是说，它不像其他高级语言一样，只要语法错误就不能编译，它是无论是否你写对它都能够编译，所以写JavaScript要注意自己的代码是否错误。

## :gem: script 标签 ##

向Html页面中插入JavaScript的主要方法就是使用`<script>`标签，这个标签也是Html插入其他代码的标签，在Html中这个标签共有以下几个属性：

 * async : 可选。表示应该立即下载脚本，但不妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。
 
 * charset ： 可选，表示通过src属性指定代码的字符集，由于大多数浏览器会忽视它的值，所以这个不经常使用。

 * defer ： 可选，表示脚本可以延迟到文档完全被解析和显示后才执行。
 
 * src ： 可选。表示要执行代码的外部文件。
 
 * type ： 可选，表示文件的属性，这个并不需要，在使用时，不写这个会被默认为text/JavaScript也就是js语言，所以这个没必要写上。
 
## :gem: JavaScript引用 ##

如果需要使用JavaScript代码量比较少，可以直接写在Html文档中，如下在网页上弹出一个Hello World！：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>基本知识</title>  
	</head>
	<body>
		<script>
			alert("Hello World!");
		</script>
	</body>
</html>
```

`alert("Hello World!");`即为JavaScript代码，它是镶嵌在标签中，在两个script标签中，即为JavaScript代码的执行区域。可以编写多个scripe标签来完成对多个代码块的执行，但是我们去查看别人的网页很少能见到代码写在标签中的，如下：

![](https://github.com/Lumnca/StudyJS/blob/master/Images/a2.png)

我们可以看到别人使用的是从外部加载的办法，也就是说别人的代码是事先写在了其他地方上，然后再从Html中引用这个代码，这样做可以处理一些代码量大的工作，以及代码的安全和维护。我们也可使用这种方法：

 * 第一步编写JavaScript代码文件（JavaScript文件以.js为扩展名）
 
 * 第二步引用这个JavaScript文件
 
 如下显示

```Html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>基本知识</title>  
	</head>
	<body>
		<script src="Hello.js"></script>
	</body>
</html>
```

如上Hello.js即为我写的JavaScript代码。这样就完成了对代码的引用，那么在js文件中我们需要做什么呢？其实在Js文件中不需要额外声明什么，直接开始编写代码即可


 
 
 
 
