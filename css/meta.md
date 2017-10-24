# meta标签的各种用途

```html

<!-- 是否删除默认的苹果工具栏和菜单栏 -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- 其他的meta设置 -->
<!-- 启用360浏览器的极速模式(webkit) -->
<meta name="renderer" content="webkit">

<!-- 避免IE使用兼容模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">

<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">

<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">

<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">

<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">

<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">

<!-- UC应用模式 -->
<meta name="browsermode" content="application">

<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">

<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">



```

## viewport(视口)

### safari在网页加载时隐藏地址栏与导航栏

```html
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no, minimal-ui">
```

最后的minimal-ui属性可以让safari在网页加载时隐藏地址栏与导航栏(仅支持ios7.1以上)

### 删除默认苹果工具栏和菜单栏

```html
<meta name="apple-mobile-web-app-capable" content="yes" />
```

这meta的作用就是删除默认的苹果工具栏和菜单栏。content有两个值”yes”和”no”,当我们需要显示工具栏和菜单栏时，这个行meta就不用加了，默认就是显示。

### safari状态栏显示样式

```html

    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

```

在web app应用下状态条（屏幕顶部条）的颜色；

默认值为default（白色），可以定为black（黑色）和black-translucent（灰色半透明）

若值为“black-translucent”将会占据页面px位置，浮在页面上方（会覆盖页面20px高度–iphone4和itouch4的Retina屏幕为40px）


### 禁止识别数字当作电话或者邮箱

```html

<meta name="format-detection" content ="telephone=no"/>  

```

格式检测 禁止识别我们页面中的数字，防止把其当作电话识别，`email=no` 禁止识别邮箱

### uc强制全屏

```html

<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">

```

### QQ强制全屏

```html

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">

```