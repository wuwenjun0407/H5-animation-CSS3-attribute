# 画布canvas

@(H5移动端动画)



>作用：H5新标签，在页面上绘制图形用的（通常称它画布）

>canvas 只是一个容器，我们用JS脚本来控制他

## 步骤
>1.获取出canvas标签
```
var draw=document.getElementById("draw");
```
>2.设置绘制环境(目前都是在2d环境下)
>cvs 这个就是画板，操作是在这上面操作的，进行绘制
```
var cvs=draw.getContext("2d")
```
### 绘制的具体属性
>样式 颜色 边框的宽度
-  填充的样式 cvs.fillStyle
-  笔触颜色（边框的颜色）cvs.strokeStyle
-  边框的宽度 cvs.lineWidth

>绘制的两种方式
-  填充 cvs.fill()
-  边框 cvs.stroke()

>颜色值
-  颜色名字：”red“
-  十六进制：#ff6700
-  三色值：rgb(123,234,120)
-  四色值：rgba(123,234,120,.3)

>坐标：是以画布为基准，距离画布的左边是X的坐标值，上边是Y的坐标值
-  起始点的坐标 cvs.moveTo(x,y)
-  如果没有moveTo就把上一个挨着的lineTo作为起始坐标
-  结束点坐标 cvs.lineTo(x,y)
-  假如第一个不是moveTo而是lineTo，那么lineTo就是起始坐标

>路径(自动闭合，从结束坐标值，到起始坐标自动连接)
-  开始一个新的路径 cvs.beginPath()
-  关闭当前路径  cvs.closePath()

>设置线条交汇处的样式lineJoin，他有三个属性（尖角miter，斜角bevel，圆角round）

>设置一条线段。两端点的样式
>cvs.lineCap 三个属性 butt（默认 平角） round（圆角） square（方角）
>cvs.closePath();	加上这句话没有端点的效果

#### 实例

>1.以边框的形式显示出来
```
function draw1(){
	var draw=document.getElementById("draw");
	var cvs=draw.getContext("2d");
	cvs.beginPath();
	cvs.moveTo(50,50);
	cvs.lineTo(150,50);
	cvs.closePath();
	cvs.strokeStyle="#800080";
	cvs.lineWidth=20;
	cvs.stroke();//以边框的形式显示出来
}
```
![Alt text](./QQ截图20170608184536.png)

>2.绘制三角形
```
function draw2(){
	var draw=document.getElementById("draw");
	var cvs=draw.getContext("2d");
	cvs.beginPath();
	cvs.lineTo(80,120);
	cvs.lineTo(80,240);
	cvs.lineTo(200,240);
	cvs.closePath();
	cvs.strokeStyle="#02646E";
	cvs.lineWidth=10;
	cvs.stroke();
}
```
![Alt text](./QQ截图20170608184649.png)

>3.绘制三角形 交汇的点是斜角
```
function draw3(){
	var draw=document.getElementById("draw");
	var cvs=draw.getContext("2d");
	cvs.beginPath();
	cvs.lineTo(200,100);
	cvs.lineTo(100,250);
	cvs.lineTo(300,250);
	cvs.closePath();
	cvs.strokeStyle="blue";
	cvs.lineWidth=10;
	cvs.lineJoin="bevel";
	cvs.stroke();
};
```
![Alt text](./QQ截图20170608184741.png)	




### 绘制矩形
>**注意：** 边框的一半在里面，一半在外面

>1.填充的矩形 cvs.fillRect(x,y,w,h)
-  x,y 这个矩形左上角的坐标
-  w,h 这个矩形的宽 高

>2.带边框的矩形 cvs.strokeRect(x,y,w,h)
-  x,y 这个矩形左上角的坐标
-  w,h 这个矩形的宽 高

>3.清除矩形  cvs.clearRect(x,y,w,h)
-  x,y 这个矩形左上角的坐标
-  w,h 这个矩形的宽 高
-  清除某部分，清除的还是矩形


#### 实例
>1.边框矩形和填充矩形
```
function draw1(){
	//填充
	cvs.fillStyle="red";
	cvs.fillRect(10,20,100,50);
	//边框
	cvs.strokeStyle="blue";
	cvs.lineWidth=30;
	cvs.strokeRect(150,15,100,50)
	
}
```
![Alt text](./QQ截图20170608185633.png)

>2.清除某部分，清除的还是矩形
```
function draw2(){
	cvs.fillStyle="red";
	cvs.fillRect(20,100,300,100);
	//清除某部分，清除的还是矩形
    cvs.clearRect(150,130,40,40)
}
```
![Alt text](./QQ截图20170608185856.png)

