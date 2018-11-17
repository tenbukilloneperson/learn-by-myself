# dom扩展

## 目标

- 能够使用H5扩展API完成页面效果

## 扩展内容

### 获取元素

~~~javascript
document.getElementsByClassName ('class'); 
//通过类名获取元素，以伪数组形式存在。

document.querySelector('selector');
//通过CSS选择器获取元素，符合匹配条件的第1个元素。

document.querySelectorAll('selector'); 
//通过CSS选择器获取元素，以伪数组形式存在。
~~~

### 类名操作

~~~javascript
Node.classList.add('class'); 
//添加class

Node.classList.remove('class'); 
//移除class

Node.classList.toggle('class'); 
//切换class，有则移除，无则添加

Node.classList.contains('class'); 
//检测是否存在class
~~~

### 自定义属性

> 在HTML5中我们可以自定义属性，其格式如下data-*=""

~~~html

<div id="demo" data-my-name="itcast" data-age="10">
<!--1. 大家理解的自定义属性：自己定义的属性-->
<!--2. 非标准属性：就是自定义属性-->
<!--3. 像：name class id title alt 标准属性  反之 非标准-->

<!--H5规范 用来存储数据的属性 -->
<!--4. 以 data- 开始的属性认为是自定义属性 -->
<!--5. 操作自定义属性注意些：-->
<!--6. dataset对象 指定的是当前dom元素上的自定义属性的集合 -->
<!--7. 获取自定义属性：dataset.属性名称 dataset[属性名称] -->
<!--8. 设置自定义属性： dataset.属性名称 = 属性值   dataset[属性名称] = 属性值 -->
<!--9. 自定义属性的名称遵从驼峰命名 -->
<!--10. dom上的属性的定义 不支持大写 写了也转换成小写-->
<script>
/*
  Node.dataset是以对象形式存在的，当我们为同一个DOM节点指定了多个自定义属性时，
  Node.dataset则存储了所有的自定义属性的值。
  */
var demo = document.querySelector(反馈);
//获取
//注：当我们如下格式设置时，则需要以驼峰格式才能正确获取
var name = demo.dataset['myName'];
var age = demo.dataset['age'];
//设置
demo.dataset['name'] = 'web developer';
<script/>
~~~
## 总结

在不使用第三方库的情况下，使用最便捷的方式操作DOM，完成页面效果