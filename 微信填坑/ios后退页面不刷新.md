# 1.需要引入jquery

```bash
$(function () { 
  var isPageHide = false;
  window.addEventListener('pageshow', function () { 
    if (isPageHide) { 
      window.location.reload(); 
    } 
  })
  window.addEventListener('pagehide', function () { 
    isPageHide = true; 
  })
})
```

## 通过监听pageshow事件刷新页面
```bash
window.onpageshow = function(event) {
 if (event.persisted) {
   window.location.reload()
 }
}
```