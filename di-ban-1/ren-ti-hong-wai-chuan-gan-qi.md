# 人体红外传感器

使用人体红外传感器库

```js
var mag7 = require("mag7");
var hb = require("humanbody");
```

打开设备并设置回调函数

```js
var h = hb.open(mag7, function(){
   print("Detect human"); 
});
```

关闭设备

```js
h.close();
```



