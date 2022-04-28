<!--
 * @作者: gaowei
 * @页面: 
 * @最后修改人: gaowei
 * @Date: 2022-04-28 12:08:24
 * @LastEditTime: 2022-04-28 14:05:53
-->


## 什么是防抖（debounce）？什么是节流（throttling）？

本质: 不管 debounce 还是 throttling 从目的来看,都是为了`减少事件触发频率`。

区别: 

1. debounce 适合短期内限定频率 , throttling 适合长期频率
2. debounce 适合有改变的内容 , throttling 适合无改变的内容

简单场景分析

1. keyword 联想功能, 用户频繁的触发 input 事件  
   1. 如果 throttling 可能在屏蔽时间段内输入 导致无法联想
   2. 而 debounce 则可以在短暂的时间高频率的触发，更适合
2. throttling 例如应用刷新按钮
   1. debounce 如果一直点击则会导致无法触发联想
   2. 而 throttling 在短期内频繁点击仍然会触发

仅个人认为 debounce 适合触发后`参数会不一致的请求`,`会执行不同的方法`
而 throttling 更适合 长时间段的 `参数相同但触发时间不同的请求`,`同种方法`

throttling 更像是一个定时器(触发延迟型)

而 debounce 只是在短期内推迟了执行

#### 代码实现

debounce :

```js
// fn 代表原始方法 , wait 代表等待时间
const debounce = function(fn,wait = 250){ 
    const timeOutCount = null;
    return function(...args){
        clearTimeout(timeOutCount); // 先清除上一次存储的
        timeOutCount = setTimeout(()=>{
            fn.apply(this,args);
        },wait);
    }
}

```


throttling : 

节流分为两种 `前置型节流` 和 `后置型节流` 

`前置型节流` : 触发后立即执行,周期内不再执行。

`后置型节流` : 触发后在周期内不执行,周期结束执行。

```js
// fn 代表原始方法 , wait 代表等待时间 ,immediate 是否立即执行
const throttling = function(fn,wait,immediate = false){
    const intercept = false; // 
    return function(){
        if(intercept) return ; // 周期内拦截
        intercept = true;  // 打开拦截器
        immediate && fn.apply(this,args);  // 立即执行则后置不执行
        setTimeout(()=>{
            !immediate && fn.apply(this,args);  // 不立即执行则后置执行
            intercept = false 
        },wait)
    }
}

```