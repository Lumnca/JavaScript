<h2>:large_blue_diamond: Canvas使用</h2>

要使用canvas>元素，必须先设置其width和height属性，指定可以绘图的区域大小。出现在开始和结束标签中的内容是后备信息，如果浏览器不支持<canvas>元素，就会显示这些信息。
下面就是<canvas>元素的例子。

```html
<canvas id="drawing"width="200height="200">A drawing of something.</canvas>
```

与其他元素一样，<canvas>元素对应的DOM元素对象也有width和height属性，可以随意修改。而且，也能通过CSS为该元素添加样式，如果不添加任何样式或者不绘制任何图形，在页面中是看不到该元素的。
要在这块画布（canvas）上绘图，需要取得绘图上下文。而取得绘图上下文对象的引用，需要调用getContext（）方法并传入上下文的名字。传入'2d'，就可以取得2D上下文对象。

```js
var drawing=document.getElementById("drawing");
```

在使用<canvas>元素之前，首先要检测 getcontext（）方法是否存在，这一步非常重要。有些浏览器会为HTML规范之外的元素创建默认的HTML元素对象。
在这种情况下，即使drawing变量中保存着一个有效的元素引用，也检测不到getcontext（）方法。

```js
    var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext('2d');
			console.log('context exist!');
		}
```

<h4>:small_blue_diamond: 2D上下文</h4>

使用2D绘图上下文提供的方法，可以绘制简单的2D图形，比如矩形、弧线和路径。2D上下文的坐标开始于<canvas>元素的左上角，原点坐标是（0，0）。
所有坐标值都基于这个原点计算，x值越大表示越靠右，y值越大表示越靠下。默认情况下，width和height表示水平和垂直两个方向上可用的像素数目。

**填充和描边**

2D上下文的两种基本绘图操作是填充和描边。填充，就是用指定的样式（颜色、渐变或图像）填充图形；描边，就是只在图形的边缘画线。大多数2D上下文操作都会细分为填充和描边两个操作，而
操作的结果取决于两个属性：fi11style和strokestyle。这两个属性的值可以是字符串、渐变对象或模式对象，而且它们的默认值都是“#000000”。
如果为它们指定表示颜色的字符串值，可以使用CSS中指定颜色值的任何格式，包括颜色名、十六进制码、rgb、rgba、hsl或hsla。如下：

```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.fillStyle = '#ff0000';  
			context.strokeStyle = 'red';   
		}
```

**绘制矩形**

矩形是唯一一种可以直接在2D上下文中绘制的形状。与矩形有关的方法包括fi11Rect（）、strokeRect（）和clearRect（）。
这三个方法都能接收4个参数：矩形的x坐标、矩形的y坐标、矩形宽度和矩形高度。这些参数的单位都是像素。
首先，fillRect（）方法在画布上绘制的矩形会填充指定的颜色。填充的颜色通过fillstyle属性指定，比如：


```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.fillStyle = '#ff0000';   //先声明填充颜色
			context.fillRect(0,0,200,200);   //再声明绘制矩形
		}
```

注意的是声明颜色和绘制必须按照顺序，否则不会出现对应颜色图像！可以在canvas中绘制多个图形：

```js
		if(drawing.getContext){
			var context = drawing.getContext("2d");
      //第一个图形
			context.fillStyle = '#ff0000';
			context.fillRect(0,0,100,100);
      //重新定义颜色，再绘制一个
			context.fillStyle = 'rgba(0,0,255,0.5)';
			context.fillRect(75,75,100,100);
		}
```

使用toDataURL()方法，可以导出在<canvas>元素上绘制的图像。这个方法接受一个参数，即图像的MIME类型格式，而且适合用于创建图像的任何上下文。
比如，要取得画布中的一幅PNG格式的图像，可以使用以下代码。

```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.fillStyle = '#ff0000';
			context.fillRect(0,0,100,100);

			context.fillStyle = 'rgba(0,0,255,0.5)';
			context.fillRect(75,75,100,100);
		}

		var imgUrl = drawing.toDataURL('image/png');  //获取图片png信息
		var img = document.createElement('img');
		img.src = imgUrl;
		document.body.appendChild(img);
```

同理对图像进行描边:

```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.strokeStyle = '#ff0000';
			context.strokeRect(0,0,100,100);

			context.strokeStyle = 'rgba(0,0,255,0.5)';
			context.strokeRect(75,75,100,100);
		}
```

最后，clearRect（）方法用于清除画布上的矩形区域。本质上，这个方法可以把绘制上下文中的某一矩形区域变透明。通过绘制形状然后再清除指定区域，
就可以生成有意思的效果，例如把两个图像重叠部分清空:

