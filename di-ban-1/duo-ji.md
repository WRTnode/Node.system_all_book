# 舵机

使用舵机库

```js
var mag7 = require("mag7");
var sm = require("servomotor");
```

打开设备

```js
var m = sm.open(mag7.D1);
```

设置角度（-90到90）

```js
m.angle(45);
```

关闭设备

```js
m.close();
```



