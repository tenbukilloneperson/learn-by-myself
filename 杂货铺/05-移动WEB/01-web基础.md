;一  流式布局

## 1.viewport 

```html
<!--viewport 视觉窗口。移动端才有的概念， 在移动端特有的一个区域，这个区域用来承载网页，显示在浏览器窗口内，虚拟的。 默认的宽度是980px 可以缩放  默认的缩放比例  运行用户自行缩放功能-->
```

## 2.标准设置

```html 
<meta name = "viewport" content = "width=device-width,initial-scale=1.0,user-scalable=no">
<!--1. 页面的宽度和设备的宽度一致 当前设备宽度
2. 页面的缩放比例和PC保持一致 1.0
3. 不允许用户自行缩放-->

<!--width:视口宽度   单位PX  device-width
height:视口的高度  一般不使用
initial-scale:视口的默认缩放比例  1.0
user-scalable:用户缩放功能  允许缩放 yes 1  不允许缩放 no 0
maximum-scale:允许的最大缩放比例
minimum-scale:允许的最小缩放比例-->
```

## 3.适配的四种布局方式

### 1.流式布局：

```css
- 就是百分比布局，当页面尺寸发生改变的时候，网页内容会向两侧填充 ，流动的效果。
- 特点：宽度自适应，高度固定.一般布局容器使用百分比，内部元素也可以根据情况使用固定像素
.container {
    width:100%;
    max-width:750px;
    min-width:320px;
    margin : 0 auto; //一般是为了在开发阶段的观看效果。
}
```



### 2.响应式布局（bootstrap 一套页面可以兼容多类不同的设备）

```javascript
// 使用bootstrap 提供的布局盒子。
// .container  响应式布局
// .container-fluid  流式布局容器  和栅格系统
```



### 3.REM布局

```javascript
//  rem 布局是所有使用数值属性的值都是用相对单位rem,rem是相对于根元素（html）的字体大小。
//  原理就是当页面尺寸发生改变时，通过媒体查询来改变html的font-size的大小。从而使页面元素的尺寸发生改变。
//  需要注意的是：这种布局是等比例缩放，宽高都发生变化。
//  当前基准值的计算方式为 ：当前屏幕尺寸 / 设计稿的尺寸 * 设计稿下的基准值；
```



### 4.flex布局

```javascript
	必须是父元素套着一个子元素,父元素设置display:flex
    // 设置flex属性后，子元素默认为行内块的显示模式，
            /*1. flex布局 不是指的一个盒子  是一个父容器套着子容器 */
        /*2. 成为伸缩布局  需要给父容器指定盒模型 display: flex;*/
        /*3. 子容器  默认呈现出  行内块元素的特性 */
        /*4. 默认的排列的方式  以行进行排列   而且默认是不会换行的  即使超过了宽度 也不会换行 会压缩*/
        /*5. 子容器 flex 属性  宽度失效*/
        /*6. flex:1  意思：把剩余的宽度分成若干份（是子容器的flex属性的值的和） 子容器的flex值是多少就占几份*/
   
      <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 100%;
            height: 100%;
            background: pink;
            /*基于浏览器*/
            position: absolute;
            left: 0;
            top: 0;

            display: flex;
            /*flex布局的排列方向 默认是行方向 row  也有列方向 column*/
            flex-direction: column;
        }

        header{
            width: 100%;
            height: 50px;
            background: green;
        }

        section{
            flex: 1;
            background: yellow;
            width: 100%;
            display: flex;
        }
        section aside{
            flex: 1;
            height: 100%;
            background: red;
            /*排序  根据 order 的值 从小道到大排列*/
            order: 2;
        }
        section article{
            flex: 2;
            background: blue;
            order: 1;
        }

    </style>
</head>
<body>
<div class="box">
    <header></header>
    <section>
        <aside></aside>
        <article></article>
    </section>
</div>
</body>
</html>

```



## 4.二倍图

用于解决移动端图片失真的问题，一般将图片做成二倍像素的大小，通过压缩来获得高清显示

