# ------------------基本概念--------------- #

<p id="title"></p>

## 目录 ##

:arrow_down:<a href="#a1">1.JavaScript语法</a>

:arrow_down:<a href="#a2">2.JavaScript变量</a>

:arrow_down:<a href="#a3">3.JavaScript数据类型</a>

:arrow_down:<a href="#a4">4.JavaScript引用 </a>

<p id="a1"></p>

## :gem: JavaScript语法 ## 

:arrow_double_up:<a href = "#title">返回目录</a>

ECMAScript 的语法大量借鉴了C及其他类C语言的语法，因此熟悉这些语言在学ECMAScript会更加容易与轻松。


### :sweat_drops: 1.1区分大小写 ###

要理解的第一个概念就是ECMAScript中的一切（变量，函数名，和操作符）都区分大小写，这也就意为着，变量名test和Test分别代表两个不同的变量，函数名也是一样的道理。

### :sweat_drops: 1.2标识符 ###

所谓的标识符就是指变量，函数，属性的名字，或者函数的参数命名，标识符可以是按照下列规则组合起来的一或多个字符：

  * 第一个字符必须是一个字母，下划线（_）或者一个美元符号（$）；
  
  * 其他字符可以是字母，下划线，美元符号或者数字。
  
按照惯例，Js语法的标识符采用驼峰大小写格式，也就是第一个字母小写，剩下的单词首字母大写，例如：myJavaScript，firstName。

### :sweat_drops: 1.3注释 ###

ECMAScript使用C风格的注释，包括单行注释和块级注释，单行注释以两个斜杠开头，如下所示： 

```
// int a = 12;
// a = a + 6;
```

块级注释以`（/*）`开头，以`（*/）`结尾，如下：

```
/* int a = 12;
  * a = a + 6;
  * a = a - 7;
  console.log(a);*/
```

虽然上面注释中间的每行前面都有个 `*`但是这是可以省略的，之所以这样添加，纯粹是为了提高注释的可读性，企业级应用中用的比较多。

### :sweat_drops: 1.4 严格模式 ###

严格模式是为JavaScript定义了一种不同的解析与执行模型，在严格模式下，有些行为会得到不同的处理，也就是区别于其他模式，他会做出不同的特殊处理。启用严格模式可以在Js代码顶部添加以下代码：

```Javascript
"use strict"
```
这只是一段字符串，但他是一个编译指示，用于告诉支持的JavaScript引擎切换到严格模式。关于严格模式后面会作出解释。

### :sweat_drops: 1.5 语句 ###

ECMAScript中语句以一个分号结尾；如果省略分号，则由解析器确定语句结尾，如下例所示：

```JavaScript
var sum = 3 + 6       //没有分号也是可以执行语句，不推荐这样使用
var num = 6 -4;       //推荐这样做，每一行用分号结束
```

### :sweat_drops: 1.6 关键字与保留字 ###

每一门语言都有关键字，关键字是不能用来做标识符的，这些关键字用于代码编制的重要一点，有关关键字可以自行查看，还有一类是保留字，尽管保留字还没有规定特定的用处，但他们有可能在将来作为关键字，同样的不能作为标识符。

<p id="a2"></p>

## :gem: JavaScript变量 ##

:arrow_double_up:<a href = "#title">返回目录</a>

ECMAScript变量是松散类型的，所谓松散类型就是可以支持任何变量，不像C语言，整型数据只能使用int，字符只能使用char，在Js中我们基本上使用var来定义任何变量。如：

```JavaScript
var message;
```

这行代码只是定义了个变量，如果想要赋值，只需要在变量后赋值就行，或者在声明变量时即可初始化变量：

```JavaScript
var message1 = 5 ;              //数字5
var message2 = '5' ;            //字符5
var message3 = "5";             //字符串5
```

上面三种定义方式并没有限定变量只能是什么类型，如上 message 一开始为整型数字5，但是我们可以改变它的类型即给一个新的类型如下：

```
var message1 = 5;
message1 = "Hello";   //不建议这样做
```

如上面操作是完全可行的，但是我们不推荐这样做。对于变量都有它的作用域，即这个变量能够存在的区域，有关作用域，后面再做介绍。可以使用一个var语句定义多个变量，使用逗号隔开，如下：

```JavaScript
var message1 = 5,       
message2 = '5' ,         
message3 = "5";
```

<p id="a3"></p>

## :gem: JavaScript数据类型 ##

:arrow_double_up:<a href = "#title">返回目录</a>

ECMAScript中有5种简单数据类型（也称为基本数据类型）：Undefined（无定义），Null(空)，Boolean（布尔），Number（数字），和String（字符串）。还有一种复杂的数据类型----Object，Object本质是由一组无序的名值对组成的。

### :sweat_drops: 3 .1 typeof操作符 ###

鉴于ECMAScript类型是松散的，所以需要一种手段来检测数据类型。typeof就是负责提供这个方面的信息的。typeof会返回以下字符串某个：

|返回值|说明|
|:---:|:----:|
|undefined|这个值未定义|
|boolean|这个值是布尔值|
|string|这个值是字符串|
|number|这个值是数字|
|object|这个值是对象或者null|
|function|这个值是函数|

如下例子：

```JavaScript
var message = 5;
alert(typeof(message));
alert(typeof message);
alert(typeof "Hello");
```

typeof可以使用两种形式来，第一种是像上面第一种那样，`typeof(变量)` 或者直接` typeof 变量`这种形式，alert()是弹出一个警告话框，我们后面使用这个方法来查看数据。

### :sweat_drops: 3.2Undefined类型 ###

Undefined类型只有一个值，即特殊的undefined值，在使用var声明变量但未对其加以初始化时，这个变量的值就是undefined，就是这个变量并没有存在或者没有初始化，就会显示这个值。如下：

```JavaScript
var message = 5;
var message3;
alert(typeof(message));
alert(typeof(message2));
alert(typeof message3);
```

message2这个变量并没有存在，所以返回undefined，message3这个变量并没有初始化，所以也返回undefined，注意这个undefined不是一个字符串也不是一个变量，它是一个代表值与true和false一样，是一个具有代表的值，我们可以像下面这样使用这个值：

```JavaScript
var message2;

if(message2 == undefined)
{
    alert("这个值没有定义或者初始化,其值为："+message2);
}
else{
    alert("这个值已经定义了，他的值为："+message2);
}
```

像上面这样就可以分辨某个值是否是undefined类型的。

### :sweat_drops: 3.3Null类型 ###

Null类型与undefined类型一样只有一个值，这个值为null，从逻辑角度来说，null值表示一个空对象指针，这也是使用typeof会返回object的原因。

```
var message2 = null;
alert(message2);
```

如上信息会返回object的值，如果储存的变量将来用于保存对象，那么最好将该变量初始化为null而不是其他值。只要使用这个变量与null比较就可以知道，这个变量是否引用了其他对象，实际上undefined派生于null，也就是说它们是相等的。即 `undefined == null`由于还没讲解对象与引用，所以null的真正用处还不能够具体说明，等后面介绍了对象，再来说明Null。

### :sweat_drops: 3.4 ###







