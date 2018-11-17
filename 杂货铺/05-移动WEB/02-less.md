#                   less

## 1. 概念

```css
预编译脚本语言：在css的基础上加入了变量，mixin(混入),函数，运算等，让CSS也有一定的逻辑性，便于代码的复用和维护。同时也可以让代码变得更简洁
```

## 2.语法

### 1.变量(variable)

```css
/*定义变规则：
    必须使用使用@为前缀
    less每一行必须有分号
    不能以数组开头,不能包含特殊字符,大小写敏感
*/

示例 ：
@company:jd;
@maincolor:#ccc;

/*变量拼接使用 {}*/
@{company}-nav {
    width : 100px;
}
```
### 2.mixin(混入 ) 、函数
```css
  /*1. 通过ID或者类的方式混入,这种方式编译过后.position会出现在css文件中。*/

    .position{
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
    }
    .box {
        .position;      
    }

/*2. 定义函数,并传参(@direction:right为默认参数的设置的方式)*/
 .border(@direction:right,@color:red) {
    border-@{direction} : 1px solid @color;
}
 .float(@direction:left) {
    float: @direction;
}
/* 下面为调用*/
.box {
    .border(left,green);
}
.box1 {
    .float(left);
}
```

### 3.  嵌套 

```css
/* 伪元素和交集选择器前面用&符号连接*/
.box {
    width: 100px;
    ul {
        li {
            &.active{
                color : red;
            }
            height: 100px;
            a {
                color: 1px;
                &:before{
                    content:'444';
                }
            }
        }
    }
}
```

### 4.运算和内置函数

```css
/*运算包括数值运算和色值运算*/
@num:9;
.jd_banner{
  width: 100%;
  ul{
    width: 100% * @num;
    li{
      width: 100% / @num; //数值运算  运算后保留单位
      height: floor(200px / 6);
      color: red + green; //色值运算
      background: #222 + #555;
      border-color: lighten(red,20%);
    }
  }
}



```

api地址：http://lesscss.cn/functions/#functions-overview

中文：http://www.css88.com/doc/less/functions/#color-operations

### 5.引入

```css
/*一般在index.less页面引入其他的less模块，变量和函数模块 */
@import "veriable"    //  引入变量
@import "mixin"       // 引入函数和
@import "banner"     // 引入各个模块
@import "header"  
    
```

## 3.less预览

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" type="text/less" href="index.less">
    <script src="less.min.js"></script>
    <script>
        less.watch();
    </script>
</head>
<body>
    <!--1.在浏览器端直接使用less文件预览 type="text/less" -->
    <!--2.浏览器无法直接使用less类型的文件，无法解析-->
    <!--3.转换成css,需要js插件支持-->
    <!--4.下载插件 https://github.com/less/less.js/tree/master/dist -->
    <!--5.less.js会异步加载less文件的内容，再去解析成css,然后追加到style-->
    <!--6.必须使用HTTP形式打开页面，不要以file形式打开-->
    <!--7.更改完成之后每次要刷新，可以配置less监听，自动刷新页面预览-->
    <!--8.需要js配置 less.watch() -->
    <div class="box2">test</div>
</body>
</html>
```



## 4.rem适配布局(等比例缩放)

```css 
em  是相对单位  相对于父容器的字体大小

rem  是一个相对单位  r --- root  根  html 元素  相对于HTML的字体大小
rem布局的原理


rem 适配布局俩种：
1.使用flexible.js  淘宝团队写的。
2.使用媒体查询，适配多种设备
	编写less文件
	
```

### 4.1  媒体查询的方法

```css
//适配主流设备十几种
@adapterDeviceList:750px,720px,640px,540px,480px,424px,414px,400px,384px,375px,360px,320px;
//设计稿尺寸
@psdWidth:750px;
//预设基准值
@baseFontSize:100px;
//设备的种类
@len:length(@adapterDeviceList);
//适配函数
.adapterMixin(@index) when ( @index > 0){
  @media (min-width: extract(@adapterDeviceList,@index)){
    html{
      font-size: @baseFontSize / @psdWidth * extract(@adapterDeviceList,@index);
    }
  }
  .adapterMixin( @index - 1);
}
```

### 4.2  flexible适配布局



```css
/*使用flexible的唯一作用就是改变媒体查询的基准值，flexible的基准值为设计稿的1/10*/
/* 需要修改的地方
	1.改变基准值  @baseFontsize:@psdWidth/10;
	2.删除媒体查询的部分    也就是下面适配函数的部分
	3.@len长度删除
*/

//适配主流设备十几种
@adapterDeviceList:750px,720px,640px,540px,480px,424px,414px,400px,384px,375px,360px,320px;
//设计稿尺寸
@psdWidth:750px;
//预设基准值
@baseFontSize:@psdWidth/10;
//设备的种类
@len:length(@adapterDeviceList);
//适配函数
.adapterMixin(@index) when ( @index > 0){
  @media (min-width: extract(@adapterDeviceList,@index)){
    html{
      font-size: @baseFontSize / @psdWidth * extract(@adapterDeviceList,@index);
    }
  }
  .adapterMixin( @index - 1);
}
```

