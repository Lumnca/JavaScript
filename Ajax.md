## :cyclone:Ajax ##

<p id="title"></p>

### 目录点击链接 ###
:point_right:<a href="#one" >Ajax简介<a><br>
:point_right:<a href="#two" >XHR对象<a><br>
:point_right:<a href="#three" >使用Ajax提取文本文件<a><br>
:point_right:<a href="#four" >使用Ajax读取XML信息<a><br>
:point_right:<a href="#five" >使用Ajax获取JSON<a><br>

<p id = "one"></p>

### ---------------------------------------------------Ajax简介--------------------------------------------- ###

<a href="#title">:arrow_up:返回目录</a>
* AJAX 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。
* AJAX = 异步 JavaScript 和 XML。
* AJAX 是一种用于创建快速动态网页的技术。
* 通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。
* 传统的网页（不使用 AJAX）如果需要更新内容，必需重载整个网页面。
* 有很多使用 AJAX 的应用程序案例：新浪微博、Google 地图、开心网等等。

Ajax技术核心是XMLHttpRequest对象简称XHR，XHR向服务器发送请求和解析服务器响应提供了流畅的接口，能够以异步方式从
服务器取得更多信息，以为着用户单击后，可以不必刷新页面也能取得数据，也就是说可以使用XHR对象取得数据，然后通过DOM讲数据插入到
页面中，另外，虽然名字中包含XML的成分，但Ajax通信与数据格式无关；这种技术就是无须刷新页面即可从服务器取得数据，但不一定是XML数据。

#### :arrow_double_down:下图为Ajax工作模式 ####

