# 湿度传感器

使用湿度传感器库

```js
var mag7 = require("mag7");
var pm = require("potentiometer");
```

打开设备

```js
var p = pm.open(mag7.A1);
```

读取湿度值

```js
var value = p.read();
```

关闭设备

```js
p.close();
```



