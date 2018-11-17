# less

## 目标

- 什么是预编译脚本语言less
- less的基本语法

## 知识内容

### 什么是less

作为一门标记性语言，CSS 的语法相对简单，对使用者的要求较低，但同时也带来一些问题：CSS需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码，造成这些困难的很大原因源于 CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。LESS 为 Web 开发者带来了福音，它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，LESS 可以让我们用更少的代码做更多的事情。

### less的安装

1. 安装nodejs https://nodejs.org/dist/ 可选择版本(6.0)。
2. 检查是否安装成功，使用cmd命令 node -v 查看版本即可。
3. 基于nodejs安装less:
    + 在线安装：使用cmd命令 npm install -g less
    + 离线安装:   
      a.找到C盘根目录下的用户或User文件夹打开  
      b.找到当前计算机使用的用户文件夹打开  
      c.找到隐藏文件夹AppData打开  
      d.找到Roaming文件夹打开  
      e.找到npm文件夹打开，该文件夹为基于nodejs程序目录  
      f.把npm.zip文件解压到该目录 
4. 基于koala软件也可以编译LESS;

### less编译

本质上，LESS 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。LESS 并没有裁剪 CSS 原有的特性，更不是用来取代 CSS 的，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。

```text
    lessc 目标文件地址 生成文件地址
```
在开发过程当中如果要预览less，每次都要执行编译命令，为了方便可以使用部分编辑器中less自动编译功能。
1. 点击文件打开菜单，选择设置选项
2. 选择工具当中的文件监听选项
3. 点击右上角加号按钮，选择less后弹出对话框，点击确定即可。less的语法

### less基本语法

- 变量
```less
    @mainColor:#e92323;
    @className:box;
    
    div{
      background: @mainColor;
    }
    a:hover{
      color: @mainColor;
    }
    //变量用于字符拼接使用方法
    .@{className}{
      color: @mainColor;
    }
```
- 混入(mixin)
```less
    .borderRadius(@width:100px){
      border-radius: @width;
      -webkit-border-radius:@width;
      -moz-border-radius:@width;
      -o-border-radius:@width;
      -ms-border-radius:@width;
    }
```
- 嵌套
```less
    .wjs_app{
      display: block;
      img{
        display: none;
      }
      /*需要连接的情况：&*/
      &:hover{
        img{
          display: block;
          position: absolute;
          left: 50%;
          margin-left:-60px;
          border: 1px solid #ccc;
          border-top: none;
          top:40px;
          z-index: 100000;
        }
      }
      > div{
        display: block;
      }
    }
```
- 导入
```text
@import "variables";
```
- 运算&内置函数

api地址：http://lesscss.cn/functions/#functions-overview

中文：http://www.css88.com/doc/less/functions/#color-operations

```less
   /*运算*/
   @num:5;
   ul{
     width: 100%*@num;
     li{
       width: 100%/@num;
       color: red+yellow+blue;
       background: gray*0.3;
       /*内置函数*/
       border-color: darken(red,20%);
     }
   } 
```
### less预览

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
## 总结

less是一门预编译脚本语法，使用它用来提高css的可维护性。