# 湿度传感器

使用湿度传感器库

```js
var mag7 = require("mag7");
var hd= require("humidity");
```

打开设备

```js
var h = hd.open(mag7.A1);
```

读取湿度值

```js
var value = h.read();
```

关闭设备

```js
h.close();
```