### 绘制圆形
>cvs.arc(x,y,r,star,end,n) 都是以弧度计算
- x,y 圆心的坐标 
- r 半径
- star 起始角，以弧度计算（三点钟的方向是0度）
- end  结束角 2*Math.PI(360度)  Math.PI(180度) Math.PI/2(90度)  Math.PI/4(45度)
- n  是否逆时针 true/false默认值是（false 顺时针）

#### 实例

>1.  45度绘制
```
function draw1(){
		cvs.strokeStyle="#0000FF";
		cvs.beginPath();
		cvs.arc(150,150,100,0,Math.PI/2,false);
		cvs.closePath();
		cvs.stroke();
	}
	draw1();
```			
![Alt text](./QQ截图20170608190336.png)

>2. 填充和边框混合绘制圆形
```
function draw2(){
    	cvs.fillStyle="red";
    	cvs.beginPath();
    	cvs.arc(200,200,40,0,2*Math.PI,false);
    	cvs.closePath();
    	cvs.fill();
    	cvs.strokeStyle="yellow";
    	cvs.lineWidth=40;
    	cvs.beginPath();
    	cvs.arc(200,200,60,0,2*Math.PI,false);
    	cvs.closePath();
    	cvs.stroke()
    }
```
![Alt text](./QQ截图20170608190701.png)

>3.连续写两个弧度，中间没有关闭路径产生的闭合
```
function draw3(){
	cvs.beginPath();
	cvs.strokeStyle="greenyellow";
	cvs.lineWidth=2;
	cvs.arc(100,100,100,0,Math.PI/2,false);
	cvs.stroke();
	
	cvs.fillStyle="#0000FF";
	cvs.arc(300,300,80,0,Math.PI/2,false);
	cvs.closePath();
	cvs.fill();
	//每次调用fill的时候，会把当次路径的起始点和结束点分别连接，填充闭合部分
	//所以说以后在写每次路径的时候，记得关闭当前路径
}
```
![Alt text](./QQ截图20170608190943.png)

### 线性渐变
>var CLG=cvs.createLinearGradient(x0,y0,x1,y1)
>CLg.addColorStop(n,m)
-  x0 渐变开始的X坐标
-  y0 渐变开始的Y坐标
-  x1 渐变结束的X坐标
-  y1 渐变结束的Y坐标
-   n   设置颜色的偏移量
-  m  颜色

####实例
```
function draw1(){
    	var CLG=cvs.createLinearGradient(0,0,200,200);
    	CLG.addColorStop(0,"red");
    	CLG.addColorStop(0.25,"yellow");
    	CLG.addColorStop(0.5,"blue");
    	CLG.addColorStop(0.75,"#ccc");
    	CLG.addColorStop(1,"red");   	
    	cvs.fillStyle=CLG;
    	cvs.fillRect(0,0,200,200);
    	
    }
```
![Alt text](./QQ截图20170608191410.png)

### 径向渐变 发散型渐变

>cvs.createRadialGradient(x0,y0,r0,x1,y1,r1)
>CLg.addColorStop(n,m)
-  x0 发散渐变开始中心的X坐标
-  y0 发散渐变开始中心的Y坐标
-  r0 发散渐变开始的半径
-  x1 发散渐变结束中心的X坐标
-   y1 发散渐变结束中心的Y坐标
-   r1  发散渐变结束的半径
-  n  设置颜色的偏移量
-  m  颜色

#### 实例
>如果是矩形径向渐变，会把没有的地方自动填充颜色（就近的）
```
 function draw2(){
    	var CRG=cvs.createRadialGradient(200,200,100,200,200,10);
    	CRG.addColorStop(0,"#000");
    	CRG.addColorStop(0.5,"yellow");
    	CRG.addColorStop(1,"blue")
    	cvs.fillStyle=CRG;
    	cvs.fillRect(100,100,200,200);
    }
```
![Alt text](./QQ截图20170608192041.png)
 
### 阴影(可以给盒子添加也可以给文本添加)
>cvs.shadowOffsetX 表示阴影的横向偏移量 默认值是0
>cvs.shadowOffsetY 表示阴影的纵向偏移量 默认值是0
>cvs.shadowColor  表示阴影的颜色
>cvs.shadowBlur  表示阴影的范围

#### 实例
```
function draw1(){
		cvs.shadowOffsetX=10;
		cvs.shadowOffsetY=10;
		cvs.shadowColor="#0000FF"
		cvs.shadowBlur=20;
		cvs.fillStyle="#449FDB";
		cvs.fillRect(50,50,100,100);
	}
```
![Alt text](./QQ截图20170608192453.png)

### 文本

