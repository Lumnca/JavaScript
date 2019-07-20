# Dom操作技术

<b id="t"></b>

:one:[动态脚本](#a1)

:two:[动态样式](#a2)

:three:[动态节点](#a3)

<b id="a1"></b>

### :moneybag:动态脚本 ###

:arrow_double_up:[返回目录](#t)

我们可以使用Js向html输入脚本，也可以使用JS创建Js脚本，这就是动态脚本，如下是利用Js动态生成crs.js脚本：

```JavaScript
var dom1 = document.createElement("script");

dom1.type = "text/javascript";

dom1.src = "crs.js";

document.body.appendChild(dom1);
```

然后在Html界面中正确放置脚本标签的位置，如果Js标签在头部中，就会失败，因为在这里执行的js代码最先执行，读取不到后面的body属性。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	</body>
	<script src="Hello.js"></script>
</html>
```

当然生成多个脚本节点时，可以使用函数进行封装。使用也比较方便。

<b id="a2"></b>

### :moneybag:动态样式 ###

:arrow_double_up:[返回目录](#t)

同样的例子，可以利用link标签来生成css样式表，如下：

```JavaScript
var dom1 = document.createElement("link");

dom1.rel = "stylesheet";
dom1.type = "text/css";
dom1.href = "output.css";

document.getElementsByTagName("head")[0].append(dom1);
```

:three:[动态节点](#a3)

<b id="a3"></b>

### :moneybag:动态节点 ###

:arrow_double_up:[返回目录](#t)

当然在DOM技术中用的最多应该是节点生成，为了前后端分离中根据后端的返回数据来生成相应的节点数目。首先先看一下单一节点的生成：

```JavaScript
var dom1 = document.createElement("div");
dom1.style = "width:200px;height:100px;border: 1px solid red;";
dom1.textContent = "Hello";
document.body.append(dom1);
```

这样就生成了一个具有style样式的div标签，如果想在div中继续生成标签，可以继续添加：

```JavaScript
var dom1 = document.createElement("div");
dom1.style = "width:200px;height:100px;border: 1px solid red;";
dom1.textContent = "Hello";
document.body.append(dom1);

var dom2 = document.createElement("h2");
dom2.textContent = "Lumnca";
dom1.appendChild(dom2);
```

当然是用最多的还是表格生成，根据后台数据来生成表格数据是常用的技术，如下我们要把接受的数据动态生成到表格中

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<table border="1">
			<thead>
				<tr>
					<td>姓名</td>
					<td>性别</td>
					<td>年龄</td>
				</tr>
			</thead>
			<tbody>
				
			</tbody>
		</table>
	</body>
	<script src="Hello.js"></script>
</html>
```

下面直接利用Json字符串来代表后台数据输入，生成表格数据：

```JavaScript
var tbody = document.getElementsByTagName("tbody")[0];

var personData = [
    {
        name : 'Lumnca',
        sex : '男',
        age : 21
    },
    {
        name : 'Kay',
        sex : '男',
        age : 21
    },
    {
        name : 'Marry',
        sex : '女',
        age : 19
    }
]


for(let i=0;i<personData.length;i++)
{
    createRow(personData[i]);
}

function createRow(data){
    var tr = document.createElement("tr");
    var td1 = document.createElement("td");
    var td2 = document.createElement("td");
    var td3 = document.createElement("td");

    td1.textContent = data.name;
    td2.textContent = data.sex;
    td3.textContent = data.age;
    tr.appendChild(td1);
    tr.appendChild(td2);
    tr.appendChild(td3);
    tbody.appendChild(tr);
}
```

点击运行即可看到动态生成表格：

![](https://github.com/Lumnca/JavaScript/blob/master/Images/a8.png)













