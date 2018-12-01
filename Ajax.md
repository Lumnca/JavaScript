## :cyclone:Ajax ##

<p id="title"></p>

### 目录点击链接 ###
:point_right:<a href="#one" >Ajax简介<a><br>
:point_right:<a href="#two" >XHR对象<a><br>
:point_right:<a href="#three" ><a><br>
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
 
