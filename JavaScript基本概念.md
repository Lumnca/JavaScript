# ------------------基本概念--------------- #

<p id="title"></p>

## 目录 ##

:arrow_down:<a href="#a1">1.JavaScript语法</a>

:arrow_down:<a href="#a2">2.JavaScript变量</a>

:arrow_down:<a href="#a3">3.JavaScript数据类型</a>

:arrow_down:<a href="#a4">4.JavaScript操作符</a>

:arrow_down:<a href="#a5">5.JavaScript语句</a>

:arrow_down:<a href="#a6">6.JavaScript函数</a>

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

### :sweat_drops: 3.4Boolean类型 ###

该类型只有两个值 ： true和false，在Js中这两个值不与数字是一回事，因此true不一定等于1，而false也不一定等于0。如下为定义Boolean类型数据：

```JavaScript
var falg1 = true;
var falg2 = false;
```

注意字面true与false是区分大小写的，也就是说只能使用全小写的true与false，不能使用大写。Boolean型数据可以转换，将一个类型的值转换为Boolean需要使用函数Boolean()，如下所示：

```JavaScript
var  message = "Hello";

var falg1 = Boolean(message);

alert(falg1);
```

返回值为true，关于类型转换为Boolean，遵守如下规则：

|数据类型|转换为true|转换为false|
|:--:|:---:|:---:|
|Boolean|true|false|
|String|非空字符串|""(空字符串)|
|Number|任何非0数，包括无穷大|0和NaN|
|Object|任何对象|null|
|Undefined|无|Undefined|

### :sweat_drops: 3.4Number类型 ###

Number类型是数字的整合，包括整数与浮点型数据，也就是小数，不像其他语言还区分小数与整数。最基本的数值字面格式是十进制整数，如下;

```JavaScript
var  message = 52;
```

除了十进制以外，还可以使用8进制或者16进制，其中8进制第一位必须是零（0），十六进制开头必须为0x，如果格式不正确将不会转义为相对应的进制：

```avaScript
var  message = 010;
var message1 = 079;
var message2 = 0x1F;
```

**1.浮点类型**

所谓浮点型，就是该数值中必须含有一个小数点，并且小数点后面至少有一位数字。虽然小数点前面可以没有整数，但我们不推荐使用这种方法。看下面例子：

```JavaScript
var  message = 0.54;
var message2 = .754;
var message3 = 3.;
```

可以看到小数点前没数字如.75会被当做0.75，同理小数点后没有数字加0.对于那些非常大的小数可以采用科学计数法，ECMAScript也支持这种写法如1.25的负十次方可以表示为1.25e-10，0.49的十次方表示为：0.49e10 。如下，他们是等价的：

```JavaScript
var  message = 1.25e10;

if(message==12500000000){
    alert(message);
}
```

浮点数的精确位只有17位小数，但是在计算时误差远远不如整数，比如0.1+0.2的结果不是0.3而是0.30000000000000004，这个小小的误差会导致有些条件不能进行：

```JavaScript
if(0.1+0.2==0.3){
    alert("OK");
}
else{
    alert("No");
}
```

如上例子会执行else的语句，至于为什么，这是基于IEEE754数值的浮点计算的通病，并不只是JavaScript会这样，其他的语言也是一样的，所以千万不要进行0.1+0.2==0.3的条件测试。

**2.数值的范围**

由于内存限制，ECMAScript也只能存储限定的数值范围，这个范围是5e-324~1.7977e308如果某次计算超出了这个范围，则这个数值会被转换为特殊的Infinity值（正无穷），如果是负数则会转换为-Infinity（负无穷），如果某一次计算返回了Infinity值，那么该值不能在参与下一次计算，因为Infinity是不能参与计算的。


```JavaScript
var message = 7e307 + 8e308

alert(message);   //返回Infinity

alert(message-8e308);  /message已经为Infinity，不能计算，错误
```

**3.NaN**

NaN，即非负值（Not a Number）是一个特殊的数值，这个数值用于表示一个本来要返回数值的操作数未返回数值的情况（这样做是为了防止抛出错误），在其他语言中，会因为数值错误而导致编译失败，但在ECMAScript中，就不会影响到其他代码的执行

