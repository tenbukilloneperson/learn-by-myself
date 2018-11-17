# 				1.日常

## 1.多文件上传

```html 
<!--1. php提交文件，必须设置enctype="multipart/form-data"-->
<form action="01.php" enctype="multipart/form-data"></form>

<!-- 2.使用ajax上传多个文件 设置multiple  可以一次上传多个文件-->
<input type="file" name="files[]" multiple>
```



## 2.jquery的优点：

```js
// 1. 提供ajax

// 2. 良好的兼容性

```

## 3.数组的遍历

```javascript
var arr = [1,2,3];
// 1. 使用forEach..     jquery为  $.each()
arr.forEach(function (i,ele) {
    console.log(i,ele);
})
// 2. 使用for循环
for(var i = 0; i < arr.length;i++) {
    console.log(i,arr[i]);
};
```

## 4.window对象

```javascript
window.location.href  // 获取、设置当前的url地址
window.location.search   // 获取url查询参数

window.history.back()   // 回退一条历史记录
window.history.forwards()   //  前进一条历史记录
window.history.go(1)       // 前进制定条数的历史记录
window.history.pushState(null，null,url)    //  添加一条历史记录(H5的新属性),不发生跳转
window.history.replaceState(null,null,url)    // 替换一条历史记录(H5的新属性),不发生跳转
window.onresize = function (){}  //  页面尺寸改变事件
window.onpopstate = function() {}  //  切换历史记录事件
```





# 				2.web api

## 1.概念

```javascript
// 1. web api : 应用程序编程接口。浏览器预先提供的操作页面元素(DOM)和浏览器(BOM)的方法。
```

## 2.事件的设置

```javascript
// 1. 单个事件使用 on 的方式。
// 2. 设置事件时，如果事件源为动态创建的元素，(动态创建表格案例）
//     需要使用事件委托的方式设置。（e.target 和e.type）
// 3. 
```

## 3.BOM对象

```javascript
// 1. location对象
// 2. history对象
// 3. navagator-userAngent
```

## 4.select

```javascript
        var select = document.querySelector('select');
        select.onchange = function () {
            console.log(this.value);    //获取选中的value值。
            console.log(this.innerText)   // 获取文本1,2,3,4
        };
```

## 5.offset系列属性

```javascript
// 1. offsetWidth 获取自身的宽度(不包括margin）
// 2. offsetHeight 获取自身的高度(不包括margin)
// 3. offsetLeft  获取到定位父元素之间的距离（边框到边框之间的距离）
// 4. offsetTop  获取到定位父元素上边的距离  （边框到边框之间的距离）

jquery 中
// 1. offset()   获取到body元素之间的距离 {top:10,left:10}
// 2. position()   获取到定位父元素之间的距离   {left:100,top:100}
// 3. width()     获取自身的宽
// 4. innerWidth()  获取 padding+width
// 5. outerWidth()   获取padding+border+width
// 6. outerWidth(true)   获取盒模型总宽
```

# 					3.JS

## 1.数据类型及转换

```javascript
// 三元表达式和bool取反的应用
	在判断条件比较简单时，可以使用三元表达式来代替if 语句
    num.toString()    //  null 和 undefined 没有这个方法
	String(num)
```

## 2.switch语句

```javascript
// 语法结构： （一般用来做单值比较，因为是全等。）
switch(值) {
        case 条件1 ：
        代码1
        break;
        case 条件2 ：
        代码2
        break;
        //....
    default:
        代码3
        break;
}
//  也可以将值设置为true  ，然后条件设置为boolean值
```

## 3.数组的类型检测

```javascript
var arr = [1,2,3];
console.log(arr.instanceof Array)  // instanceof操作符    true
console.log(arr.constructor === Array)   // constructor构造器属性  true 
console.log(Object.prototype.toString.call(arr)）  //  [object Array];
            
// 伪数组转换为真数组的方式 
            //  arguments 为伪数组   arguments.callee 为当前函数
   Array.prototype.slice.call(arguments)
   [].slice.call(arguments)
   Array.from(arguments)
```

## 4.对象的应用

```javascript
// 1.  封装函数时，参数太多或者参数有可选参数时。可以以对象的形式传入
function (options) {
    name = options.name;
    age = options.age;
    gender = options.gender;
}
// 2.  将ajax获取到的数据库的英文信息转换为中文
var obj = {
    published : '已发布'，
    transhed : '未发布',
    rush : '草稿箱'
}
obj[status]  //  status为获取到的数据库信息(published,transhed, rush);
```

## 5.继承

```javascript
        function People (name,age,gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
        }
        People.prototype.sayHi = function () {
            console.log('peolple的方法');
        }

        function Student (name,age,gender,school) {
            // 注意：调用People时，一定要写上后续参数
            People.call(this,name,age,gender);
            this.school = school;
            Student.prototype = People.prototype;
            // Student.prototype.constructor = Student;
            Student.prototype.sayHaHa = function () {
                console.log('student的方法')
            }
        }
        var obj = new Student('lxn',18,'男','一种');
        console.log(obj);


	//  call()  和 apply()  的区别
	//  都是改变函数内this的指向。9
    //  不同的是传参方式不同，call()可以传入多个参数，第一个为this指向的的对象。后续参数依次传入
    //  apply()  第一个this的指向，第二个为数组。
```

