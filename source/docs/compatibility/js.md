title: JS 浏览器兼容处理
---

## ES5
低版本浏览器兼容 ES5 的一些属性、方法，引入：
```
<script src="//cdn.bootcss.com/es5-shim/4.5.9/es5-shim.min.js"></script>
<script src="//cdn.bootcss.com/es5-shim/4.5.9/es5-sham.min.js"></script>
```

## ajax请求参数
在低版本浏览器中，ajax get 请求参数含有中文字符转码后字符太长，后端获取不到参数，可改用 post；

## echarts
图表插件 echarts，在低版本浏览器中报 js 错误(fiflter 未定义…)，可以通过引入es5-array.js 插件解决；

## 跨域
ajax 在 ie8，ie9 下不能跨域，引入 jquery.xdomainrequest.min.js 解决；
```
<script src="cdn.bootcss.com/jquery-ajaxtransport-xdomainrequest/1.0.4/jquery.xdomainrequest.min.js"></script>
```

## 键盘事件
ie8 浏览器下不识别键盘事件中的 event.which ，用 event.which||event.keyCode；

## placeholder
文本框的 placeholder 在 ie8 之下失效，可以通过引入 placeholder.js 来解决；
```
<script src="cdn.bootcss.com/placeholders/4.0.1/placeholders.jquery.min.js"></script>
```

## 其它
1. jquery 版本选择低于 2.0
2. ajax 请求，中文编码问题（encodeUrl）
