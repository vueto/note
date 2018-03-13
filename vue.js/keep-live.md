# keep-alive的用法

## 1.基本用法

vue2.0提供了一个keep-alive组件

用来缓存组件,避免多次加载相应的组件,减少性能消耗

```html
<keep-alive>
    <component>
  <!-- 组件将被缓存 -->
    </component>
</keep-alive>

```

有时候 可能需要缓存整个站点的所有页面,而页面一般一进去都要触发请求的
在使用`keep-alive`的情况下

```html

<keep-alive>
    <router-view></router-view>
</keep-alive>

```

将首次触发请求写在`created`钩子函数中,就能实现缓存,
比如列表页,去了详情页 回来,还是在原来的页面

## 2.缓存部分页面或者组件

(1) 使用router. meta属性

```html

// 这是目前用的比较多的方式
<keep-alive>
    <router-view v-if="$route.meta.keepAlive"></router-view>
</keep-alive>
<router-view v-if="!$route.meta.keepAlive"></router-view>

```

`router设置`

```bash
... 
  routes: [
    { path: '/', redirect: '/index',  component: Index, meta: { keepAlive: true }},
    {
      path: '/common',
      component: TestParent,
      children: [
        { path: '/test2', component: Test2, meta: { keepAlive: true } } 
      ]
    }
    ....
    // 表示index和test2都使用keep-alive
```

(2) 使用新增属性inlcude/exclude

2.1.0后提供了`include/exclude`两个属性 可以针对性缓存相应的组件

```html
<!-- comma-delimited string -->
<keep-alive include="a,b">
  <component :is="view"></component>
</keep-alive>
<!-- regex (use v-bind) -->
<keep-alive :include="/a|b/">
  <component :is="view"></component>
</keep-alive>

//其中a,b是组件的name
```

注意:这种方法都是预先知道组件的名称的

(2) 动态判断

```html
<keep-alive :include="includedComponents">
  <router-view></router-view>
</keep-alive
```

`includedComponents`动态设置即可