# rem适配方案

## 目标

- 掌握rem的适配原理
- 掌握rem+媒体查询适配方案
- 掌握rem+flexible.js适配方案

### 知识内容

### rem的适配原理

- rem 是相对于页面根源素html的字体大小的一个尺寸单位
- 页面内容可以使用rem为单位，那么html的字体大小就是一个控制尺寸的开关
- 当设备改变的时候可以根据设备的宽度和原本设计稿的尺寸比例关系设置html的字体大小
- 这样凡是以rem为单位的内容会根据设备做等比适配

```text
    1.假设设计稿是750px
    2.假设这个时候html字体大小为100px
    3.那么在320px设备的时候  字体大小为 100/750*320
    4.只要根据这个比例在不同设备设置rem基准值(html字体大小)即可
    5.改变rem基准值有两种方式：媒体查询或javascript
```
### rem+媒体查询

```css
/*假设的设备  320px 414px 640px */
@media (min-width: 320px) {
    html{
        font-size: 50px;
    }
}
@media (min-width: 414px) {
    html{
        font-size: 64.6875px;
    }
}
@media (min-width: 640px) {
    html{
        font-size: 100px;
    }
}
```
### rem+flexible.js

- flexible.js 是手机淘宝团队做移动端适配的库
- 我们使有它的目的只有一个根据设备设置rem基准值

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=.0">
<script src="flexible.js"></script>
```
### 基于less的rem可维护方案

```less
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
## 总结

使用rem完成页面的适配，注意不一定全部都是rem,大布局的适配还是可以使用流失布局或者伸缩布局。