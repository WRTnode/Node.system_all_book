# REGLED使用说明

在使用regled之前你需要require它

```js
var regled= require('regled');
```

## regled.set

### 说明

设置引脚复用

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| R分量 | number | 必须 | 红色值，0-255 |
| G分量 | number | 必须 | 绿色值，0-255 |
| B分量 | number | 必须 | 蓝色值，0-255 |

### 返回值

如果成功返回true，失败返回false

