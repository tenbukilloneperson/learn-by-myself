# 					H5新特性

## 1 - domExtend（dom扩展）

### 选择器

```javascript
var li = document.querySelector('li:nth-child(2)')   // 获取第二个li元素
var lis = document.querySelectorAll('li')     // 获取页面所有的li
```

### DOM类名操作（h5）

```javascript
1. 添加类名  box.classList.add()   // 可以添加多个类名，不会覆盖
2. 删除类名  box.classList.remove()   //  移除类名
3. 切换类名  box.classList.toggle()     // 切换类名
4. 检测类名是否存在  ： box.classList.contains()     // 返回布尔值true 或者false	
```



### 自定义属性操作

```javascript
- 存储信息使用
- 遵循驼峰命名  data-user-name   userName   
- 不支持大写  即使大写也会默认转换小写 （data-passWord  会被默认为data-password）
- 获取属性  box.dataset.id 
- 设置属性  box.dataset.name = 'abc'
- 修改属性  box.dataset.name = '123'
- 删除属性   delete  box.dataset.name    // 对比删除对象的属性
```


### jquery类名操作

```javascript
addClass( )   // 添加类名
removeClass()  //移除类名
toggleClass()   // 切换类名
hasClass()   //检测类名是否存在
```



### jquery自定义属性操作

- data()  // 参数为：data- 后面的部分      
- attr()   // 参数为： 完整的属性名称

### 原生类名操作

box.className   操作

### 原生自定义属性操作

setAttribute()    getAttribute()   removeAttribute()



## 2 - fullScreen（全屏）

```javascript
- 	全屏 ：webkitRequestFullScreen()     //  一定要记得加私有前缀
- 	取消全屏 ：document.webkitCancelFullScreen()     // 取消全屏一定要设置给document
- 	窗口尺寸改变事件 ：window.onresize = function () {}    // 窗口大小改变时触发。
- 	document.isFullScreen检测当前是否处于全屏，不同浏览器需要添加前缀
          document.webkitIsFullScreen、document.mozIsFullScreen 
```

### 私有前缀（解决兼容）

```javascript

//	谷歌 sarfri ： webkit
//	火狐 ： moz
//	欧朋 ： o
//	IE  ： ms

```

```css
-webkit-transition : all 1s;
-moz-transition :all 1s;
-o-transition : all 1s;
-ms-transition : all 1s;
```




## 3 - madia(多媒体)

- ### 音频

  ```html
  <audio controls muted autoplay>出错时提示的信息</audio>   <!-- 添加音频-->
  ```

- ### 视频


```html
<video controls muted autoplay>出错时提示的信息</video>
```

## 秒数转换为时分秒的格式

```javascript
function date (time) {
    var h = Math.floor(time / 3600);      // 转换为小时
    var m = Math.floor(time % 3600 / 60);  // 转换为分钟
    var s = Math.floor(time % 60);    // 转换为秒
   return (h < 10 ? '0' + h : h) + ':'+(m < 10 ? '0' + m : m)+':'+(s < 10 ? '0' + s : s)
}
```

## 4.客户端存储信息方案

### 1.cookie 

```javascript
// 1. 数据格式：字符串和json字符串
// 2. 存储大小：4KB左右
// 3. 有效期 ： 默认的是关闭浏览器就失效。可以手动设置有效期
	// document.cookie = "username=xyy;Expires="+new Date('2100-01-01');
//4. 网络请求 ：请求报文会携带cookie信息。
```

### 2.localStorage 

```javascript
// 1. 数据格式 ： 字符串和json字符串（实际操作可以利用数组来保存，用JSON.stringify() 来转换为json格式）
// 2. 存储大小 ： 20mb左右
// 3. 有效期 ： 不手动删除就永久生效
// 4. 网络请求 ： 不会携带（毕竟数据量太大，如果携带消耗性能）	
// 5. 设置，获取，删除，修改，清空
	// 5.1 设置 localStorage.setItem(key,value);
	// 5.2 修改 localStroage.setItem(key,value1);
	// 5.3 获取 localStorage.getItem(key);
	// 5.4 删除 localStorage.remove(key);
	// 5.5 清空 localStorage.clear()    不能轻易使用，会清除所有的信息（包括浏览器自带的）
```

### 3. localSession

```javascript
// 1. 数据格式 ： 字符串和json字符串
// 2. 存储大小 ： 50mb左右
// 3. 有效期 ： 浏览器关闭失效，或者重新访问网址失效。其他情况有效。
// 4. 网络请求 ： 不会携带（毕竟数据量太大）
// 5. 操作
	// 5.1 设置 ：sessionStorage.setItem(key,value);
	// 5.1 修改 ：sessionStorage.setItem(key,value1);
	// 5.1 获取 ：sessionStorage.getItem(key);
	// 5.1 删除 ：sessionStorage.removeItem(key);
	// 5.1 清空 ：sessionStorage.clear();
```

## 5.拖拽

### 1.拖拽元素的事件

```html
<box class = "box" draggable = "true"></div>   <!--draggable属性必须加，元素才可以拖拽-->
```



```javascript
var box  = document.querySelector('.box');
// 1. 检测拖拽元素拖拽过程
box.addEventListener('drag',function () {})；
// 2. 检测元素开始拖拽的时刻
box.addEventListener('dragstart',function () {});
// 3. 检测托转元素结束的时刻
box.addEventListener('dragend',function () {});
// 4. 检测拖拽元素的的鼠标区域离开当前元素的时刻
box.addEventListener('dragleave',function () {});
```

### 2.目标元素的事件

```javascript
var target = document.querySelector('.target');
// 1. 检测进入目标元素事件
target.addEventListener('dragenter',function () {});
// 2. 检测在目标元素内移动事件
target.addEventListener('dragleave',function () {});
// 3. 检测文件在目标元素上放下事件
target.addEventListener('drop',function () {});
// 4. 检测元素李尅目标元素的事件
target.addEventListener('dragleave',function () {});

// 前三个事件内部一定要写 e.preventDefault()   ---- 阻止默认时间方法  一定要加括号。。。
```

### 3.历史记录

```javascript
// 1.   
//   回到上一条历史记录  history.back()
//   前进一条历史记录  history.forward()
//   前进或者后退几条历史记录  history.go(1)

// 2.  H5扩展的新的API
	  //    history.pushState(null,null,url)  追加一条新的而历史记录，不发生跳转，在切换后不刷新页面，
	  //    history.replaceState(null,null,url); 把当前的替换，不会跳转

// 3.  切换历史记录事件
        window.onpopstate = function (){
			location.href // 获取当前页面的url
        }
```

