# 函数是一种对象
## 有名字的函数
* function name(arg1, arg2){ return arg1 + arg2}
## 匿名函数
* let a = function(arg1,arg2){return arg1 + arg2}
* let a = function fn(arg1,arg2){return arg1+arg2}
* fn(1,2)//fn is not defined
* 等于号右边的函数的作用域只在函数内，不是全局作用域

## 箭头函数
* x => x*x // 输入x 输出 x的平方
* (x,y) => x*y //输入x和y，返回x*y的值
* (x,y) => {console.log('test')
* return x*y} //如果有两个操作语句，需要{}，而且必须写return
* 如果想用箭头函数返回一个对象: let f4 = x => ({name:x})

## 用构造函数
* let f = new Function('x','y','console.log(\'hi\');return x + y')

## fn vs fn()
* fn 保存了函数地址
* fn()是调用函数
```javascript 
    let fn = () => console.log('hi')
    let fn2 = fn
    fn2()
```
* fn保留了 匿名函数的地址
* 这个地址被复制给了fn2
* fn2()调用了匿名函数
* fn 和 fn2都只是匿名函数的引用而已
* 真正的函数既不是fn 也不是 fn2

# 函数的要素
## 调用时机 影响函数的结果
```javascript
let i = 0
for(i;i<6;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}// 6个6
```
## 作用域
* 每个函数都会创建一个作用域

### 全局变量
* 在顶级作用域李申明的变量
* 在window上面写变量
* Object parseInt 这些都是写在window上面的，所以可以随便用
* 其他都是局部变量
* 就近原则

### 作用域 & 闭包
```javascript
function f1(){
    let a = 1
    function f2(){
        let a = 2
        function f3(){
            console.log(a)
        }
        a = 22
        f3()
    }
    console.log(a)
    a=100
    f2()
}
f1()
```
#### 闭包
* 如果一个函数用到了外部的变量，那么这个函数加那个变量就叫做闭包
```javascript
let a = 2
function f3(){
    console.log(a)
}
```

## 形式参数
* 就是非实际参数
```javascript
function add(x,y){
    return x+y
}
// 其中x 和 y就是形参，因为他们不是实际参数
add(1,2) //调用时，1 和 2才是实际参数
```
* 形参可多可少
```js
function add(x){
    return x + argument[1]
}
add(4,5)//9
```

## 返回值
* 每个函数都会有返回值，如果没写return 就会返回undefined
* 函数执行完了才会有返回值
* 只有函数才会有返回值

## 调用栈
* js引擎在调用一个函数之前，需要把函数所在的环境push一个数组里面
* 这个数组就是调用栈 
* 等函数执行完了后，会被刚才执行的函数pop出来
* 然后return到之前的环境，继续执行后续代码
### 递归
* 先递进，直到fn(1),再回归
### 爆栈
* 程序push到调用栈的帧太多，已经超过栈的最大值因此爆栈
* chrome 12573个栈

## 函数提升
* 只针对于 `function add(x,y){}` 这种写法
* 函数永远会跑到第一行
* 如果一个let变量和函数名相同，就会报错：identifier 'name' has already been declared
* `let fn = function(){}`这种写法不回存在函数提升

## arguments && this
### arguments
* arguments 是一个包含了所有参数的伪数组，它没有数组的共有属性
* 用Array.from()可以变成伪数组

### this
* 如果不给任何的条件，this默认是window（一般不用）
* 函数中的this最终就是调用函数的对象```person.sayHi()```

#### 两种调用方法
1. ```person.sayHi()```
* 自动把person这个实例传到函数调用的实参里面，作为this；
2. person.sayHi.call(person); 这个方法可以帮助我们理解this
* 需要手动把person传到函数中，作为this
```js
let person = {
    name:'frank',
    sayHi(){
        console.log(this.name)
    }
}
person.sayHi.call({name:1}) // 返回1
person.sayHi.call({name:jack}) // 返回jack
person.sayHi.call(person) // 返回frank

function add(x,y){
    return x+y
}
add.call(undefined,1,3) //add.call(this,arguments[1,3]) 返回4
```

#### this两种使用方法
1. 隐式传递
* fn(1,2) 等价于 fn.call(undefine,1,2)
* obj.child.fn(1) 等价于 obj.child.fn.call(obj.child,1)

2. 显示传递
* fn.call(undefiend,1,2)
* fn.apply(undefined,[1,2])

#### 绑定this
* 使用.bind可以让this不被改变
```js
function f1(p1,p2){
    console.log(this,p1,p2)
}
let f2 = f1.bind({name:'mike'})
//那么f2就是f1绑定了this之后的新函数
//f2() 等价于 f1.call({name:'mike'}) f2 是f1的绑定版函数，绑定了this
```

* .bind 可以绑定其他参数
```js
let f3 = f1.bind({name:'mike'},'hi')
f3() //等价于 f1.call({name:'mike'},'hi') 绑定了this 和 p1
```

## 箭头函数
* 箭头函数没有 arguments 和 this，如果出现了就可以忽略
* 箭头函数里面的this 就是外面的this
```js
console.log(this)//window
let fn = () =>{console.log(this)}
fn()// 返回window
fn.call({name:'mike'})//返回window
```