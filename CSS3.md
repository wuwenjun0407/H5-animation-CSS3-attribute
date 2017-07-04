# CSS3

## 渐变

### 线性渐变 linear-gradient()
>从顶部到底部：
- top
- to bottom
```
background: linear-gradient(top,red,yellow,green,blue);
				background: -webkit-linear-gradient(top,red,yellow,green,blue);
```

>从底部到顶部：
- bottom
- to top
```
background: linear-gradient(to top,red,yellow,green,blue);
				background: -webkit-linear-gradient(to top,red,yellow,green,blue);
```

>从左到右：
-  left
-  to right
```
background: linear-gradient(to right,red,yellow,green,blue);
				background: -webkit-linear-gradient(to right,red,yellow,green,blue);
```

>从右到左：
- right
- to left
```
background: linear-gradient(to left,red,yellow,green,blue);
				background: -webkit-linear-gradient(to left,red,yellow,green,blue);
```

>从坐上角到右下角：
-  left top
-  left top to right bottom
```
background: linear-gradient(left top,red,yellow,green,blue);
				background: -webkit-linear-gradient(left top,red,yellow,green,blue);
```

>自定义渐变：（颜色后面加上百分比）

### 径向渐变
>圆心的位置50px 200px
```
#box1{
background: radial-gradient(50px 200px,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(50px 200px,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606143846.png)
>circle强制圆形渐变
```
#box1{
background: radial-gradient(circle,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(circle,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606144108.png)

>ellipse强制椭圆形渐变(只对长方形起作用)
```
#box1{
background: radial-gradient(ellipse,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(ellipse,#fff,yellow,green,red,plum);
}
```


----------
![Alt text](./QQ截图20170606144310.png)

>圆心在X轴50 Y轴50
```
#box1{
background: radial-gradient(200px 200px at 50px 50px,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(200px 200px at 50px 50px,#fff,yellow,green,red,plum);
}
			
```
![Alt text](./QQ截图20170606144526.png)

>扩散度紧凑
```
#box1{
background: radial-gradient(circle closest-side,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(circle closest-side,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606144849.png)

>靶心
```
#box1{
background: -repeating-radial-gradient(#fff,#fff 5px,green 10px);

background: -webkit-repeating-radial-gradient(#fff,#fff 5px,green 10px);
}
```
![Alt text](./QQ截图20170606145050.png)

>扩散度扩散
```
#box1{
background: radial-gradient(circle closest-corner,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(circle closest-corner,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606145214.png)

>圆心X轴0 Y轴50%（一半）
```
#box1{
background: radial-gradient(circle at 0 50%,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(circle at 0 50%,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606145357.png)

>和下面的一样
```
#box1{
background: radial-gradient(200px 200px at top,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(200px 200px at top,#fff,yellow,green,red,plum);
			}
```
![Alt text](./QQ截图20170606145532.png)
>圆心在X轴50%（一半） Y轴0
```
#box1{
background: radial-gradient(200px 200px at 50% 0,#fff,yellow,green,red,plum);

background: -webkit-radial-gradient(200px 200px at 50% 0,#fff,yellow,green,red,plum);
}
```
![Alt text](./QQ截图20170606145532.png)


## 边框
### box-shadow(x y a b c i)
>x：水平方向的偏移 正：右边，负：左边
>y：垂直方向的偏移 正：下 负：下
>a：模糊半径
>b：延伸半径
>c：颜色
>i：insert 设置内阴影
```
box-shadow:2px 2px 2px 2px #0000FF inset
```
>渐变（透明度越来越浅）
```
box-shadow: 1px 1px 1px rgba(0,0,0,.5),2px 2px 1px rgba(0,0,0,.4),3px 3px 1px rgba(0,0,0,.3),4px 4px 1px rgba(0,0,0,.2),5px 5px 1px rgba(0,0,0,.1);
```
### border-radius（）
```
正方形：四分之一圆
border-radius(0 200px 0 0)

长方形：半圆
border-radius（200px 200px 0 0）
```

### border-image()
>stretch 拉伸 默认值
```
-webkit-border-image: url(img/border.png) 27 stretch
```
![Alt text](./QQ截图20170606142208.png)

>round 平铺
```
-webkit-border-image: url(img/border.png) 27 round 
```
![Alt text](./QQ截图20170606142249.png)

>repeat 复制 
```
-webkit-border-image: url(img/border.png) 27 repeat 
```


----------
![Alt text](./QQ截图20170606142233.png)


## 背景类
### background-origin（默认值是padding-box）
>不会改变图片的大小，顾上不顾下，顾左不顾右，只要不超过border就可以

>border-box:从border的外边界算起,包括border
```
background-origin: border-box;
```
>content-box:只有内容部分不包括padding和border
```
background-origin: content-box;
```
>padding-box:包括padding不包括border
```
background-origin: padding-box;
```
###


## 文本
### 1.text-overflow:clip/ellipsis
>clip：对于文本内容超出容器会被裁剪，但是不会显示省略号，可以单独使用
>ellipsis：超出内容显示省略号，必须配合使用overflow：ellipsis ||  white-space：nowarp，才有效果
### 2.word-wrop:normal/break-word
>normal：默认值。控制文本连续换行（但是允许里面内容撑破边界，英文单词是一个整体，不会因为到头就马上换行，或者词语）
>break-word：在容器边界换行（不截断英文单词）
### 3.word-break：normal/break-all/keep-all
>normal：默认值。中文会换行，英文不会
>break-all：可以强制截断英文换行
>keep-all：不允许断开，中文会把标点符号前后一个词或者短语整个换行 英文加上“—”会折行
## 2D变形

### transtion
>transition：left 2s 1s ease-out 过渡
```
参数1：一个具体的属性left/或者all，
参数2：运动时间
参数3：延迟时间
参数4：运动曲线
ease:默认值 渐渐变慢
linear：匀速直线运动
ease-in:由慢变快
ease-in-out：由慢变快再变慢
```

### transform (下面是他的属性)
```
transform:translate(X,Y) scale(n)  rotate(deg)
```
>translate(X,Y)   平移
>每一次移动坐标改变了；
>坐标是根据元素来画的，每个元素都有自己各自的坐标，各自之间没有关系，现有元素才会有坐标
```
X:向X轴方向平移 正：右边，负：左边
Y:向Y轴方向平移 正：下边，负：上边
translate(X)====translateX(X) 
如果你只传了一个值就代表 向X轴方向平移
```
>scale(n)  缩小放大表示的是轴缩小放大
```
 n:(0-1)缩小  ，n>1放大，n=1不变
scaleX(nX)x轴方向缩小、放大
scaleY(nY)x轴方向缩小、放大
```
>rotate(20deg) 旋转
```
绕着中心（元素中心）旋转20度  正：顺时针  负：逆时针
```
>skew(Xdeg,Ydeg)  倾斜
```
只穿了一个就相当于skewX(Xdeg);
```

## 3D变形
>视距：模拟眼睛到元素的距离，一般都是给较高级，父级的父级
>3D属性： transform-style：preserve-3d，告诉浏览器这里面呈现出来的是3D效果，一般都是给父级加
>平移：translateX，translateY，translateZ（正是前，负是后）
>旋转：rotateX，rotateY，rotateZ。注意：从轴的正方向开始看 rotate3d（x,y,z）
>scaleX() scaleY()  scaleZ()

## 动画 animation
>animation：自定义动画名字(必填)，运动总时间（必填），延时时间（选填），执行的次数（ 默认是一次，infinite：无数次），运动曲线（默认ease），both（停在最后结束的位置）；
>perspective-origin: 50% 50%; 视觉中心
```
.box{
width: 100px;
height: 100px;
position: absolute;
left: 10px;
top: 10px;
background-color: yellow;
animation: go 2s 1s infinite linear both;
}
@(H5移动端动画)-webkit-keyframes go{
/*自定义动画的过程*/
0%{left: 10px;}
/*刚开始的时候*/
/*25%{}
50%{}
75%{}*/
100%{left: 1000px;}
/*结束的时候*/
	}
```