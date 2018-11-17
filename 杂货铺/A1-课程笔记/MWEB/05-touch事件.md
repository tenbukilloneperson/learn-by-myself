# 触摸事件

## 目标

- 掌握移动端触摸事件
- 掌握移动端滑动效果的实现

## 知识内容

### 触摸事件

| 事件          | 说明                    |
| ----------- | --------------------- |
| touchstart  | 当手指触碰屏幕时候触发该事件        |
| touchmove   | 当手指在屏幕上滑动时候触发该事件      |
| touchend    | 当手指离开屏幕时触发该事件         |
| touchcancel | 当系统停止跟踪（被迫终止）触摸时候会触发。 |

| 触摸点集合          | 说明              |
| -------------- | --------------- |
| targetTouches  | 目标元素的所有当前触摸点集合  |
| changedTouches | 目标元素的最新更改的触摸点集合 |
| touches        | 页面上的所有触摸点集合     |
注意：在touchend事件的时候event只会记录changedtouches

| 点坐标             | 说明        |
| --------------- | --------- |
| pageX/pageY     | 基于页面大小的坐标 |
| clientX/clientY | 基于视口大小的坐标 |
| screenX/screenY | 基于屏幕大小的坐标 |

### 滑动效果原理

```js
imageBox.addEventListener('touchmove', function (e) {
        var moveX = e.touches[0].clientX;
        distanceX = moveX - startX;
        /*计算将要给图片盒子的定位*/
        /*基于当前的定位去计算*/
        var translateX = -index * width + distanceX;
});
```



## 总结

移动端滑动效果，就是使用touch事件，拖动元素。