NaN本身具有两个特点：一是任何涉及NaN的计算（NaN+5，NaN/6等四则运算）都会返回NaN。二是NaN与任何数值都不相等，包括本身，如下：

```JavaScript
alert(NaN==NaN);  //返回false
```

针对NaN的特点，ECMAScript定义了isNaN()函数，这个函数接收一个参数，该参数可以是任何类型，这个函数可以来判断某些数值能不能够转换为数字类型。如果不能被转换为数值就会返回true，能够转换为数值就返回false。如下：

```JavaScript
alert(isNaN(NaN));            //true
alert(isNaN(10));             //false
alert(isNaN("10"));           //false,可以被转换为数值10
alert(isNaN("abc"));          //true，（不能被转换数值）
alert(isNaN(true));            //false，可以被转换为1
```

**4.数值转换**

有三个函数可以把非数值转换为数值：Number()，parseInt()和parseFloat()。

Number（）函数转换规则：

 * Boolean类型根据值转换为1和0

 * null 转化为0
 
 * 如果本身就是数值，那就没有变化
 
 * 如果是undefined，返回NaN。
 
 * 如果是字符串则分情况： 
 
      * 如果字符串内容全部为数值类型包括小数，就转换为相对应的数值。
      
      * 如果是八进制和十六进制的数值字符串，则就转换为对应的十进制数。
      
      * 空字符返回0
      
      * 以上不包括的返回NaN
      
 * 如果是对象，则需要调用对象方法valueOf()方法，根据上面的规则转换返回的值。
 
如下：

```JavaScript
var num1 = Number("abc");    //NaN
var num2 = Number("");       //0
var num3 = Number("00012");  //12
var num4 = Number(true);     //1
var num5 = Number("0x10");   //10
```

parseInt只能处理整数，并且多用于处理字符串，Boolean等类型将会被转换为NaN， parseInt()函数在转换时只看是否含有数值，它会忽略掉字符串前面的空格，直到找到第一个非空字符，如果第一个字符不是数值或者进制字符就会返回NaN。如下：

```JavaScript
var num1 = parseInt("123abc");      //123
var num2 = parseInt("");            //NaN
var num3 = parseInt("abc123");      //NaN
var num4 = parseInt(true);          //NaN
var num5 = parseInt("0x10");        //16
var num6 = parseInt("32.58");       //32
var num7 = parseInt(32.58);         //32
```

可以看出parseInt适用于字符串转整数，且小数也只能转换为整数。实际上parseInt还有一个作用就是进制转换，可以给方法提供第二个参数，来限定是多少进制的转换，如下：

```JavaScript
var num1 = parseInt("101",2);          //5
var num2 = parseInt("0x1A",16);        //26
```

当然对于16进制可以不加0x即`var num2 = parseInt("1A",16); `,注意的是一定是字符串格式，若上面不是字符串则不能转换。

parseFloat原理与parsInt一样，从第一位开始，一直到字符串末尾，或者遇到第一个无效的符号为止，而且小数点只有第一个有效，而且parsFloat不能转换进制数，所以也不能传递第二个参数。如下：

```JavaScript
var num1 = parseFloat("123abc");     //1234
var num2 = parseFloat("0xA");        //0
var num3 = parseFloat("1.25.74");    //1.25
var num4 = parseFloat("002.95");     //2.95
var num5 = parseFloat("3.125e4");    //31250
```

### :sweat_drops: 3.5tring类型 ###

String类型用于表示字符串，字符串可以用双引号和单引号表示，所以可以向下面这样使用：

```JavaScript
var s1 = "Hello World";
var s2 = 'Hello World';
```

在其他语言中单引号和双引号所表示的类容不同，单引号表示一个字符，双引号代表字符串。在ECMAScript中却没有什么区别。

**1.字符字面量**

String数据包含一些特殊的字符字面量，也叫转义序列。用于表示非打印字符，或者具有其他字符，如下所示：

