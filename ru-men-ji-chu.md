# Node.system 组件开发入门基础

要使用一个组件，我们需要require这个组件名来得到这个组件对象
``` js
var xxx = require("xxx");
```
在我们调用require的时候，实际上是去调用了该模块的入口函数，入口函数负责构造math对象并返回。
``` c
jerry_value_t zjs_xxx_init() {
    jerry_value_t xxx = jerry_create_object(); // 创建一个js对象
    return xxx; // 将这个对象返回出去
}
```
在调用require时传递了一个"xxx"的参数，require需要通过"xxx"这个字符串来查找到zjs_xxx_init这个函数，所以我们还要提供"xxx"字符串和zjs_xxx_init函数的对应关系。在zjs_modules.h中zjs_modules_array中添加一项
``` c
module_t zjs_modules_array[] = {
    ...
    ...
    ...
    {"xxx", zjs_xxx_init}
};
```
这个时候我们完成一个最简单的组件开发了，但是xxx这个组件并没有任何实际作用，因为我没有赋予xxx任何实际有用的方法。
