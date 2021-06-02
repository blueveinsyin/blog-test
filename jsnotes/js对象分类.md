# 构造函数
* 可以构造出对象的函数
* 把细节写到一个函数里面，可以调用；这就是封装。

## prototype属性
*  所有函数一出生就有一个 prototype 属性（除了箭头函数）
* 所有 prototype 一出生就有一个 constructor 属性
* 所有 constructor 属性一出生就保存了对应的函数的地址
* 如果一个函数不是构造函数，它依然拥有 prototype 属性，只不过这个属性暂时没什么用
* 如果一个对象不是函数，那么这个对象一般来说没有 prototype 属性，但这个对象一般一定会有 __proto__ 属性

# new操作符
* 自动创建空对象
* 自动为空对象关联原型，原型地址指定为对象.prototype
* 自动将空对象作为this关键字运行构造函数
* 自动return this

# 构造函数
* 函数本身负责给对象本身添加属性
* 构造函数.prototype对象负责保存对象的共用属性

## 词性
* 建议构造函数首字母大写，用名词
* 其他的函数建议用动词开头

# 原型公式
* 对象.__proto__ === 构造函数.prototype

# 类型 & 类
## 类型
* 类型是js数据的分类，有7种
* 四基两空一对象

## 类
* 类是针对于对象的分类，有无数种
* 常见的有Array Function Date RegExp

## 数组对象
* js的数组是一种对象，不是单独的一个品种
* 自身属性：'0'/'1'/'2' 等
* 共有属性：'push' 'pop' 'shift' 'unshift' 'join'

## 函数对象
* 定义一个函数：
* function fn(x,y){return x + y}
* let fn2 = fucntion fn(x,y){return x + y}
* let fn = (x,y)=>x+Y
* let fn = new Function('x','y','return x + y')

* 函数对象自身属性：'name'/'length'
* 函数对象共有属性：'call'/'apply'/'bind'