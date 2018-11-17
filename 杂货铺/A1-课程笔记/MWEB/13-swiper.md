#  swiper

## 目标

- 使用swiper解决移动端轮播图需求

## 知识内容

### 介绍

**Swiper**是纯javascript打造的滑动特效插件，面向手机、平板电脑等移动终端。

**Swiper**能实现触屏焦点图、触屏Tab切换、触屏多图切换等常用效果。

**Swiper**开源、免费、稳定、使用简单、功能强大，是架构移动终端网站的重要选择！

### 使用

##### Swiper4.x使用方法

1.首先加载插件，需要用到的文件有swiper.min.js和swiper.min.css文件。可下载[Swiper文件](http://www.swiper.com.cn/download/index.html#file1)或使用[CDN](http://www.swiper.com.cn/cdn/index.html)。

```html
<!DOCTYPE html>
<html>

<head>
    ...
    <link rel="stylesheet" href="path/to/swiper.min.css">
</head>
<body>
    ...
    <script src="path/to/swiper.min.js"></script>
</body>
</html>
```

2.HTML内容。

```html
<div class="swiper-container">
    <div class="swiper-wrapper">
        <div class="swiper-slide">Slide 1</div>
        <div class="swiper-slide">Slide 2</div>
        <div class="swiper-slide">Slide 3</div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>
    
    <!-- 如果需要导航按钮 -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
    
    <!-- 如果需要滚动条 -->
    <div class="swiper-scrollbar"></div>
</div>
导航等组件可以放在container之外
```

3.你可能想要给Swiper定义一个大小，当然不要也行。

```css
.swiper-container {
    width: 600px;
    height: 300px;
}  
```

4.初始化Swiper：最好是挨着</body>标签

```html
<script>        
  var mySwiper = new Swiper ('.swiper-container', {
    direction: 'vertical',
    loop: true,
    
    // 如果需要分页器
    pagination: {
      el: '.swiper-pagination',
    },
    
    // 如果需要前进后退按钮
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },
    
    // 如果需要滚动条
    scrollbar: {
      el: '.swiper-scrollbar',
    },
  })        
  </script>
</body>
```

如果不能写在HTML内容的后面，则需要在页面加载完成后再初始化。

```html
<script type="text/javascript">
window.onload = function() {
  ...
}
</script>
```

或者这样（Jquery和Zepto）

```html
<script type="text/javascript">
$(document).ready(function () {
 ...
})
</script>
```

5.完成。恭喜你，现在你的Swiper应该已经能正常切换了。

6.参考地址 http://www.swiper.com.cn/api/index.html

## 总结

移动端轮播图需求使用swiper来解决是一个好的选择。