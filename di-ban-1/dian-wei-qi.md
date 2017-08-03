# 电位器

使用电位器库

```js
var mag7 = require("mag7");
var pm = require("potentiometer");
```

打开设备

```js
var p = pm.open(mag7.A1);
```

读取电位器值

```js
var value = p.read();
```

关闭设备

```js
p.close();
```



