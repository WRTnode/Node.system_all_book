# GPIO使用说明

再使用GPIO之前你需要require它

```js
var pinmux= require('pinmux');
```

## pinmux.set

### 说明

设置引脚复用

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| 引脚号 | number | 必须 | 无 |
| 功能号 | number | 必须 | 无 |

### 返回值

如果成功返回true，失败返回false