>设置字体样式：cvs.font="字体大小（font-size） font-family"
>
>水平对齐方式：cvs.textAlign(对齐方式 属性值：start end right center) 书写格式：text-align=“”
>
>垂直对齐方式：cvs.textBaseline(top middle hanging bottom alphabetic ideographic)textBaseline=“”
>
>计算文本长度  var text="12345"  var length=cvs.measureText(text)
>
>填充文字  cvs.fillText(text,x,y)
>
>绘制文字轮廓  cvs.strokeText(text,x,y);
>
>text:文本内容
	>
>x,y 文字起始点坐标（你从那个地方开始写）

#### 实例
>1.基本的绘制文本
```
function draw2(){
     	var text="hello word";
     	cvs.fillStyle="#ffE470";
     	cvs.font="40px verdana";
     	cvs.textAlign="start";
     	cvs.textBaseline="top";
     	cvs.fillText(text,0,0);
     	var length=cvs.measureText(text)
     	cvs.fillText("字体长度为："+length.width,20,60)
     	
     }
```
![Alt text](./QQ截图20170608192904.png)

>2.填充绘制文本并且加线性渐变和阴影
```
function draw3(){
     	var CLG=cvs.createLinearGradient(0,150,450,250);
     	CLG.addColorStop(0,"red");
     	CLG.addColorStop(0.25,"yellow");
     	CLG.addColorStop(0.5,"green");
     	CLG.addColorStop(0.75,"yellow");
     	CLG.addColorStop(1,"red");
     	var text="hello word";
     	cvs.fillStyle=CLG;
     	cvs.shadowOffsetX=5;
     	cvs.shadowOffsetY=4;
     	cvs.shadowColor="#008000";
     	cvs.shadowBlur=5;
     	cvs.font="40px cursive";
     	cvs.textAlign="start";
     	cvs.textBaseline="top";
     	cvs.fillText(text,20,120);
     	var length=cvs.measureText(text).width;
     	cvs.fillText("字体长度为："+length,0,190)
     }
```


----------
![Alt text](./QQ截图20170608193121.png)

>3.边框绘制文本并且线性渐变和文本阴影
```
function draw4(){
     	var CLG=cvs.createLinearGradient(0,250,350,350);
     	CLG.addColorStop(0,"red");
     	CLG.addColorStop(0.25,"plum");
     	CLG.addColorStop(0.5,"yellow");
     	CLG.addColorStop(0.75,"skyblue");
     	CLG.addColorStop(1,"red");
     	var text="I LOVE YOU";
     	cvs.strokeStyle=CLG;
     	cvs.shadowOffsetX=5;
     	cvs.shadowOffsetY=4;
     	cvs.shadowColor="#0000FF";
     	cvs.shadowBlur=5;
     	cvs.font="40px simsun";
     	cvs.textAlign="start";
     	cvs.textBaseline="top";
     	cvs.strokeText(text,20,230);
     	
     	
     }
```
![Alt text](./QQ截图20170608193359.png)


### 绘图（真实图片）

> 不截取 
>  cvs.drawImage(Image,x,y,w,h)
- Image 就是可以放在DOM中的真实图片，可以动态创建，也可以获取页面上的
- x,y  图片左上角的坐标
- w,h  绘制图片的宽高

> 截取cvs.drawImage(Image,sx,sy,sw,sh,dx,dy,dw,dh)
- sx,sy  图片左上角的坐标
- sw,sh  矩形区域的宽高，用来截取图片
- dx,dy  截取出来放在canvas上的坐标
- dw,dh  画在canvas上的宽高；
- sx,sy,sw,sh 是截取图片的过程
- dx,dy,dw,dh 把截取出的图片放在canvas上的过程
>设置平铺
>cvs.createPattern(Image,type)
-  Image 就是可以放在DOM中的真实图片，可以动态创建，也可以获取页面上的
-  type no-repeat 不平铺 repeat 全放行平铺 repeat-x x轴方向平铺 repeat-y y轴方向平铺

### 实例

>1.不截取
```
 function draw1(){
   	var img=new Image();
   	img.src="img/QQ图片20170608164520.gif";
   	img.onload=function(){
   		cvs.drawImage(this,0,100,100,75)
   	}
   }
```
![Alt text](./QQ截图20170608193900.png)

>2.截取
```
 function draw2(){
   	var img=new Image();
   	img.src="img/QQ图片20170608164529.jpg";
   	img.onload=function(){
   		cvs.drawImage(this,480,150,440,410,0,0,200,200);
   		cvs.drawImage(this,70,80,400,400,200,0,200,200)
   	}
   }
```
>原图片
![Alt text](./QQ图片20170608164529.jpg)

