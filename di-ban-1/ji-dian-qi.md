# 继电器

使用继电器库

```js
var mag7 = require("mag7");
var relay= require("relay");
```

打开设备

```js
var r = relay.open(mag7.D1);
```

设置继电器状态，状态值只能为true和false

```js
r.set(true);
```

关闭设备

```js
r.close();
```



