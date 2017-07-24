# Node.system MQTT客户端组件

## 简介
MQTT客户端组件是一个封装了MQTT的相关操作的组件，通过这个组件我们可以实现MQTT的订阅和推送
``` js
var mqtt = require("mqtt");
```

## 建立连接
通过mqtt.connect方法，我们可以发起一个mqtt连接并返回一个client对象。注意，connect方法是异步方法，返回client并不代表连接成功。若连接成功将通知该client的事件函数。
``` js
var client = mqtt.connect("your.server", 1883);
```
若需要指定用户名、密码、ID，可以使用
``` js
var option_data = {
    "id" : "your_id",
    "username" : "your_username",
    "password" : "your_password="
};
var client = mqtt.connect("your.server", 1883, option_data);
```
通过client.onConnect方法注册连接事件
``` js
client.onConnect(function(result){
    if (!result) {
        print("[CONNECT] connect failed");
        return;
    }
    print("CONNECT OK");
    do_some_thing_else...
});
```
## 消息订阅和推送
订阅与推送建议在client.onConnect所注册的事件中进行。若连接成功才使订阅和推送功能
``` js
client.onConnect(function(result){
    if (!result) {
        print("[CONNECT] connect failed");
        return;
    }
    client.subscribe("message");
    var val = 0;
    setInterval(function(){ 
        client.publish("counter", Buffer(val.toString()));
        val++;
    }, 1000);
});
```
获取订阅的消息推送，需要注册onMessage事件
``` js
client.onMessage(function(topic, message){
    print("[MESSAGE] " + topic + ": " + message);
});
```