```css
/*背景图：*/
.box {
    background-size : 100px 100px;
}
/*图片*/
img {
    width : 100px;
    height : 100px;
}
```



## 5. 移动端 reset css

```css
a {
	text-decoration:none;
    color : #333;
    /*清除移动端点击a高亮显示*/
    -webkit-tap-highlight-color :transparent;
}
input[type="text"],input[type="search"] {
    border:none;
    outline:none;
    /*输入框 在safari 浏览器中 立体效果 阴影效果*/
    -webkit-appearance:none;
}
*,*::before,*::after {
      /*设置宽度从边框开始计算*/
    /*防止盒子的宽度溢出屏幕的宽度 导致出现横向的滚动条*/
    box-sizing : border-box;   // content-box  //padding-box
    -webkit-box-sizing : border-box; 
}
```

## 6.background属性

```css
background-position-x : 100%;  /*（容器的宽度-背景图的宽度）*100%  可以解决不同分辨率的兼容性问题*/
background-size : 100px 200px;
background-origin : content-box/border-box/padding-box; /*背景图定位的起点，以内容的区域的左上角开始*/
background-clip : content-box; /*裁剪的区域  从内容区域开始裁剪*/
background : url(images/01.jpg) no-repeat 100px 100px / 200px 200px;
```

## 7.移动端的touch事件

```javascript
        // 触摸事件时移动端特有的事件:
        // 1. ontouchstart 触摸开始时触发
        // 2. ontouchmove  触摸开始移动时触发
        // 3. ontouchend   触摸结束时触发
        // 4. ontouchcancel 被迫取消(触摸时来电话被迫取消)

        // 触摸点集合:
        // e.touches  页面上所有触摸点集合
        // e.targetTouches  当前元素的触摸点集合
        // e.changeTouches   改变后的触摸点集合
        // 总结：
	    // 在touchend事件结束后,页面和当前元素是没有触摸点的,所以只能通过changedTouches来获得触摸点信息

        // 滑动的原理：
        // 使用touch相关事件,先获取起始触摸点的坐标,在滑动过程中或者滑动结束时,记录当前触摸点的坐标。
        // 根据当前坐标和起始坐标比较得到移动的距离,把移动的距离设置给目标元素

        // e.touches[0]  第一个触摸点的坐标
        // clientX/Y   基于浏览器窗口的坐标(视口坐标)
        // pageX/Y     基于页面的坐标
        // screenX/Y   基于屏幕的坐标
```

## 8. 移动端布局常用

```javascript
// 1. 局部作用域内的变量，其他局部作用域访问不到。可以使用变量提升，将此变量声明为全局变量（联想滑动事件）
// 2. 流式布局：布局盒子设置为百分比。只有容器盒子设置为百分比即可。
	// 并排的li,可以将li设置为百分比，然后内部的内容设置为固定像素
	// 三栏自适应布局：
		// - 自身定位法
		// - 左右盒子固定像素，绝对定位。中间一栏宽度设置为100% 自适应4

----------------------------------------------------------------------------------------------
移动端使用属性，最应该注意的要加-webkit-前缀。兼容weblit内核的浏览器

//  轮播图 ： 
	// 1. ul可以设置绝对定位，父容器设置相对定位。通过改变ul的left值来实现动画滑动的过程。
	// 2. CSS3 可以使用 transform:translateX 来改变ul的位置，配合过渡属性也可以产生动画的效果。

-------------------------------------------------------------------------------------------------
// 2.设置小圆点(主要看类名now的应用)
	var setPoint = function () {
    	point.querySelector('li.now').classList.remove('now');
    	point.querySelector('li:nth-child('+index+')').classList.add('now');
	}；		
//  间距自适应  ---图片宽度固定   等比例缩放，图片设置百分比
768  -992   -1200
```

## 9.入口函数

