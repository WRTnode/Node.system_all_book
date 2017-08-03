# 开关

使用开关库

```js
var mag7 = require("mag7");
var sw = require("switch");
```

打开设备

```js
var s = sw.open(mag7.D1);
```

读取开关值，该值只能为true和false

```js
var value = s.read();
```

关闭设备

```js
h.close();
```



