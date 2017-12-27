title: CSS 浏览器兼容处理
---

## IE浏览器hack
```
“-″减号是IE6专有的hack
“\9″ IE6/IE7/IE8/IE9/IE10都生效
“\0″ IE8/IE9/IE10都生效，是IE8/9/10的hack
“\9\0″ 只对IE9/IE10生效，是IE9/10的hack
.hack{
/*demo1 注意顺序，否则IE6/7下可能无法正确显示，导致结果显示为白色背景*/
    background-color:red; /* All browsers */
    background-color:blue !important;/* All browsers but IE6 */
    *background-color:black; /* IE6, IE7 */
    +background-color:yellow;/* IE6, IE7*/
    background-color:gray\9; /* IE6, IE7, IE8, IE9, IE10 */
    background-color:purple\0; /* IE8, IE9, IE10 */
    background-color:orange\9\0;/*IE9, IE10*/
    _background-color:green; /* Only works in IE6 */
    *+background-color:pink; /*  WARNING: Only works in IE7 ? Is it right? */
}
```

## Html5
低版本浏览器兼容 Html5 新标签，引入：
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script>
<![endif]-->
```
用于解决IE9以下版本浏览器对HTML5新增标签不识别，并导致CSS不起作用的问题。
原理：利用脚本document.createElement(“”)创建对应的脚本，CSS选择器便可正确应用到该标签。<br/>
注：此插件会对页面性能造成影响，所以如果项目开始阶段已经确定兼容IE9以下，就不建议使用html5新标签。


## Media Query
低版本浏览器无法识别 Media Query，引入：
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
<![endif]-->
```
Respond.js让不支持css3 Media Query的浏览器包括IE6-IE8等其他浏览器支持查询。<br/>
注：引入respond.min.js，但要在css的后面（越早引入越好，在ie下面看到页面闪屏的概率就越低，因为最初css会先渲染出来，如果respond.js加载得很后面，这时重新根据media query解析出来的css会再改变一次页面的布局等，所以看起来有闪屏的现象）

## CSS3 选择器
IE8 不支持 CSS3 选择器，可引入 selectivizr-min.js 解决 selectivizr-min.js
需要其它 js 库进行支持，不同 js 库对其支持程度不同，推荐使用 nwmatcher.js；
两者结合可满足 CSS3 绝大多数选择器：
```
<!--[if lt IE 9]>
  <script type="text/javascript" src="Lib/nwmatcher.js"></script>
  <script type="text/javascript" src="Lib/selectivizr-min.js"></script>
<![endif]-->
```
注：此插件会对页面性能造成影响，非必要情况下不建议使用。

## nth-child(even)
table 的隔行变色 用 nth-child(even)不兼容，可引入：
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/selectivizr/1.0.2/selectivizr-min.js"></script>
<![endif]-->
```

## IE6,IE7下overflow：hidden无效
解决办法：position:relative; 或者 position:relative; / for IE6,IE7 */ 即可解决该bug。
```css
position: relative;
overflow: hidden;
```

## 背景渐变linear-gradient
CSS 属性颜色渐变 linear-gradient，低版本浏览器不兼容，可使用 hack 技术添加一纯色背景
```css
background-color: #f5840c;
background: linear-gradient(top, #f5840c 0%,#f584cc 100%);
```

## 水平布局
inline-block下padding元素重叠，使用float: left替代display: inline-block实现水平布局；

## line-height
行内样式垂直居中问题，有时 line-height 和高度相等在 ie8 无效果，使用:
```css
height: 50px;
line-height: 50px;
vertical-align: middle;
```

## button左右两边留白
ie8 下 button 按钮左右两边留白的问题，用 :
```css
overflow: visible;
padding: 0;
```

## z-index
低版本浏览器 z-index 失效，给元素都添加:
```css
 position:relative
```

## background-size
让 ie7\ie8 支持 CSS3 background-size，引入 backgroundsize.min.htc，例子：
```css
body {
   height: 100%;
   margin: 0;
   background: url(images/126.jpg) center no-repeat;
   background-size: cover;
   -ms-behavior: url(backgroundsize.min.htc)\9;
   behavior: url(backgroundsize.min.htc)\9;
}
```

## 透明度兼容性：

a、使用rgba背景色做透明的：<br/>
背景色变成：background: #000; <br/>
再加IE9及以下的透明度设置方法
```
background: #000;
opacity=80;
-ms-filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=80);
filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=80);
```
b、直接使用opacity设置透明度的:<br/>
添加IE9及以下的透明度设置方法
```css
opacity=80
-ms-filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=80);
filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=80);
```
关于opacity引起里面文字透明，可以使用定位解决

## css伪类问题：
将用伪类实现的效果换成其他实现方式；<br/>
主要是针对IE7内核，如果不用兼容IE7内核，则不用处理此类问题。

## 伪类last-child
first-child是CSS2的内容，但是last-child就不是了，所以IE8不买账。<br/>
推荐的做法不是使用last-child，而是给最后一个元素设置一个.last的class，然后对此进行样式设置，这样就全部兼容了。


## filter blur

CSS3中提供支持滤镜效果的属性filter，比如支持高斯模糊效果：<br/>
```css
filter: blur(10px);
-webkit-filter: blur(10px);
-moz-filter: blur(10px);
```
IE8对filter: blur(10px)的显示效果是对HTML元素进行小范围的模糊处理，这个效果并不是高斯模糊<br/>
要想支持高斯模糊，需要如下设置：<br/>
```css
filter: progid:DXImageTransform.Microsoft.Blur(PixelRadius='10');
```
在实践中发现一个坑就是，所有position: relative的元素都不会生效。<br/>
其他的发现是，IE9对filter: blur(10px)无效，<br/>
而对filter: progid:DXImageTransform.Microsoft.Blur(PixelRadius='10'),是针对元素小范围的模糊效果。
