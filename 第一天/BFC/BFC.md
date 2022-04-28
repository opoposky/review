
## 什么是 BFC ( block formatting context ) 

简单点说 BFC 就是块级上下文的定义，这个概念比较弱，主要是概念在文档中的介绍翻译并不容易，大致可以理解为 
1. BFC 只对子元素负责，不对其孙或者更后代的负责。 （只要正确嵌套的 BFC 不会出现渲染的问题）
2. 每一个 BFC 是一个沙盒，相互独立且互不影响。

#### 一个盒模型作为 BFC 的条件

1. body 本身
2. 设置 float , left/right
3. 设置 position , absoulte/fixed
4. 设置 display , inline-block/flex
5. 设置 overflow , hidden/auto/scroll
6. 设置 boder , 不能为0px  鲜有人知的

#### BFC 解决的问题 

   主要问题就是解决文档流的错位问题，如果是正常的BFC就不会出现错位。

1. 常见问题，外边距重叠的问题 
   1. 子级边距突破父盒模型，导致父盒模型产生外边距
   2. 子元素之间的边距重叠，只取高值
2. 浮动问题，未清除的浮动和不成立的BFC 
   1. 浮动高度塌陷问题
   2. 浮动文档流错位问题



