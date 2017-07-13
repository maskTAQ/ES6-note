# es6笔记

## Promise
1. `Promise.prototype.catch`和`Promise.prototype.then`都会返回一个Promise对象,
如果代码块中无错会触发`resolve`传递return的值,有错会触发`reject`,以下代码用catch举例.

```javascript
let someAsyncThing = function() {
    return new Promise(function(resolve, reject) {
        resolve(x + 2);
    });
};

someAsyncThing()
.catch(error => {
  /*
  1. catch中的y并没有定义会报错
     catch方法会返回 Promise 对象
     触发reject回调
     触发函数b
  */
  //y + 1;
  /*
  2. catch方法会返回 Promise 对象
     触发resolve回调,传递return的值
     触发函数a
  */
  //return 'ok';
})
.then(function a(message) {
    console.log(message);
})
.catch(function b(error) {
    console.log(error);
})
```