>截取后
![Alt text](./QQ截图20170608194110.png)

>图片平铺
```
function draw3(){
    	var img=new Image();
    	img.src="img/QQ图片20170608164520.gif";
    	img.onload=function(){
    		var rep=cvs.createPattern(this,"repeat");
    		cvs.fillStyle=rep;
    		cvs.fillRect(0,0,draw.width,draw.height);
    	}
    }
```
![Alt text](./QQ截图20170608194638.png)

### 绘制图形的平移，缩放，旋转

>平移：cvs.translate(x,y)
-  x:坐标原点向x轴平移的距离
-  y:坐标原点向y轴平移的距离

>缩放：cvs.scale(x0,y0)
-  x0:  x轴按照x0的比例缩放
-  y0：y轴按照y0的比例缩放

>旋转：cvs.rotate（angle）
-  angle 坐标轴转的角度（和画圆的弧度计算是一样的）

#### 实例

>1.平移
```
function draw1(){
		cvs.fillStyle="red";
		cvs.fillRect(0,0,200,100);
		cvs.translate(50,0);
		cvs.translate(50,0);
		cvs.fillStyle="yellow";
		cvs.fillRect(0,0,100,50);
		
		
	}
```
![Alt text](./QQ截图20170608195639.png)

>2.缩放(等比缩放)
```
unction draw2(){
		cvs.scale(1,2);		
		cvs.fillStyle="yellow";
		cvs.fillRect(0,0,100,50);		
	}
```
![Alt text](./QQ截图20170608195805.png)

>3.旋转(X轴沿三点钟方向顺时针旋转了90度)
```
function draw3(){
		cvs.translate(100,0);
        cvs.rotate(Math.PI/2);       
		cvs.fillStyle="yellow";
		cvs.fillRect(100,0,100,50);		
	}
```
![Alt text](./QQ截图20170608195910.png)


### 图形组合
>图形组合：cvs.globalCompositeOperation=type;
>type的值：
- 1.source-over:默认值 在原来的图形上绘制新图（覆盖的意思）
- 2.destination-over：在原来的图形下面绘制新图
- 3.source-in：显示原来图形和新图的交集，新图在上，颜色就是新图的颜色
- 4.source-out:显示新图非交集部分
- 5.destination-in:显示原来图形和新图的交集，原来图形在上，颜色就是，原来图形的颜色
- 6.destination-out:显示原来图形非交集部分
- 7.source-atop：显示原来图和交集部分，交集是新图的颜色
- 8.destination-atop:显示新图和交集的部分，交集是原来图形的颜色
- 9.lighter:全部显示，交集是二者颜色的叠加
- 10.xor:显示非交集
- 11.copty:只显示新图

### 实例
```
unction draw1(){
     	cvs.fillStyle="yellow";
     	cvs.fillRect(10,10,100,100);
     	cvs.globalCompositeOperation="destination-over";
//      cvs.globalCompositeOperation="source-in";
//      cvs.globalCompositeOperation="source-out";
//      cvs.globalCompositeOperation="destination-in";
//      cvs.globalCompositeOperation="destination-out";
//      cvs.globalCompositeOperation="destination-out";
//      cvs.globalCompositeOperation="destination-atop";
//      cvs.globalCompositeOperation="lighter";
//      cvs.globalCompositeOperation="xor";
//      cvs.globalCompositeOperation="copty"
     	cvs.fillStyle="#0000FF";
     	cvs.fillRect(50,50,100,100);
     }
```

>1.destination-over：在原来的图形下面绘制新图
![Alt text](./QQ截图20170608200352.png)

>2.source-in：显示原来图形和新图的交集，新图在上，颜色就是新图的颜色
![Alt text](./QQ截图20170608200446.png)

>3.source-out:显示新图非交集部分
![Alt text](./QQ截图20170608200534.png)

>4.destination-in:显示原来图形和新图的交集，原来图形在上，颜色就是，原来图形的颜色
![Alt text](./QQ截图20170608200653.png)

>5.destination-out:显示原来图形非交集部分
![Alt text](./QQ截图20170608200740.png)

>6.source-atop：显示原来图和交集部分，交集是新图的颜色
![Alt text](./QQ截图20170608200959.png)

>7.destination-atop:显示新图和交集的部分，交集是原来图形的颜色
![Alt text](./QQ截图20170608200905.png)

>8.lighter:全部显示，交集是二者颜色的叠加
![Alt text](./QQ图片20170608202132.png)

>9.xor:显示非交集
![Alt text](./QQ图片20170608202141.png)

>10.copty:只显示新图
![Alt text](./QQ图片20170608202157.png)











