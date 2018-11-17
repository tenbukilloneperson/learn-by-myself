# bootstrap

## 目标

- 掌握bootstrap的基本样式使用
- 掌握bootstrap的基本组件使用
- 能够使用bootstrap完成响应式页面

## 知识内容

### 什么是UI框架

user interface 用户界面，指的是有预制样式库，组件，插件，有一套比较完整的网页功能解决方案，称为UI框架

### bootstrap是什么

- 简介：  
    + 作者：Twitter  公司两位前端工程师（mark otto && jacob thornton）在2011发起开发完成的。
    + 特点：组件简洁大方，代码规范精简，界面自定义性强。
    + 目的：提高web开发效率。  
- 文档：  
    + 中文官网  http://www.bootcss.com/
    + 官网 http://getbootstrap.com/
    + 学习文档 http://bootstrap.css88.com/  
- 优点：  
    + 有自己的生态圈，不断的更新迭代。
    + 提供了一套简洁、直观、强悍的组件。
    + 标准化的html+css编码规范。
    + 让开发更简单，提高了开发的效率。
    + **注意：虽然界面组件样式已经定义好了，但是扩展性相对较强，也就是说我们还可以自定义，修改默认样式。**
- 版本:  
    + 2.x.x  停止维护,兼容性好,代码不够简洁，功能不够完善。
    + 3.x.x  目前使用最多,稳定,但是放弃了IE6-IE7。对IE8支持但是界面效果不好,偏向用于开发响应式布局、移动设备优先的 WEB 项目。

### bootstrap基本模板

````html
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
    <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=0">
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
<!--TODO-->
<!-- bootstrap依赖jquery-->
<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
<script src="../lib/jquery/jquery.min.js"></script>
<!-- bootstrap js 核心文件-->
<!-- Include all compiled plugins (below), or include individual files as needed -->
<script src="../lib/bootstrap/js/bootstrap.min.js"></script>
</body>
</html>
````
### bootstrap常用类

- container
- container-fluid
- row
- col-\*-\*
- col-\*-offset-\*
- col-\*-pull-\*
- col-\*-push-\*
- pull-left
- pull-right
- text-center
- text-left
- text-right

### 怎么使用组件

查询官方文档

- 组件的HTML模板代码结构分析
- 写一份和组件一致的样式选择器修改预制样式为产品需求样式
- 检查响应式是否符合产品需求，不满足自行修改

## 总结

bootstrap是一个完整的组件库，包含html,css,js的框架，能够快速的搭建响应式站点。