```js

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.fillStyle = '#ff0000';
			context.fillRect(0,0,100,100);

			context.fillStyle = 'rgba(0,0,255,0.5)';
			context.fillRect(75,75,100,100);

			context.clearRect(75,75,25,25);
		}

```

**绘制路径**

2D绘制上下文支持很多在画布上绘制路径的方法。通过路径可以创造出复杂的形状和线条。要绘制路径，首先必须调用beginPath（）方法，
表示要开始绘制新路径。然后，再通过调用下列方法来实际地绘制路径。

arc（x，y，radius，startAngle，endAngle，counterclockwise）：以（x，y）为圆心绘制一条弧线，弧线半径为radius，起始和结束角度（用弧度表示）分别为startAngle和endAngle。
最后一个参数表示 startAngle和endAng1e是否按逆时针方向计算，值为false表示按顺时针方向计算。

```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.beginPath();
			context.arc(100,100,98,0,Math.PI*2,false);
			context.stroke();	
		}
```
arcTo（x1，y1，x2，y2，radius）：从上一点开始绘制一条弧线，到（x2，y2）为止，并且以给定的半径radius穿过（x1，y1）。

```js
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.beginPath();
			context.arc(100,100,98,0,Math.PI,false);
			context.arcTo(50,50,100,100,50);
			context.stroke();	
		}
```


bezierCurveTo（c1x，cly，c2x，c2y，x，y）：从上一点开始绘制一条曲线，到（x，y）为止，并且以（c1x，c1y）和（c2x，c2y）为控制点。

```js
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.beginPath();
			context.arc(100,100,98,0,Math.PI,false);
			context.arcTo(50,50,100,100,50);
			context.bezierCurveTo(30,60,60,30,0,0);
			context.stroke();	
		}
```



lineTo（x，y）：从上一点开始绘制一条直线，到（x，y）为止。

moveTo（x，y）：将绘图游标移动到（x，y），不画线。

quadraticcurvero（cx，cy，x，y）：从上一点开始绘制一条二次曲线，到（x，y）为止，并且以（cx，cy）作为控制点。

rect（x，y，width，height）：从点（x，y）开始绘制一个矩形，宽度和高度分别由width和height 指定。这个方法绘制的是矩形路径，而不是strokeRect（）和fi1lRect（）所绘制的独立的形状。


创建了路径后，接下来有几种可能的选择。如果想绘制一条连接到路径起点的线条，可以调用closePath（）。如果路径已经完成，你想用fil1style填充它，可以调用fi11（）方法。
另外，还可以调用stroke（）方法对路径描边，描边使用的是strokestyle。最后还可以调用c1ip（），这个方法可以在路径上创建一个剪切区域。

```js
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.beginPath();
			context.arc(100,100,98,0,Math.PI,false);
			context.arcTo(50,50,100,100,50);
			context.bezierCurveTo(30,60,60,30,0,0);
			context.lineTo(200,100);
			//context.stroke();	  描边
			context.fill();   //填充
		}
```
在2D绘图上下文中，路径是一种主要的绘图方式，因为路径能为要绘制的图形提供更多控制。由于路径的使用很频繁，所以就有了一个名为isPointInPath（）的方法。
这个方法接收x和y坐标作为参数，用于在路径被关闭之前确定画布上的某一点是否位于路径上，例如：

```js
alert(context.isPointInPath(0,100));
```


描边线条的宽度由1ineWidth属性控制，该属性的值可以是任意整数。另外，通过linecap属性可以控制线条末端的形状是平头、圆头还是方头（"butt"、
"round"或'square‘），通过lineJoin属性可以控制线条相交的方式是固交、斜交还是斜接（“round"、“beve1“或“mitern）。

```js
		var drawing = document.getElementById('drawing');

		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.lineWidth = 5;
			context.lineCap = 'round';
			context.moveTo(0,0);
			context.lineTo(200,100);
			context.stroke();	
		}
```

**描绘文本**

文本与图形总是如影随形。为此，2D绘图上下文也提供了绘制文本的方法。绘制文本主要有两个方法：fi11Text（）和strokeText（）。
这两个方法都可以接收4个参数：要绘制的文本字符串、x坐标、y坐标和可选的最大像素宽度。而且，这两个方法都以下列3个属性为基础。

