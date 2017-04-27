# GPIO使用说明

再使用GPIO之前你需要require它

```js
var gpio = require('gpio');
```

## 

## gpio.open

### 说明

打开一个引脚，获得`pinobj`，通过该`pinobj`控制引脚读写

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| 引脚号 | number | 必须 | 无 |

### 返回值

如果成功返回引脚对象`pinobj`，否则返回false

## 

## pinobj.pinnum

### 说明

获取该pinobj对象的引脚号

### 参数

无

### 返回值

该pinobj对象的引脚号

## 

## pinobj.read

### 说明

从引脚上读电平信号，在此之前请注意用[pinobj.direction\('in'\)](#pinobjdirection)设置引脚为输入模式

### 参数

无

### 返回值

如果引脚为高电平返回true，如果为低电平返回false，如果读取失败返回Undefined

## 

## pinobj.write

### 说明

通过引脚写电平信号，在此之前请注意用[pinobj.direction\('out'\)](#pinobjdirection)设置引脚为输出模式

### 参数

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| 电平值 | boolean | 必须 | 高电平true，低电平false |

### 返回值

成功返回true，失败返回false

## 

## pinobj.pull

### 说明

设置内部上拉/下拉

### 参数

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| 模式 | string | 必须 | 'up'、'down' 或者 'none' |

### 返回值

成功返回true, 失败返回false

## 

## pinobj.direction

### 说明

设置I/O方向

### 参数

| 参数名 | 类型 | 可选/必须 | 说明 |
| :--- | :--- | :--- | :--- |
| 方向 | string | 必须 | 'in' 或者 'out' |

### 返回值

成功返回true, 失败返回false

