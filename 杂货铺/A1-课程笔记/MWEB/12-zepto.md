# zepto.js

## 目标

- 能够使用zepto完成移动端操作
- 了解zepto的模块组成

## 知识内容

### zepto介绍

- Zepto是一个轻量级的针对现代高级浏览器的JavaScript库， 它与jquery有着类似的api。 如果你会用jquery，那么你也会用zepto。
- Zepto模块

| module     | default | description                              |
| ---------- | ------- | ---------------------------------------- |
| zepto      | ✔       | 核心模块；包含许多方法                              |
| event      | ✔       | 通过on()& off()处理事件                        |
| ajax       | ✔       | XMLHttpRequest 和 JSONP 实用功能              |
| form       | ✔       | 序列化 & 提交web表单                            |
| ie         | ✔       | 增加支持桌面的Internet Explorer 10+和Windows Phone 8。 |
| detect     |         | 提供 $.os和 $.browser消息                     |
| fx         |         | The animate()方法                          |
| fx_methods |         | 以动画形式的 show, hide, toggle, 和 fade*()方法.  |
| assets     |         | 实验性支持从DOM中移除image元素后清理iOS的内存。            |
| data       |         | 一个全面的 data()方法, 能够在内存中存储任意对象。            |
| deferred   |         | 提供 $.Deferredpromises API. 依赖"callbacks" 模块. 当包含这个模块时候, $.ajax() 支持promise接口链式的回调。 |
| callbacks  |         | 为"deferred"模块提供 $.Callbacks。             |
| selector   |         | 实验性的支持 jQuery CSS 表达式 实用功能，比如 $('div:first')和 el.is(':visible')。 |
| touch      |         | 在触摸设备上触发tap– 和 swipe– 相关事件。这适用于所有的`touch`(iOS, Android)和`pointer`事件(Windows Phone)。 |
| gesture    |         | 在触摸设备上触发 pinch 手势事件。                     |
| stack      |         | 提供 andSelf& end()链式调用方法                  |
| ios3       |         | String.prototype.trim 和 Array.prototype.reduce 方法 (如果他们不存在) ，以兼容 iOS 3.x. |

### 自定义打包

```text
1、首先在自己的电脑上要安装Node.js和npm包管理工具；
2、从github上下载zepto.js的源文件包到本地磁盘（例如：E:\Learning\JS）；地址：https://github.com/madrobby/zepto
3、将下载的zepto压缩包解压，进入，找到make文件，打开，找到第42行的位置，添加需要的模块名称（这里增加了fx_methods 和 fx 模块），以空格做分隔；  
modules = (env['MODULES'] || 'zepto event ajax form ie').split(' ')
4、运行中，cmd打开命令窗口，并进入zepto文件目录；
5、执行 npm install 命令；
6、输入npm run-script dist 命令，进行构建；
```
## 总结

zepto就是jquery的轻量版，功能差不多，但是不完全覆盖。