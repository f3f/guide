title: JS 浏览器兼容处理
---

## ES5
低版本浏览器兼容 ES5 的一些属性、方法，引入：
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/es5-shim/4.5.9/es5-shim.min.js"></script>
  <script src="//cdn.bootcss.com/es5-shim/4.5.9/es5-sham.min.js"></script>
<![endif]-->
```

## ajax请求参数
在低版本浏览器中，ajax get 请求参数含有中文字符转码后字符太长，后端获取不到参数，可改用 post；

## echarts
图表插件 echarts，在低版本浏览器中报 js 错误(fiflter 未定义…)，可以通过引入es5-array.js 插件解决；

## 跨域
ajax 在 ie8，ie9 下不能跨域，引入 jquery.xdomainrequest.min.js 解决；
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/jquery-ajaxtransport-xdomainrequest/1.0.4/jquery.xdomainrequest.min.js"></script>
<![endif]-->
```

## ie8,9 进行跨域post请求，参数无法传递解决办法
jquery的ajax方法添加 crossDomain: true == !(document.all) 例如：
```javascript
$.ajax({
    url: url,
    type: 'POST',
    data: params,
    dataType: 'json',
    contentType: "application/json",
    crossDomain: true == !(document.all),
    success: function (res) {
      ...
    },
    error: function (err) {
      ...
    }
})
```

## IE跨域下出现{"readyState":0,"status":0,"TypeError"...}
对浏览器进行设置 工具->Internet选项->安全->自定义级别->其他->通过域访问数据源->启用

## 键盘事件
ie8 浏览器下不识别键盘事件中的 event.which ，用 event.which||event.keyCode；

## input的placeholder
文本框的 placeholder 在 ie8 之下失效，可以通过引入 placeholder.js 来解决；
```
<!--[if lt IE 9]>
  <script src="//cdn.bootcss.com/placeholders/4.0.1/placeholders.jquery.min.js"></script>
<![endif]-->
```

## 兼容IE8不直接使用sessionStorage,localStorage
使用公用方法，使用办法如下：
```javascript
function setKeyItem(key,value) {
    if (window.sessionStorage){
      sessionStorage.setItem(key,value);
    }else{
      setCookie(key,value,TimeoutCookie)
    }
}
```

## “JSON”未定义
引入json2.js <br/>
注：本模板已经引入 <br/>
下载地址：https://github.com/douglascrockford/JSON-js <br/>

## 其它
1. jquery 版本选择低于 2.0
2. ajax 请求，中文编码问题（encodeUrl）
