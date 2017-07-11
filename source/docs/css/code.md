title: 代码规范
---

## 单行规则声明

对于*只包含一条声明*的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。

这样做的关键因素是为了错误检测 -- 例如，CSS 校验器指出在 183 行有语法错误。如果是单行单条声明，你就不会忽略这个错误；如果是单行多条声明的话，你就要仔细分析避免漏掉错误了。

``` css
/* 推荐 */
.jdc {
  display: block;
  width: 50px;
}

/* 不推荐 */
.jdc{ display: block;width: 50px;}
```

## 代码大小写

样式选择器，属性名，属性值关键字全部使用小写字母书写，属性字符串允许使用大小写。

```css
/* 推荐 */
.jdc{
  display: block;
}

/* 不推荐 */
.JDC{
  DISPLAY: BLOCK;
}
```

## 选择器

* 尽量少用通用选择器 `*`
* 不使用无具体语义定义的标签选择器
* 对于通用元素使用 class ，这样利于渲染性能的优化。
* 对于经常出现的组件，避免使用属性选择器（例如，`[class^="..."]`）。浏览器的性能会受到这些因素的影响。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 **3** 。
* **只有**在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。

```css
/* 推荐 */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }

/* 不推荐 */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
```

## 合理的避免使用ID

一般情况下ID不应该被应用于样式。ID的样式不能被复用并且每个页面中只能使用一次ID。你应该始终考虑使用class，而不是id，除非只使用一次。

```css
/* 推荐 */
.content .title {
  font-size: 2em;
}

/* 不推荐 */
#content .title {
  font-size: 2em;
}
```

## class 命名

* class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，`.btn` 和 `.btn-danger`）。
* 避免过度任意的简写。`.btn` 代表 button，但是 `.s` 不能表达任何意思。
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 使用 `.js-*` class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。

```css
/* 推荐 */
.tweet { ... }
.important { ... }
.tweet-header { ... }

/* 不推荐 */
.t { ... }
.red { ... }
.header { ... }
```

## 媒体查询（`Media query`）的位置

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

## 代码缩进

统一使用两个空格进行代码缩进，使得各编辑器表现一致（各编辑器有相关配置）

```css
.jdc {
  width: 100%;
  height: 100%;
}
```

## 分号

每个属性声明末尾都要加分号；

```css
.jdc {
  width: 100%;
  height: 100%;
}
```

## 代码易读性

左括号与类名之间一个空格，冒号与属性值之间一个空格

```css
/* 推荐 */
.jdc {
  width: 100%;
}

/* 不推荐 */
.jdc{
  width:100%;
}
```


逗号分隔的取值，逗号之后一个空格

```css
/* 推荐 */
.jdc {
  box-shadow: 1px 1px 1px #333, 2px 2px 2px #ccc;
}

/* 不推荐 */
.jdc {
  box-shadow: 1px 1px 1px #333,2px 2px 2px #ccc;
}
```

为单个css选择器或新申明开启新行

```css
/* 推荐 */
.jdc,
.jdc-logo,
.jdc-hd {
  color: #ff0;
}
.nav{
  color: #fff;
}

/* 不推荐 */
.jdc,jdc-logo,.jdc-hd {
  color: #ff0;
}.nav{
  color: #fff;
}
```

颜色值 `rgb()` `rgba()` `hsl()` `hsla()` `rect()` 中不需有空格，且取值不要带有不必要的 0


``` css
/* 推荐 */
.jdc {
  color: rgba(255,255,255,.5);
}

/* 不推荐 */
.jdc {
  color: rgba( 255, 255, 255, 0.5 );
}
```

属性值十六进制数值能用简写的尽量用简写


```css
/* 推荐 */
.jdc {
  color: #fff;
}

/* 不推荐 */
.jdc {
  color: #ffffff;
}
```

不要为 `0` 指明单位

```css
/* 推荐 */
.jdc {
  margin: 0 10px;
}

/* 不推荐 */
.jdc {
  margin: 0px 10px;
}
```

## 属性值引号

css属性值需要用到引号时，统一使用单引号

```css
/* 推荐 */
.jdc {
  font-family: 'Hiragino Sans GB';
}

/* 不推荐 */
.jdc {
  font-family: "Hiragino Sans GB";
}
```

## 属性书写顺序

建议遵循以下顺序：

1. 布局定位属性：display / position / float / clear  / visibility / overflow
2. 自身属性：width / height / margin / padding / border / background
3. 文本属性：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. 其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient ...

```css
.jdc {
  display: block;
  position: relative;
  float: left;
  width: 100px;
  height: 100px;
  margin: 0 10px;
  padding: 20px 0;
  font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
  color: #333;
  background: rgba(0,0,0,.5);
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -o-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```


[mozilla官方属性顺序推荐](https://www.mozilla.org/css/base/content.css)

## CSS3浏览器私有前缀写法

CSS3 浏览器私有前缀在前，标准前缀在后

```css
.jdc {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -o-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```
更多关于浏览器私有前辍写法：[#Vendor-specific extensions](http://www.w3.org/TR/2011/REC-CSS2-20110607/syndata.html#vendor-keywords)
