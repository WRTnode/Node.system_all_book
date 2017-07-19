# Node.system Wifi系统组件

## 简介

Wifi系统组件是一套管理WIFI的组件，通过本组件可以实现对板载WIFI设备的管理。例如接入点的设置、客户端的设置，以及获取连接状态、信号强度等wifi的基本属性。

```js
var wifi = require("wifi");
```

方法：connect

```js
wifi.connect("ssid", "password");
```
参数说明：

参数1：欲连接的Wifi介入点的名字
参数2：Wifi接入点的密码，如无密码留空即可。

