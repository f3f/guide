title: CSS 浏览器兼容处理
---

## Html5
低版本浏览器兼容 Html5 新标签，引入：
```
<script src="//cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script>
```

## Media Query
低版本浏览器无法识别 Media Query，引入：
```
<script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
```

## CSS3 选择器
IE8 不支持 CSS3 选择器，可引入 selectivizr-min.js 解决 selectivizr-min.js
需要其它 js 库进行支持，不同 js 库对其支持程度不同，推荐使用 nwmatcher.js；
两者结合可满足 CSS3 绝大多数选择器：
```
<script type="text/javascript" src="Lib/nwmatcher.js"></script>
<script type="text/javascript" src="Lib/selectivizr-min.js"></script>
```

## nth-child(even)
table 的隔行变色 用 nth-child(even)不兼容，可引入：
```
<script src="//cdn.bootcss.com/selectivizr/1.0.2/selectivizr-min.js"></script>
```

## linear-gradient
CSS 属性颜色渐变 linear-gradient，低版本浏览器不兼容，可使用 hack 技术添加一纯色背景 background-color: #f5840c\9;

## 水平布局
inline-block下padding元素重叠，使用float: left替代display: inline-block实现水平布局；

## line-height
行内样式垂直居中问题，有时 line-height 和高度相等在 ie8 无效果，使用vertical-align：middle；

## button左右两边留白
ie8 下 button 按钮左右两边留白的问题，用 overflow:visible;padding:0;

## z-index
低版本浏览器 z-index 失效，给元素都添加 postion:relative；

## background-size
让 ie7\ie8 支持 CSS3 background-size，引入 backgroundsize.min.htc，例子：
```
body {
height: 100%;
margin: 0;
background: url(images/126.jpg) center no-repeat;
background-size: cover;
-ms-behavior: url(backgroundsize.min.htc);
behavior: url(backgroundsize.min.htc);
```
