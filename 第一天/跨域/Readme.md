<!--
 * @作者: gaowei
 * @页面: 
 * @最后修改人: gaowei
 * @Date: 2022-04-24 15:29:57
 * @LastEditTime: 2022-04-24 17:53:40
-->
## 跨域（CORS）

跨域又名“同源策略”，是一种基于http头的机制，这个机制标记了服务器除了本身以外的其他域（origin）使得浏览器能允许这些 origin 访问加载自己的资源。

跨域资源有什么用？
    1. 获取资源
    2. 资源授权
    3. 图形重绘

跨域又分为 简单请求和复杂请求

#### 简单请求
满足以下几个条件
1.  Method 为 Get , Head , Post 请求
2.  不允许设置除浏览器默认行为头之外的头数据，并且 contentType 的值限于 text/plain , mutipart/form-data , application/x-www-form-urlencoded
3.  请求中没有使用 ReadableStream

服务端处理

```js 
// Access-Control-Allow-Origin:* ; 
// 对于 request head 中的 origin 字段进行检索
```


#### 预检请求
与简单请求不同 预检请求在发起正式请求之前会发送一条 Options 请求，预检请求通过后即可允许跨域请求服务端资源

同时我们也要让服务端约定更多的请求头

```js
Access-Control-Allow-Origin:*; // 检查域的合法性
Access-Control-Allow-Method:Get,Post; // 检查请求方式的合法性
Access-Control-Allow-Headers:AuthHeader,Content-Type; // 检查头的合法性
```