# ------------------JavaScript运行 --------------------- #

<p id="title"></p>

## 目录 ##

:arrow_down:<a href="#a1">1.JavaScript语言</a>

:arrow_down:<a href="#a2">2.JavaScript编译</a>

:arrow_down:<a href="#a3">3.script 标签</a>

:arrow_down:<a href="#a4">4.JavaScript引用 </a>

<p id="a1"></p>

## :gem: JavaScript语言 ## 

:arrow_double_up:<a href = "#title">返回目录</a>

JavaScript 是一种专为与网页交互而设计的脚本语言，由以下三个部分组成：

  * ECMAScript，由ECMA-262定义，提供核心语言功能；
  
  * 文档对象模型（DOM），提供访问和操作网页内容的方法和接口；
  
  * 浏览器对象模型（BOM），提供与浏览器交互的方法和接口；
  
 在实际网页开发中，JavaScript主要是用于网页动态效果渲染，以及一些数据交互。当然现在JavaScript也能够开发后台，甚至还可以做很多东西，比如H5游戏（网页游戏），和一些游戏引擎（LayAir，Unity）等都支持JavaScript语言，JavaScript语言也从只能做网页扩展了出来，连大家熟悉的Vscode也是JavaScript写出来的编译软件，而且在前端方面，JavaScript是十分重要的核心。所以这门语言建议大家都去掌握一下。
 
<p id="a2"></p>

## :gem: JavaScript编译 ##

:arrow_double_up:<a href = "#title">返回目录</a>

JavaScript编译和Html基本一致，我们使用JavaScript也是基于Html上使用，所以能够支持Html编译的，JavaScript也就能够编译，最最简单的是直接使用浏览器编译，也就是在浏览器的开发者工具中的控制台（Console）使用（F12）,如下所示，在控制台上显示Hello World：

![](https://github.com/Lumnca/StudyJS/blob/master/Images/a1.png)

当然我们不推荐这样练习JavaScript，还是需要一个编译器，可以使用Vscode以及其他支持Html编译的软件。但是控制台一般是我们用来验证数据和debug用的。JavaScript属于弱语言，也就是说，它不像其他高级语言一样，只要语法错误就不能编译，它是无论是否你写对它都能够编译，所以写JavaScript要注意自己的代码是否错误。

<p id="a3"></p>

## :gem: script 标签 ##

:arrow_double_up:<a href = "#title">返回目录</a>

向Html页面中插入JavaScript的主要方法就是使用`<script>`标签，这个标签也是Html插入其他代码的标签，在Html中这个标签共有以下几个属性：

 * async : 可选。表示应该立即下载脚本，但不妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。
 
 * charset ： 可选，表示通过src属性指定代码的字符集，由于大多数浏览器会忽视它的值，所以这个不经常使用。

 * defer ： 可选，表示脚本可以延迟到文档完全被解析和显示后才执行。
 
 * src ： 可选。表示要执行代码的外部文件。
 
 * type ： 可选，表示文件的属性，这个并不需要，在使用时，不写这个会被默认为text/JavaScript也就是js语言，所以这个没必要写上。

<p id="a4"></p>

## :gem: JavaScript引用 ##

:arrow_double_up:<a href = "#title">返回目录</a>

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

如上Hello.js即为我写的JavaScript代码。这样就完成了对代码的引用，那么在js文件中我们需要做什么呢？其实在Js文件中不需要额外声明什么，直接开始编写代码即可如上面所引用的Hello.js其文件就含有一段代码：

```
alert("Hello World!");
```

也就是文件里面不需要声明这是JavaScript代码，也不要什么开始标志，直接写就行，相当于它会把你写的代码自动镶嵌在标签里面。还有一个问题就是，那么我的script标签放在哪里呢？按照传统的做法，应该把所有的标签都放在`<head>`标签中，也就是Html的头部里面，如果这样做就意味着必须等到全部JavaScript代码都下载，解析，和执行后，才能看到页面（浏览器在遇到`<body>`标签才开始呈现类容）对于那种需要很多Js代码的页面来说，这会在呈现页面时出现延迟，这段期间界面将会是一片空白，现代Web应用程序一般都把JavaScript代码放在body标签的最后面如下：

```Html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>基本知识</title>  
	</head>	
	<body>
		<h2>标题</h2>
		<p>段落</p>
		<script src="Hello.js"></script>
	</body>
</html>
```
js代码位于最后面，这样做就可以先加载页面，后下载Js代码。

* 延迟脚本

script标签定义了defer属性，如果使用这个属性，就意味着，这个代码脚本会被延迟到整个页面都解析完毕后才运行，设置这个属性，就相当于告诉浏览器立即下载，但延迟执行。这个时候就可以把script标签放在head中而和上面例子一样的效果：


```Html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>基本知识</title>  
		<script src="Start.js" defer="defer"></script>
		<script src="End.js" defer="defer"></script>
	</head>	
	<body>
		<h2>标题</h2>
		<p>段落</p>
	</body>
</html>
```
注意脚本的解析也是按照顺序来的，比如上面两个Js外部文件，第一个会比第二个先执行，按照从上到下的原则，有时要注意调用信息。为什么？因为Js代码可以共用，举个例子来说，上面第一个Start.js代码中定义的变量可以在第二个End.js代码中使用，而第二个中定义并不一定能够在第一个中使用，当然可以使用全局变量，使整个Js代码文档都可以使用，但是局部变量就不一定行，有关这个部分后面再做介绍。

* 异步脚本

在script标签定义了async属性，与defer属性类似，async只适用外部脚本也就是引用外部js文档件，告诉浏览器立即下载文件，但是与defer不同的是，标记为async的脚本并不保证按照他们的顺序来执行。他们的执行顺序全部随机，这牵涉到异步编程，有关异步编程可以参考资料，异步编程是一种高级编程技术，许多语言都有这个方面的知识，Js也含有这个部分的内容但那属于后台内容，可以学习Node.js来学习这部分知识。现在只需要了解异步编程是一种同时调用，不占用一个程序通道的技术，举个例子来说，想想我们平时写的代码，它们都是从上到下执行，如果执行到一个比较费时间的操作
比如下载操作，假如下载需要1个小时，如下：


```C#
static void Main(string[] args)
{            
     Task t1 = new Task(Download,"Game");
     t1.Start(); //这步操作需要1个小时     
     
     Other();
     Console.WriteLine("等待时间我想做点其他的");
     Console.ReadKey();
}
```

当程序运行到t1.Start()时这个操作需要1个小时,那么这句代码下面的内容要等待这个操作完成才能够执行，想想是不是该这样，所以我们想在这个等待时间还能执行下面的代码，就需要使用异步编程，使用了异步编程你所有的任务都会是同时进行，一个操作延迟并不会影响到其他操作，这也就是为什么你能够在下载东西的同时还能够点开其他东西，这也是你为什么你能够在一个浏览器打开多个页面的原因。这些都使用了异步编程技术。










 
 
 
 