```javascript
//1. jS入口函数:
	 - window.onload = function (){}   页面所有资源加载完成（结构，图片和文件）
	 - document.addEventListener('DOMContentLoaded',function (){})  页面结构加载完成（html文档）

// 2.jquery 
     - $(function(){})   页面结构（html文档）加载完成时触发
     - $(document).ready(function(){}) 页面结构（html文档）加载完成时触发
     - $(window).load(function(){})  页面资源完全加载完成时触发
```

# 				二、响应式布局

## 1.响应式布局的概念

```javascript
  // 响应式布局 ： 一个页面可以适配多个终端（多个设备）。
```

## 2.媒体查询

```css
/* 1. bootstraps响应式布局的原理就是媒体查询和百分比。
   2. 设备分类和版心的大小
		2.1  超小屏设备(xs)  < 768px  	    版心：100%         --手机
		2.2  小屏设备(sm)    768px -992px    版心：750px		--pad
		2.3  中屏设备(md)    992px-1200px    版心：970px		--大头电脑
		2.4  大屏设备(lg)    >1200px         版心：1170px		--大屏电脑，LED显示屏等等
   3.兼容性问题 ：
				css3新技术 IE8以下不支持。
			    bootstrap中使用了条件注释，引用respond来处理这个媒体查询的兼容性问题
*/
media screen and (max-width:1200px) and(min-width:992px) {
    /*满足条件的才会生效*/
    .container {
        width : 970px;
        background : yellow;
    }
}
```

## 3.条件注释

```html
条件注释，满足条件才浏览器才会渲染。不满足条件自动略过。一般用来处理兼容性问题的文件
<!--[if lt IE 9]>
	// 处理媒体查询在IE9以下不支持的问题，只能运行在HTTP协议中
	<script src = "assets/bootstrap/respond.js"> 
	// 处理H5语义标签在IE9以下不支持的问题
	<script src = "assets/bootstrap/html5shiv.js"> 
<![endif]-->
```

## 4. Normalize.css 与自己写的reset.css的区别？

```css
Normalize.css和reset.css都是重置样式表。为了增强浏览器的表现一致性。
区别：
	Normalize.css 对于一些在不同浏览器表现一致的样式没有做修改。比如ul的小圆点（温柔）
	reset.css 不管样式是否一致，都会按照自己的要求去修改。（残暴）
```

## 5. Bootstrap 

```html 
<!--h5文档申明-->
<!DOCTYPE html>
<!--文档语言申明  en zh-CN zh-tw -->
<html lang="zh-CN">
<head>
    <!--文档编码申明-->
    <meta charset="utf-8">
    <!--要求当前网页使用浏览器最高版本的内核来渲染-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--视口的设置：视口的宽度和设备一致，默认的缩放比例和PC端一致，用户不能自行缩放-->
    <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <!-- 优先加载和浏览器解释 -->

    <title>title</title>

    <!-- Bootstrap 核心样式-->
    <link href="../lib/bootstrap/css/bootstrap.css" rel="stylesheet">
    <!-- html5shiv 和  respond 分别用来解决IE8版本浏览器不支持 H5标签和媒体查询的  不兼容问题-->
    <!-- HTML5 shiv and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- 警告：不能以file形式打开，本地打开。最好http://打开 -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!-- 在 IE 9 一下引入-->
    <!--[if lt IE 9]>
    <script src="../lib/html5shiv/html5shiv.min.js"></script>
    <script src="../lib/respond/respond.min.js"></script>
    <![endif]-->
</head>
<body>
<!--自己网页的内容-->
<!-- bootstrap依赖jquery-->
<script src="../lib/jquery/jquery.min.js"></script>
<!-- bootstrap js 核心文件-->
<!-- bootstrap.js包含所有的插件-->
<script src="../lib/bootstrap/js/bootstrap.min.js"></script>
</body>
</html>
```

## 6.Bootstrap常用类

