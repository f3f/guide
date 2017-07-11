title: 一般规范
---

## 文件/资源命名

在 web 项目中，所有的文件名应该都遵循同一命名约定。以可读性而言，减号（-）是用来分隔文件名的不二之选。同时它也是常见的 URL 分隔符（i.e. //example.com/blog/my-blog-entry or  //s.example.com/images/big-black-background.jpg），所以理所当然的，减号应该也是用来分隔资源名称的好选择。

请确保文件命名总是以字母开头而不是数字。而以特殊字符开头命名的文件，一般都有特殊的含义与用处（比如eslint的配置文件 `.eslintrc.json` ）。

资源的字母名称必须全为小写，这是因为在某些对大小写字母敏感的操作系统中，当文件通过工具压缩混淆后，或者人为修改过后，大小写不同而导致引用文件不同的错误，很难被发现。

还有一些情况下，需要对文件增加前后缀或特定的扩展名（比如 .min.js, .min.css），抑或一串前缀（比如 3fa89b.main.min.css）。这种情况下，建议使用点分隔符来区分这些在文件名中带有清晰意义的元数据。

``` html
// 不推荐
MyScript.js
myCamelCaseName.css
i_love_underscores.html
1001-scripts.js
my-file-min.css

// 推荐
my-script.js
my-camel-case-name.css
i-love-underscores.html
thousand-and-one-scripts.js
my-file.min.css
```

## 协议

> 不要指定引入资源所带的具体协议。

当引入图片或其他媒体文件，还有样式和脚本时，URLs 所指向的具体路径，不要指定协议部分（http:, https:），除非这两者协议都不可用。

不指定协议使得 URL 从绝对的获取路径转变为相对的，在请求资源协议无法确定时非常好用，而且还能为文件大小节省几个字节。



``` html
// 不推荐
<script src="http://cdn.com/foundation.min.js"></script>
// 推荐
<script src="//cdn.com/foundation.min.js"></script>
```
``` css
// 不推荐
.example {
  background: url(http://static.example.com/images/bg.jpg);
}
// 推荐
.example {
  background: url(//static.example.com/images/bg.jpg);
}
```

## 文本缩进

一次缩进两个空格
``` html
<ul>
  <li>Fantastic</li>
  <li>Great</li>
  <li>
    <a href="#">Test</a>
  </li>
</ul>
```
``` css
@media screen and (min-width: 1100px) {
  body {
    font-size: 100%;
  }
}
```
``` javascript
(function(){
  var x = 10;

  function y(a, b) {
    return {
      result: (a + b) * x
    }
  }
}());
```

## 注释

注释是你自己与你的小伙伴们了解代码写法和目的的唯一途径。特别是在写一些看似琐碎的无关紧要的代码时，由于记忆点不深刻，注释就变得尤为重要了。

当你写注释时一定要注意：不要写你的代码都干了些什么，而要写你的代码为什么要这么写，背后的考量是什么。当然也可以加入所思考问题或是解决方案的链接地址。

## 编辑器配置
将你的编辑器按照下面的配置进行设置，以避免常见的代码不一致和差异：

* 用两个空格代替制表符（soft-tab 即用空格代表 tab 符）。
* 保存文件时，删除尾部的空白符。
* 设置文件编码为 UTF-8。
* 在文件结尾添加一个空白行。

参照文档并将这些配置信息添加到项目的 `.editorconfig` 文件中。例如：[Bootstrap 中的 .editorconfig 实例](https://github.com/twbs/bootstrap/blob/master/.editorconfig)。更多信息请参考 [about EditorConfig](http://editorconfig.org)。