|字面量|含义|
|:--:|:----:|
|\n|换行|
|\t|制表|
|\b|退格|
|\r|回车|
|\f|进纸（？）|
|`\\`|`不转义\`|
|\"|不转义"|
|\'|不转义'|

字符字面量可以出现在字符串很任何位置：

```JavaScript
var s1 = "Hello World\nHello Lmc";
alert(s1);
alert(s1.length);
```

任何字符串的长度都可以使用其length属性取得。如上等于21转义字符也算一位。

**2.字符串特点**

JavaScript字符串与C++有些共同之处，就是可以使用+（加号）拼接字符串。如下

```JavaScript
var s1 = "Hello"+" World";
s1 = s1 +"! \n";
alert(s1);
```

**3.转换为字符串**

转换字符串是常用的函数，他可以将值转换为英文字符串，像null,undefined，true等值都会被转换为对应的英文字符。使用toString()函数进行转换,对于没有定义或者其他值类型使用String()函数：

```JavaScript
var s1 = 10;
var s2 = false;
var s3 = undefined;
var s4 = null;
var s5 = NaN;
var s6 = Infinity;

alert(s1.toString());    //10
alert(s2.toString());    //false
alert(String(s3));       //undefined
alert(String(s4));       // null
alert(String(s5));       //NaN
alert(String(s6));       //Infinity
```

### :sweat_drops: 3.6Object类型 ###

Object类型也就是面向对象编程的类与对象，类含有各种函数与字段，可以模拟构建现实生活的抽象对象。这部分会在后面做详细介绍，这里不做说明。

<p id="a4"></p>

## :gem: JavaScript操作符 ## 

:arrow_double_up:<a href = "#title">返回目录</a>

ECMA-262描述了一组用于操作数据值的操作符，包含算数操作符，关系操作符，和相等操作符。下面一一介绍：

### :sweat_drops:一元操作符 ###

只能操作一个值的操作符叫做一元操作符。

   * 递增递减操作符 ++a,--a;.,a++,a--;

   * 加减操作符 +，-
   
### :sweat_drops:位操作符 ###

位操作符是对数据的求与，或，非等运算。这里不做解释，这是计算机基础知识。

   * 按位非 ： 由一个`~`表示。  如 `var  num = ~10; `
   
   * 按位与 ： 由一个`&`表示。 如 `var num = 25 & 3;`
   
   * 按位或 ： 由一个`|`表示。 如 `var num = 21 | 3;`
   
   * 按位异或 ： 由一个 `^`表示。如 `var num = 25 ^ 3;`
   
   * 左移 ： 用`<<`表示。 如 `var s1 = 10 << 1;`
   
   * 有符号右移 ： 用'>>'表示。 如 `var s1 = 10 >> 1;`
 
   * 无符号右移 ： 用'>>>'表示。 如 `var s1 = 10 >> 1;`


### :sweat_drops:布尔操作符 ###

与其他语言一致，布尔操作符有`! ,||,&&`分别为逻辑非，或，与。


### :sweat_drops:乘除法操作符 ###

对于乘除法只说一些注意事项

 * 乘法使用`*`
 
   * 乘积超过范围用Infinitiy或者-Infinitiy表示。
   
   * 如果有一个操作数为NaN，结果均为NaN。
   
   * 如果是Infinitiy与0相乘，结果为NaN。
   
   * Infinitiy与非0相乘，包括本身相乘，均为Infinitiy或者-Infinitiy
   
 * 除法使用`/`
 
   * 超出范围为Infinitiy或者-Infinitiy
   
   * 如果有一个操作数为NaN，结果均为NaN。
   
   * 如果是Infinitiy除以Infinitiy返回值为NaN。
   
   * 0/0也为NaN
   
   * Infinitiy除以非0数，也为Infinitiy

 * 求模`%`与除法类似

### :sweat_drops:关系法操作符 ###

关系操作符就是常见的：`<,>,==,>=,<=,!=,`值得注意的是等号：

|操作符|说明|
|:--:|:--:|
|=|赋值|
|==|相等，转换的情况下相等|
|===|全等于，在不转换的情况下相等|


```JavaScript
var a = 5;
var b = '5';
if(a==b){
    alert("Ok");
}
if(a===b){
    alert("OK!!!")
}
```

上面执行返回Ok，因为字符5能够转换为5，所以相等。所以判断两个值是否相同最好使用全等于。

### :sweat_drops:条件操作符 ###

类似于三目运算符,是if-else的简单表达式，格式：`a = 布尔表达式 ? 表达式为真的结果 : 表达式为假的结果`。如下

```JavaScript
var a = (2>7) ? "NO" : 'YES';     //NO
```

表达式为真就赋第一个值，为假就赋第二个值。

### :sweat_drops:赋值操作符 ###

简单的为=，还可以与四则运算符联用：`*=,+=,-=,/+,%=,<<=,>>=`,

### :sweat_drops:逗号操作符 ###

逗号语句可以在一条语句中执行多个操作：

```JavaScript
var a = 1,b = 2,c =3;
```

还可以用于单个变量多个值插入，但是只能插入最后一个值：

```JavaScript
var a =(2,5,6,7,8);   //a =8
```

<p id="a5"></p>

## :gem: JavaScript语句 ## 

:arrow_double_up:<a href = "#title">返回目录</a>

基础语法与C语言一致，如if-else，do-while，while，for语句，这里不做介绍。只说下for-in，这是一种精准迭代语句，可以用来枚举对象属性，也可以用来循环数组等：

```JavaScript
var a = ["abc",5,8.69,Infinity,undefined,null,NaN,'#'];