```javascript
// 1.布局容器和栅格系统
// 		.container  响应式布局容器
//  	.container-fluid  流式布局容器
//  	.row 行，同时也可以去除父容器左右15px的槽距(内边距)，如果父元素没有内边距，没有必要调用.row
//  	.col-xs-4   列-设备-每一个容占4份
// 2. 栅格扩展
//		- 可嵌套
//		- 可偏移  .col-xs-offset-1  往右偏移一份。（占据位置）
//		- 可排序  .col-xs-push-3  往右推3份   .col-xs-pull-9 往左拉9份  (空白的地方不占据位置)
// 3. 响应式工具
//		-	.hidden-lg 	.hidden-md  .hidden-sm  .hidden-xs(超小屏设备的时候隐藏.其他设备不是生效)
//		-	.visible-lg 	.visible-md  .visible-sm  .visible-xs(超小屏设备的时候显示，其他设备不生																			效) --不建议使用
// 4. pull-right ,pull-left 左右浮动  clearfix 清除浮动
// 5. caret  下三角 
<button type="button" class="close" aria-label="Close"><span aria-hidden="true">&times;</span>		</button>
// 6. 显示隐藏 ： show  和 hidden/sr-only 
```

## 7.字体图标

```css
/* 1.定义自定义字体图标  定义字体的统一规范 */
@font-face {
    font-family: "heima56";
    src: url('../fonts/MiFie-Web-Font.eot'); /* IE9*/
    src: url('../fonts/MiFie-Web-Font.eot#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('../fonts/MiFie-Web-Font.woff') format('woff'), /* chrome, firefox */
    url('../fonts/MiFie-Web-Font.ttf') format('truetype'), /* chrome, firefox, opera, Safari, 		Android, iOS 4.2+*/
    url('../fonts/MiFie-Web-Font.svg#iconfont') format('svg'); /* iOS 4.1- */
}
/* 2.定义使用改字体的类 */
.wjs-icon {
    font-family: heima56;
}
/* 3.定义具体的体表样式 */
.wjs-icon-phone::before {
    content: 'e\908';
}

/* 使用 */ 
<span class = "wjs-icon wjs-icon-phone"></span>
```

## 8.轮播图

```javascript
//  在pc端 图片高度固定，宽度自适应(width:100%),居中显示；  
//  居中可以使用背景图，background: no-repeat center;

// 在移动端（mobile）图片要等比例缩放  width : 100%  ,高度自适应
```

## 9.Bootstrap 常用组件和插件及类名

```html
<!--媒体对象：-->
<div class="media">
  <div class="media-left media-middle">
    <a href="#">
      <img class="media-object" src="..." alt="...">
    </a>
  </div>
  <div class="media-body">
    <h4 class="media-heading">右侧盒子的标题</h4>
    ...可以加入其它的文本内容
  </div>
</div>
<!--导航条-->
<!--tab栏切换   js插件标签页-->
```

## 10 .元素居中问题

```css
/* 1. 居中块元素(没有脱离文档流的)*/
.box {
    width :200px;
    height : 200px;
    margin :0 auto;
}
/* 2. 居中一个浮动的元素 （这种方法必须设置宽高）*/
.box {
    width: 200px;
    height : 200px;
    backgground : yellow;
	position: absolute;
    margin: auto;
    left: 0;
    right: 0;
    top: 100px;
}  
/*3. 行内元素(inline)和行内块元素(inline-block)在块元素中居中*/ 
.box {
    text-align : center;
}
/* 4. 文字在块元素中垂直居中,设置行高等于高度即可*/
.box {
    height : 80px;
    line-height : 80px;
}
/* 5. 行内宽元素垂直对齐，vertical-align : center;*/
```

## 11 .css样式的继承

```css
浮动元素在后面，受到块元素高度的影响。浮动的元素放在前面。。
/* 可以继承的样式：
      1. text-开头的(text-align:center) 
      2. font-开头的(font-size、font-weight等等..) 
      3. color (a比较特殊,不能继承父元素的颜色)  
      4. cursor (鼠标样式  cursor : pointer)
      5. line-height : 80px; 行高也可以继承
*/
```