![999](http://www.runoob.com/images/ajax.gif)

<p id = "two"></p>

### ----------------------------------------------------XHR对象---------------------------------------------- ###

<a href="#title">:arrow_up:返回目录</a>
#### XMLHttpRequest 对象 ####
所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。
XMLHttpRequest 用于在后台与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。
#### 创建 XMLHttpRequest 对象 ####
所有现代浏览器（IE7+、Firefox、Chrome、Safari 以及 Opera）均内建 XMLHttpRequest 对象。创建 XMLHttpRequest 对象的语法：

```JavaScript
    variable=new XMLHttpRequest();
```
老版本的 Internet Explorer （IE5 和 IE6）使用 ActiveX 对象：

```JavaScript
    variable=new ActiveXObject("Microsoft.XMLHTTP");
```
为了应对所有的现代浏览器，包括 IE5 和 IE6，请检查浏览器是否支持 XMLHttpRequest 对象。如果支持，则创建 XMLHttpRequest 对象。如果不支持，则创建 ActiveXObject ：
```JavaScript
        var xmlhttp;
        if (window.XMLHttpRequest)
        {
            //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
            xmlhttp=new XMLHttpRequest();
        }
        else
        {
            // IE6, IE5 浏览器执行代码
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
```
#### AJAX - 向服务器发送请求请求 ####
XMLHttpRequest 对象用于和服务器交换数据。
如需将请求发送到服务器，在对象创建好了的情况下，我们使用 XMLHttpRequest 对象的 open() 和 send() 方法：

```JavaScript
    xmlhttp.open("GET","ajax_info.txt",true);
    xmlhttp.send();
```

|方法|参数说明|
|:---:|:----|
|open(method,url,async)|规定请求的类型、URL 以及是否异步处理请求。method：请求的类型；GET 或 POST； url：文件在服务器上的位置；  async：true（异步）或 false（同步）|
|send(string)|将请求发送到服务器。string：仅用于 POST 请求|

对于请求一般是get方法，并且对于是否异步调用，我们一般是true，这样使得浏览器线程不会拥塞。send方法接受一个参数，即要作为请求主体发送数据。如果不需要通过主体发送数据，则必须传入null，因为这个参数对浏览器来说是必须的。

XHR相关属性如下：
* responseText：作为响应主体被返回的文本。
* responseXML： 如果响应的类容类型是“text/xml”或者是“application/xml”这个属性中将保存着响应数据的XML DOM文档
* status:响应的Http状态，返回状态码（404）
* statusText:Http状态的文本说明
* readyState:该属性表示请求过程的当前活动阶段，这个值取值如下

|值|说明|
|:--:|:---:|
|0|未初始化，尚未调用open()方法|
|1|启动，已经调用open()方法，但尚未调用send()方法|
|2|发送，已经调用send()方法，但尚未接受到响应|
|3|接受，已经接受到部分响应数据|
|4|完成，已经完成前部响应数据，而且可以在客户端使用了|

我们可以使用readyState对请求状态进行不同的操作，只要readyState值由一个值变到另一个值。都会触发一次readystatechange事件，可以利用这个事件来检测每次
状态变化后readyState的值

```JavaScript
	var xhr = new XMLHttpRequest();
	xhr.onreadystatechange = function(){
		alert("数值变化了");
	}
	xhr.open("GET","file.txt",false);
    xhr.send(null);
 ```
 
<p id = "three"></p>

### ----------------------------------------------使用Ajax提取文件------------------------------------------ ###

可以使用ajax获取文本文件内容，并且不需要刷新网页内容，如下（使用IDEA下的web工程）首先在与网页同一目录下创建一个demo.txt文件并添加内容，创建好之后如下：

![](https://github.com/Lumnca/JavaScript/blob/master/Images/a3.png)

与用什么编译软件和语言没有关系，ajax属于JavaScript，凡是可以使用js就可以使用Ajax。如上我们的页面时logn.html，文本文件是demo，所以接下里我们使用Ajax来获取文本内容。

首先看下我们的文本内容：

![](https://github.com/Lumnca/JavaScript/blob/master/Images/a4.png)

然后在我们的html文档为以下内容：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>菜鸟教程(runoob.com)</title>
</head>
<body>
<p id="te">demo文件内容：</p>
<script>
     var xmlHttp = new XMLHttpRequest();
     xmlHttp.open("GET","demo.txt",false);
     xmlHttp.send(null);
     document.getElementById("te").innerHTML = xmlHttp.responseText;
</script>
</body>
</html>
```

可以看到我们的Ajax使用在script标签中，当然你也可以写在其他Js文件中，只需要引用即可：

```javaScript
     var xmlHttp = new XMLHttpRequest();        //创建XMLHttpRequest实例
     xmlHttp.open("GET","demo.txt",false);      //打开请求
     xmlHttp.send(null);                        //发送
     document.getElementById("te").innerHTML = xmlHttp.responseText;   //获取请求并输出在Html中的p标签中  
```

然后运行html文件我们可以看以下内容：

![](https://github.com/Lumnca/JavaScript/blob/master/Images/a5.png)


但是我们所取出来的文本都一个字符串，也就是说我们原先的文本内容是换行的，但是拿出来却不是换行的，如果我想保留格式，那该怎么做呢？，可以采用JavaScript对文本处理。你会发现我们输出的文本段之间有一个空格，这个空格就是读取到文本文件换行时的相应，我们知道在Html中空格只能保留一个，所以换行在Html文档中被理解成了一个空格。我们可以根据这个进行修改：

```JavaScript
     var xmlHttp = new XMLHttpRequest();
     xmlHttp.open("GET","demo.txt",false);
     xmlHttp.send(null);
     var text =  xmlHttp.responseText;
     for(item in text){
         if(text[item]==="\n"){
             document.getElementById("te").innerHTML +="<br>"+ text[item];
         }
         else{
             document.getElementById("te").innerHTML += text[item];
         }
     }
```

我们可以将换行字符处进入一个换行标签`<br>`，即可完成我们的要求。


<p id = "four"></p>

### ---------------------------------------------------使用Ajax读取XML文件信息--------------------------------------------- ###

与上面的文本文件操作类似，只是调用方法与文本文件有些差异，文本文件取出来是一个完整的字符串或者文本文段，也就是如果我只想获取某部分内容，就显得不方便，比如我在文本文件上创建了一个书籍目录,如果是作为文本文件取出来，那么它将会是几段文字，并不能区分他们一一对应的关系，所以我们这种情况下就需要使用XML。

首先是声明一个XML文档：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<note>
    <bookname>
        <book>红楼梦</book>
        <book>西游记</book>
        <book>三国演义</book>
        <book>水浒传</book>
    </bookname>
    <bookAuthor>
        <name>曹雪芹</name>
        <name>吴承恩</name>
        <name>罗贯中</name>
        <name>施耐庵</name>
    </bookAuthor>
</note>

```

然后在网页使用JavaScript来提取XML数据并在表格中表示

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>菜鸟教程(runoob.com)</title>
</head>
<body>
<table border="1">
    <tr>
        <td>书籍名</td>
        <td>作者</td>
    </tr>
    <tr>
        <th></th>
        <th></th>
    </tr>
    <tr>
        <th></th>
        <th></th>
    </tr>
    <tr>
        <th></th>
        <th></th>
    </tr>
    <tr>
        <th></th>
        <th></th>
    </tr>
</table>
<script>
     var xmlHttp = new XMLHttpRequest();
     xmlHttp.open("GET","scratch.xml",false);
     xmlHttp.send(null);
     var xml = xmlHttp.responseXML;
     var nIndex  = 0;
     var bIndex = 0;
     for (var i=0;i < 8;i++ ) {

         if(i%2==0){
             var book =  xml.getElementsByTagName("book")[bIndex ].childNodes[0].nodeValue;
             document.getElementsByTagName("th")[i].innerHTML = book;
             bIndex+=1;
         }
        else{
             var name =  xml.getElementsByTagName("name")[nIndex].childNodes[0].nodeValue;
             document.getElementsByTagName("th")[i].innerHTML = name;

             nIndex+=1;
         }
     }
</script>
</body>
</html>
```

我们这里主要看提取代码：

```javaScript
     var xmlHttp = new XMLHttpRequest();
     xmlHttp.open("GET","scratch.xml",false);
     xmlHttp.send(null);
     var xml = xmlHttp.responseXML;
```

其中responseXML是提取XML文件并保存为XML DOM格式，xml也就是这个XML DOM的实体，使用所以在后续的操作中，我们使用了JS DOM的方法来获取xml标签并引用取出所对应的值。这个原理和Html一样。

<p id = "five"></p>

### -------------------------------------------------AJAX获取JSON--------------------------------------------- ###










