# js函数的执行时机

```js
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
上面的代码输出结果为: 6 6 6 6 6 6 

* js是单线程执行,即按顺序执行每一行代码
* 但是setTimeout()函数可以实现暂停执行某一段代码，先去执行其他的代码。
* 在这块代码中包含console.log(i)的函数在setTimeout()函数中，因此每一次的
* for循环都会跳过setTimeout()函数，先去执行i++
* 而且，由于i = 0 的i是个全局变量，因此等到setTimeout()函数第一次执行，i已经变成了
* 6。最后由于积攒了6个暂停执行的setTimeout()函数，因此输出了6个6。

## 解决输出 6个6 的代码方法
### 方法1 定义块级作用域
```js
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
* 在这块代码中，let i = 0 可以为自己获得一份单独的作用域
* 这个i不是全局变量，它不会被改写
* 每执行一次for循环都会创建一个新的i，js引擎可以允许新的i在上一轮的i值上面相加计算
* 因此在执行setTimeout()函数后，会输出不同的i: 0 1 2 3 4 5

### 方法2 使用立即执行函数
```js
let i = 0
for(i = 0; i<6; i++){
    !function(i){  
        setTimeout(()=>{
            console.log(i)
        },0)
    }(i)
}
```


