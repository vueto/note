在ie浏览器下，下载apk文件，会被转化为zip这是因为apk文件本身就是zip文件，在ie下被转换为zip文件。

解决办法：
1.在后台需要在源服务器 指定APK文件的MIME类型为 application/vnd.android.package-archive 

2.在前端的a标签中 设置type="application/vnd.android.package-archive"