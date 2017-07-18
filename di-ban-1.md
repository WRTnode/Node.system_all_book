# MT7697底板1，板载外设说明

## RGBLED (彩灯)
板载的RGBLED可以通过rgbled模块进行控制。
```js
var rgbled = require("rgbled");
```
通过set方法设置R、G、B分量值，如
```js
rgbled.set(255, 0, 0); // 红色
rgbled.set(255, 255, 0); // 红色+绿色=黄色
```

## SWITCH (开关)
板载两个开关KEY1和KEY2。可以通过设置外部中断的方式来设置事件函数。需要用到pinmux和extint两个模块。pinmux用做配置引脚复用，extint用做配置外部中断。
```js
var pinmux = require("pinmux");
var extint = require("extint");
```
以KEY1为例，KEY1开关通过下拉的方式连接到GPIO37上。首先将GPIO37配置成中断输入模式
```js
var pinno = 37;
pinmux.set(pinno, 3); // 模式3为中断输入模式
```
配置中断模式，按键在抬起状态GPIO37上为低电平，按下状态GPIO37上为高电平。所以设置为上升沿触发
```js
var eno = extint.pin2eint(pinno);   // 通过引脚号查询对应的外部中断号
extint.init(eno, "rise_edge", 10);  // 上升沿触发，消抖时间为10毫秒
var handler = extint.register(eno, function(){
    print("KEY1 DOWN");
});                                 // 注册中断响应函数，但按钮按下时，打印 "KEY1 DOWN"
                                    // handler为该事件的控制器
```
若需要取消该事件函数，则使用
```js
handler.kill();
```

## MOTOR (电机)
板载的电机通过两个引脚GPIO29, GPIO30控制其正转和反转
| GPIO29| GPIO30|  转向  |
|:-----:|:-----:|:------:|
|   0   |   0   |  停止  |
|   1   |   0   |  正转  |
|   0   |   1   |  反转  |
|   1   |   1   |  停止  |
为了控制电机，需要使用pinmux和gpio模块
```js
var pinmux = require("pinmux");
var gpio = require("gpio");
```
配置引脚
```js
pinmux.set(29, 8);      // 将GPIO29引脚配置为普通IO口模式
pinmux.set(30, 8);      // 将GPIO30引脚配置为普通IO口模式
var m1 = gpio.open(29); // 打开GPIO29引脚，获得引脚对象
var m2 = gpio.open(30); // 打开GPIO30引脚，获得引脚对象
m1.direction("out");    // 配置为输出
m2.direction("out");    // 配置为输出
m1.pull("down");        // 配置为下拉
m2.pull("down");        // 配置为下拉
```
设置为正转
```js
m1.write(true);         // GPIO29拉高
m2.write(false);        // GPIO30拉低
```