//item为迭代索引位使用in指向a数组。

for(item in a){
    alert(a[item]);  //a[item]显示数据
}
```

对于对象也是一样的迭代：

```JavaScript
var a ={
    "Name" : "Lumnca",
   "Age" : 21,
   "Sex" : "男",
    "From" : "DZ"
};

for(item in a){
    alert(a[item]);
}
```

break与continue语句常为循环中断语句，在这之中还有一个label标签语法，类似汇编的代码块，指定一个区域，不推荐使用：

```
state :
for(var i=0;i<=10;i++){
    if(i!=6){
        alert(i);
    }
   else{
       break state;
   }
}
```

上面为中断退出state域。

with语句，是将代码作用域延长，严格模式下不允许使用with语句：

```JavaScript
if(true){
    with(window){
        var a = 5;
    }
}
alert(a+5);
```

上面可以将作用域延长到Windows全局，但是不使用with也正确，但是最好不要使用这种操作。

<p id="a6"></p>

## :gem: JavaScript函数 ## 

:arrow_double_up:<a href = "#title">返回目录</a>

函数对于任何语言来说都是一个核心的概念，可以通过函数来封装任意多条语句，而且可以在任何地方，任何时候调用。ECMAScript中函数用function关键字来声明格式如下：

```JavaScript
function  函数名(参数) {
    函数执行语句
}
```

如下一个简单无参函数：

```JavaScript
function  sayHello() {
    alert("Hello");
}
sayHello();        //执行函数
```

带参函数：

```JavaScript
function  say(s){
    alert("你说："+s);
}
```
与其他语言不一样的是，Js的函数参数不需要指定类型，全部参数默认var型，所以你不必加上类型说明。同样的函数可以有返回值：

```JavaScript
function  add(num1,num2){
    return num1+num2;
}

alert(add(5,6));     //调用5+6 =11
alert(add("Hello","World"));   //字符串调用为HelloWorld
```

可以看到参数不同，得到的结果也不同，Js函数会自动根据参数类型来判断类型。

### :sweat_drops:理解参数 ###

在Js中参数不一定需要写出来，可以使用参数数组来获取参数：

如上函数可以修改为：

```JavaScript
function  add(){
    alert("参数的数量:"+arguments.length);
    return arguments[0]+arguments[1];
}

alert(add(5,6));
alert(add("Hello","World"));
```

如上所示可以使用arguments，arguments代表参数数组，他会根据参数个数来进行扩充数组。正是由于这一点，才导致Js的函数没有重载，我们知道重载是根据参数类型不同和参数个数不同来重载的，而在Js里这样是不行的。但是可以完成类似重载的操作：

```JavaScript
function  Func(){
        if(arguments.length==0){
            alert("没有参数");
        }
        else if(arguments.length==1){
            if(typeof(arguments[0])=="number")alert("数值参数");
            else{
                alert("不是数值参数");
            }
        }
        else{
            alert("参数个数大于2");
        }
}
Func();
Func(4);
Func("12");
Func(4,"sa");
```

如上根据参数的类型与个数来执行不同的操作。如果强行使用两个命名相同的函数，Js不会报错，会使用最后面那个覆盖前面的函数。




