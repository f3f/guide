title: Html 浏览器兼容处理
---

## 浏览器的渲染模式
浏览器的渲染模式，建议引入：
```
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
```

## 低版本浏览器提示通用代码
```
$(function() {

    //判断浏览器是否是IE9以下
    var ua = (navigator.appName == "Microsoft Internet Explorer" && navigator.appVersion.split(";")[1].replace(/[ ]/g, "") == "MSIE6.0" ||
    navigator.appName == "Microsoft Internet Explorer" && navigator.appVersion.split(";")[1].replace(/[ ]/g, "") == "MSIE7.0" ||
    navigator.appName == "Microsoft Internet Explorer" && navigator.appVersion.split(";")[1].replace(/[ ]/g, "") == "MSIE8.0");

    var html = '<div class="ieTips">' +
        '<div class="fl">' +
            '<span class="fl prompt-txt"> 你的浏览器版本过低，可能导致网站不能正常访问！为了你能正常使用网站功能，请使用这些浏览器：</span>' +
            '<ul class="fl ieTips-icon-lists">' +
                '<li>' +
                    '<a href="http://sw.bos.baidu.com/sw-search-sp/software/bf7b887437715/IE10-Windows6.1-zh-cn.exe">' +
                        '<i class="ieTips-icon ieTips-iconfont ieTips-icon-ie"></i> <span class="name">IE10及以上浏览器</span> </a>' +
                '</li>' +
                '<li>' +
                    '<a href="http://sw.bos.baidu.com/sw-search-sp/software/9c6abe90486d4/Firefox_49.0.2.6136_setup.exe">' +
                        '<i class="ieTips-icon ieTips-iconfont ieTips-icon-huohu"></i> <span class="name">火狐浏览器</span> </a>' +
                '</li>' +
                '<li>' +
                    '<a href="http://sw.bos.baidu.com/sw-search-sp/software/66c03028c72ca/ChromeStandalone_54.0.2840.87_Setup.exe">' +
                        '<i class="ieTips-icon ieTips-iconfont ieTips-icon-guge"></i><span class="name">谷歌浏览器</span> </a>' +
                '</li>' +
            '</ul>' +
        '</div>' +
            '<div class="fr prompt-btn">' +
                '<button type="button" class="iet-btn no_prompt">不再提示</button> ' +
                //'<button type="button" class="iet-btn close_prompt">关闭提示</button> ' +
            '</div>' +
        '</div>';

    if(getCookie('test')==false){
        //$(".ieTips").hide();
        if (ua){
            //$(".ieTips").show();
            $("body").append(html);
        }
    }

    $(".no_prompt").click(function(){
        setCookie("test","tank",3600); //cookie失效时间 3600秒=1小时
        $(this).parents(".ieTips").slideUp();
    });

    $(".close_prompt").on("click", function () {
        $(this).parents(".ieTips").slideUp();
    });

});

//取得cookie
function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');    //把cookie分割成组
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];                      //取得字符串
        while (c.charAt(0)==' ') {          //判断一下字符串有没有前导空格
            c = c.substring(1,c.length);      //有的话，从第二位开始取
        }
        if (c.indexOf(nameEQ) == 0) {       //如果含有我们要的name
            return unescape(c.substring(nameEQ.length,c.length));    //解码并截取我们要值
        }
    }
    return false;
}

//清除cookie
function clearCookie(name) {
    setCookie(name, "", -1);
}

//设置cookie
function setCookie(name, value, seconds) {
    seconds = seconds || 0;   //seconds有值就直接赋值，没有为0。
    var expires = "";
    if (seconds != 0 ) {      //设置cookie生存时间
        var date = new Date();
        date.setTime(date.getTime()+(seconds*1000));
        expires = "; expires="+date.toGMTString();
    }
    document.cookie = name+"="+escape(value)+expires+"; path=/";   //转码并赋值
}

```
