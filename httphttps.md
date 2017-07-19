# Node.system Http客户端组件

## 简介

Http客户端组件是一个封装了Http、Https的相关操作的组件，通过这个组件我们可以实现简单的http、https的请求，方便把板子的数据通过http api进行上报，或者执行某些操作。

```js
var http = require("http");
```

通过 request方法，我们可以实现对http的请求。

```js
http.request("http://example.com", /* 请求方法 1:GET 2:POST 可空，默认1 */,/* 可空 GET、或POST的参数 */);
```

