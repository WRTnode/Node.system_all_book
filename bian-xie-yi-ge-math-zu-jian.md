# Node.system 组件开发/编写一个math组件

提供一个math的入口函数，在require时被调用
``` c
jerry_value_t zjs_math_init() {
    jerry_value_t math = jerry_create_object(); // 创建一个js对象
    zjs_obj_add_function(math, zjs_math_add, "add");    //这个math对象添加add方法
    zjs_obj_add_function(math, zjs_math_sub, "sub");    //这个math对象添加sub方法
    zjs_obj_add_function(math, zjs_math_mul, "mul");    //这个math对象添加mul方法
    zjs_obj_add_function(math, zjs_math_div, "div");    //这个math对象添加div方法
    zjs_obj_add_function(math, zjs_math_pow, "pow");    //这个math对象添加pow方法
    return math; // 将这个对象返回出去
}
```
接下来就需要实现zjs_math_add、zjs_math_sub、zjs_math_mul、zjs_math_div、zjs_math_pow函数。这些函数是直接有jerryscript引擎调用的，原型规定如下
``` c
typedef jerry_value_t (*jerry_external_handler_t) (const jerry_value_t function_obj,
                                               const jerry_value_t this_val,
                                               const jerry_value_t args_p[],
                                               const jerry_length_t args_count);
```
以实现zjs_math_add为例
``` c
static jerry_value_t zjs_math_add(const jerry_value_t function_obj,
                                    const jerry_value_t this,
                                    const jerry_value_t argv[],
                                    const jerry_length_t argc)
{
    if (argc != 2 || !jerry_value_is_number(argv[0]) || !jerry_value_is_number(argv[1]))
        return ZJS_ERROR_INVALID_ARG(); //若不满足参数个数为2且参数均为number型，返回参数错误
    double a = jerry_get_number_value(argv[0]); // 获取参数1的值
    double b = jerry_get_number_value(argv[1]); // 获取参数2的值
    return jerry_create_number(a + b); // 将参数1和参数2的值相加，并用结果创建一个js变量返回出去
}
```
zjs_math_sub、zjs_math_mul、zjs_math_div、zjs_math_pow的实现类似。
最后我们还要提供"math"字符串和zjs_math_init函数的对应关系。在zjs_modules.h中zjs_modules_array中添加一项
``` c
module_t zjs_modules_array[] = {
    ...
    ...
    ...
    {"math", zjs_math_init}
};
```
在js代码中，我们可以这样调用
``` js
var math = require("math");
print("1+2=" + math.add(1, 2));
print("1-2=" + math.sub(1, 2));
print("1*2=" + math.mul(1, 2));
print("1/2=" + math.div(1, 2));
```
