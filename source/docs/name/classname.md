title: ClassName命名
---


ClassName的命名应该尽量精短、明确，必须以**字母开头命名**，且**全部字母为小写**，单词之间**统一使用破折号** “-” 连接

## 命名原则

基于姓氏命名法（继承 + 外来），祖先模块不能出现破折号，除了是全站公用模块，如 `mod-` 系列的命名：

**推荐：**

```html
<div class="modulename">
  <div class="modulename-info">
    <div class="modulename-son"></div>
    <div class="modulename-son"></div>
    ...
  </div>
</div>

<!-- 这个是全站公用模块，祖先模块允许直接出现破折号 -->
<div class="mod-info">
  <div class="mod-info-son"></div>
  <div class="mod-info-son"></div>
  ...
</div>
```

**不推荐：**

```html
<div class="modulename-info">
  <div class="modulename-info-son"></div>
  <div class="modulename-info-son"></div>
  ...
</div>
```

在子孙模块数量可预测的情况下，严格继承祖先模块的命名前缀

```html
<div class="modulename">
  <div class="modulename-cover"></div>
  <div class="modulename-info"></div>
</div>
```

当子孙模块超过4级或以上的时候，可以考虑在祖先模块内具有识辨性的独立缩写作为新的子孙模块

**推荐：**

```html
<div class="modulename">
  <div class="modulename-cover"></div>
  <div class="modulename-info">
      <div class="modulename-info-user">
        <div class="modulename-info-user-img">
          <img src="" alt="">
          <!-- 这个时候 miui 为 modulename-info-user-img 首字母缩写-->
          <div class="miui-tit"></div>
          <div class="miui-txt"></div>
          ...
        </div>
      </div>
      <div class="modulename-info-list"></div>
  </div>
</div>
```

**不推荐：**

```html
<div class="modulename">
  <div class="modulename-cover"></div>
  <div class="modulename-info">
      <div class="modulename-info-user">
        <div class="modulename-info-user-img">
          <img src="" alt="">
          <div class="modulename-info-user-img-tit"></div>
          <div class="modulename-info-user-img-txt"></div>
          ...
        </div>
      </div>
      <div class="modulename-info-list"></div>
  </div>
</div>
```

## 模块命名

全站公共模块：以 `mod-` 开头

```html
<div class="mod-yours"></div>
```

业务公共模块：以 `业务名-mod-` 开头

```html
<div class="paipai-mod-yours"></div>
```

## 常用命名推荐

**注意**：ad、banner、gg、guanggao 等有机会和广告挂勾的字眼不建议直接用来做ClassName，因为有些浏览器插件（Chrome的广告拦截插件等）会直接过滤这些类名，因此

```html
<div class="ad"></div>
```

这种广告的英文或拼音类名不应该出现

另外，**敏感不和谐字眼**也不应该出现，如：

``` html
<div class="fuck"></div>
<div class="jer"></div>
<div class="sm"></div>
<div class="gcd"></div>
<div class="ass"></div>
<div class="KMT"></div>
...
```


| ClassName | 含义 |
| ------------ | ------------- |
| header | 头部 |
| nav | 页面主导航 |
| left-bar | 左侧导航 |
| logo | 网站logo |
| footer | 底部 |
| main | 页面主内容区 |
| left-\*\*\*、top-\*\*\* | 页面布局位置相关 |
| \*\*\*-wrap | 页面区块 |
| \*\*\*-content | 内容区块 |
| item | 子项目 |
| menu | 菜单 |
| breadcrumb | 面包屑 |
| table | 表格 |
| title | 标题 |
| list | 列表 |
| tab | 页签 |
| chart | 图表容器 |
| pic | 图片容器 |
| icon | 图标 |
| back | 返回 |
| btn、btn-\*\*\* | 按钮 |
| mask | 遮罩 |
| pop | 弹窗 |
| search | 搜索 |
| tips | 页面提示信息 |
| date/time | 日期/时间 |
| fl/fr | 浮动 |
| clearfix | 清除浮动 |
| tl/tr/tc | 文本对齐 |
| active | 激活状态 |
| about | 关于 |
| article | 文章 |
| avatar | 头像 |
| tools | 工具 |
| category | 分类 |
| chart | 图表 |
| close | 关闭 |
| comment | 评论 |
| copyright | 版权 |
| default | 默认 |
| description | 描述 |
| details | 细节 |
| disabled | 不可用 |
| error | 错误 |
| even | 偶数，常用于多行列表或表格中 |
| fail | 失败（提示） |
| feature | 专题 |
| fewer | 收起 |
| filter | 筛选 |
| first | 第一个，常用于列表中 |
| forum | 论坛 |
| banner | 广告图 |
| gallery | 画廊 |
| help | 帮助 |
| hide | 隐藏 |
| home | 主页 |
| info,information | 信息 |
| last | 最后一个，常用于列表中 |
| links | 链接 |
| login | 登录 |
| logout | 退出 |
| more | 更多（展开） |
| msg | 消息 |
| next | 下一页 |
| on | 鼠标移过 |
| pagination | 分页 |
| preview | 预览 |
| previous | 上一页 |
| primary | 主要 |
| progress | 进度条 |
| recommend | 推荐 |
| reg,register | 注册 |
| save | 保存 |
| secondary | 次要 |
| section | 区块 |
| selected | 已选 |
| share | 分享 |
| show | 显示 |
| slide | 幻灯片，图片切换 |
| sort | 排序 |
| sub | 次级的，子级的 |
| submit | 提交 |
| subtitle | 副标题 |
| success | 成功（提示） |
| summary | 摘要 |
| txt,text | 文本 |
| thumbnail | 缩略图 |
| video | 视频 |