* font：表示文本样式、大小及字体，用CSS中指定字体的格式来指定，例如10pxArial"。
* textAlign：表示文本对齐方式。可能的值有“start"、"end"、"left"、"right“和“center"。
建议使用“start"和“end"，不要使用“1eft“和“right*，因为前两者的意思更稳妥，能同时适合从左到右和从右到左显示（阅读）的语言。
* textBaseline：表示文本的基线。可能的值有“top"、“hanging"、"middle"、"alphabetic"、"ideographic"和“bottom"。
这几个属性都有默认值，因此没有必要每次使用它们都重新设置一遍值。fi11Text（）方法使用fil1style属性绘制文本，而strokeText（）方法使用strokesty1e属性为文本描边。
相对来说，还是使用fillText（）的时候更多，因为该方法模仿了在网页中正常显示文本。例如，


```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.font="bold 14px Arial";
			context.textAlign="center";
			context.textBaseline="middle";
			context.fillText("Hello",60,100);
		}
```


**变换**

通过上下文的变换，可以把处理后的图像绘制到画布上。2D绘制上下文支持各种基本的绘制变换。创建绘制上下文时，会以默认值初始化变换矩阵，在默认的变换矩阵下，所有处理都按描述直接绘制。
为绘制上下文应用变换，会导致使用不同的变换矩阵应用处理，从而产生不同的结果。
可以通过如下方法来修改变换矩阵。

*rotate（angle）：围绕原点旋转图像angle弧度。

*scale（scalex，scaley）：缩放图像，在x方向乘以scalex，在y方向乘以scaleY。scalex和scaley的默认值都是1.0。

*translate（x，y）：将坐标原点移动到（x，y）。执行这个变换之后，坐标（0，0）会变成之前由（x，y）表示的点。

*transform（mi_1，ml_2，m2-1，m2-2，dx，ay）：直接修改变换矩阵，方式是乘以如下矩阵。

*setTransform（m1_1，ml_2，m2_1，m2_2，dx，dy）：将变换矩阵重置为默认状态，然后再调用transform（）。
变换有可能很简单，但也可能很复杂，这都要视情况而定。如下是倒置文字图像

```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.font="bold 14px Arial";
			context.textAlign="center";
			context.textBaseline="middle";
			context.translate(200,200);
			context.rotate(Math.PI);
			context.fillText("Hello",60,100);
		
		}
```

无论是刚才执行的变换，还是fi11style、strokestyle等属性，都会在当前上下文中一直有效，除非再对上下文进行什么修改。虽然没有什么办法把上下文中的一切都重置回默认值，
但有两个方法可以跟踪上下文的状态变化。如果你知道将来还要返回某组属性与变换的组合，可以调用 save（）方法。调用这个方法后，当时的所有设置都会进入一个栈结构，得以妥善保管。
然后可以对上下文进行其他修改。等想要回到之前保存的设置时，可以调用restore（）方法，在保存设置的栈结构中向前返回一级，恢复之前的状态。连续调用 save（）可以把更多设置保存到栈结构中，
之后再连续调用restore（）则可以一级一级返回。需要注意的是，save（）方法保存的只是对绘图上下文的设置和变换，不会保存绘图上下文的内容。

**绘制图像**

2D绘图上下文内置了对图像的支持。如果你想把一幅图像绘制到画布上，可以使用drawImage（）方法。根据期望的最终结果不同，调用这个方法时，可以使用三种不同的参数组合。
最简单的调用方式是传人个HTML<img>元素，以及绘制该图像的起点的x和y坐标。例如：


```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			var img = document.images[0];  //获取第一个img标签图片
			img.onload = function(){         //图片加载完毕启用
				context.drawImage(img,0,0);
			}
		}
```

如果你想改变绘制后图像的大小，可以再多传入两个参数，分别表示目标宽度和目标高度。通过这种方式来缩放图像并不影响上下文的变换矩阵。例如

```js
context.drawImage(img,0,0,40,40);
```


除了上述两种方式，还可以选择把图像中的某个区域绘制到上下文中。drawImage（）方法的这种调用方式总共需要传入9个参数：要绘制的图像、源图像的x坐标、源图像的y坐标、源图像的宽度、源图像的高度、目标图像的x坐标、目标图像的y坐标、目标图像的宽度、目标图像的高度。这样调用drawImage（）方法可以获得最多的控制。

除了给drawImage（）方法传入HTML<img>元素外，还可以传人另一个<canvas>元素作为其第一个参数。这样，就可以把另一个画布内容绘制到当前画布上。
结合使用drawImage（）和其他方法，可以对图像进行各种基本操作。而操作的结果可以通过toDataURL（）方法获得。不过，有一个例外，即图像不能来自其他域。如果图像来自其他域，调用toDataURL（）会抛出一个错误。打个比方，假如位于`www.example.com`上的页面绘制的图像来自于`www.wrox.com，`那当前上下文就会被认为“不干净”，因而会抛出错误。
	
