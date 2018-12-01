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
