# meta标签的各种用途

## viewport(视口)

### safari在网页加载时隐藏地址栏与导航栏

```html
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no, minimal-ui">
```

最后的minimal-ui属性可以让safari在网页加载时隐藏地址栏与导航栏(仅支持ios7.1以上)