**阴影余渐变**


2D上下文会根据以下几个属性的值，自动为形状或路径绘制出阴影。

* shadowcolor：用CSS颜色格式表示的阴影颜色，默认为黑色。
* shadowoffsetx：形状或路径x轴方向的阴影偏移量，默认为0。
* shadowoffsetY：形状或路径y轴方向的阴影偏移量，默认为0。
* shadowBlur：模糊的像素数，默认0，即不模糊。

这些属性都可以通过 context对象来修改。只要在绘制前为它们设置适当的值，就能自动产生阴影。例如：

```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			context.shadowOffsetX = 5;
			context.shadowOffsetY = 5;
			context.shadowBlur = 4;
			context.shadowColor = 'rgba(0,0,0,0.5)';
			context.fillStyle = '#0000ff';
			context.fillRect(0,0,100,55);
		}

```

渐变由CanvasGradient实例表示，很容易通过2D上下文来创建和修改。要创建一个新的线性渐变，可以调用createLineareradient（）方法。
这个方法接收4个参数：起点的x坐标、起点的y坐标、终点的x坐标、终点的y坐标。调用这个方法后，它就会创建一个指定大小的渐变，并返回CanvasGradient对象的实例。
创建了渐变对象后，下一步就是使用addcolorstop（）方法来指定色标。这个方法接收两个参数：色标位置和CSS颜色值。色标位置是一个0（开始的颜色）到1（结束的颜色）之间的数字。例如：


```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			var gradient = context.createLinearGradient(30,30,70,70); 
			gradient.addColorStop(0,"white"); 
			gradient.addColorStop(1,"black");

			context.fillStyle = gradient;
			context.fillRect(0,0,100,100);
		}
```


要创建径向渐变（或放射渐变），可以使用createRadialGradient（）方法。这个方法接收6个参数，对应着两个圆的圆心和半径。前三个参数指定的是起点圆的原心（x和y）及半径，后三个参数指定的是终点圆的原心（x和y）及半径。可以把径向渐变想象成一个长圆桶，而这6个参数定义的正是这个桶的两个圆形开口的位置。

如果把一个圆形开口定义得比另一个小一些，那这个圆桶就变成了圆锥体，而通过移动每个圆形开口的位置，就可达到像旋转这个圆锥体一样的效果。
如果想从某个形状的中心点开始创建一个向外扩散的径向渐变效果，就要将两个圆定义为同心圆。
比如，创建一个放射性的渐变圆，径向渐变的两个圆的圆心都应该在（100，100），因为矩形的区域是从（0，0）到（200，200）。请看代码：


```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");

			var gradient = context.createRadialGradient(100,100,0,100,100,100);

			gradient.addColorStop(0,"white"); 
			gradient.addColorStop(1,"yellow");

			context.fillStyle = gradient;
			context.arc(100,100,100,0,Math.PI*2);
			
			context.fill();
		}
```

**模式**

模式其实就是重复的图像，可以用来填充或描边图形。要创建一个新模式，可以调用createpattern（）方法并传人两个参数：一个HTML<img>元素和一个表示如何重复图像的字符串。
其中，第二个参数的值与CSS的background-repeat属性值相同，包括“repeat"、"repeat-x”、"repeat-y"和“no-repeat"。与css图像填充一样，看一个例子。


```js
		var drawing = document.getElementById('drawing');
		if(drawing.getContext){
			var context = drawing.getContext("2d");
			var image = document.images[0];
			image.onload = function(){
				var pattern = context.createPattern(image,"repeat");
				//绘制矩形
				context.fillStyle = pattern;
				context.fillRect(0,0,1000,1000);
			}
		}
```

**使用图像数据**

2D上下文的一个明显的长处就是，可以通过getImageData（）取得原始图像数据。这个方法接收4个参数：要取得其数据的画面区域的x和y坐标以及该区域的像素宽度和高度。例如，要取得左上角坐标为（10，5）、大小为50×50像素的区域的图像数据，可以使用以下代码：

```js
var imageData=context.getImageData（10，5，50，50）；
```

这里返回的对象是ImageData的实例。每个ImageData对象都有三个属性；width、height和data。其中data属性是一个数组，保存着图像中每一个像素的数据。在data数组中，每一个像素用


4个元素来保存，分别表示红、绿、蓝和透明度值。
因此，第一个像素的数据就保存在数组的第0到第3个元素中，例如：


```js
var data = imageData.data，
red=data[0]，
green=data[1]，
blue=data[2]，
alpha =data[3]；
```


这个数据是一个一个像素点构成的，如一个`100px*100px`的图片就会有`100*100*4`个数据。



