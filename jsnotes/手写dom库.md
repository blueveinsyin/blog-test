# 什么是库
* 提供给其他人用的工具代码叫做库
* 比如jquery underscore

# api
* 库暴露出来的函数或者属性叫做api

# 框架
* 当你的库变得很大，并且需要学习就叫做库
* 比如vue/react

# 封装技术
* 具体见github代码 

# jquery
* jquery是一个不需要加new的构造函数
* jquery对象指的是jquery函数构造出来的对象
```js jQuery('.test').find.call(jQuery('.test'),'.child').parent().print() ```
* 如果觉得jquery太长了，我们可以用bash alias的方法偷懒:
```js window.$ = window.jQuery ```

## 命名风格的问题
* 如果是普通的div元素 用el开头命名
* 如果是jQuery的元素 用$开头命名