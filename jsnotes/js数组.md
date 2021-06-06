# js的数组不是典型的数组

## 典型的数组
* 元素的数据类型相同
* 使用连续的内存存储
* 通过数字下标获取元素

## js的数组不一样
* js数组元素类型可以不一样
* 内存不一定是连续的
* 不能通过数字下标获取，只能通过字符串下标获取
* 意味着js数组可以有任何key

## 创建数组
* let arr = [1,2,3]
* let arr = new Array(1,2,3)
* let arr = '1,2,3'.split(',')
* let arr = '123'.split(',')
* Array.from(字符串)
* Array.from(0:'a',1:'b',3:'c',length:3)

* arr2 = arr1.slice(0) 将arr1复制到arr2
* arr2.concat(arr1)  将arr1和arr2两个数组合并
* js生提供到拷贝 都是 浅拷贝

## 伪数组
* 如果一种数组没有Array里的共有属性，这种数组就是伪数组
* let divList = document.querySelect('div')
* 伪数组的原型链中没有数组的原型

## 删除数组
* 跟对象的删除是一样的，因为数组也是对象
* 在用`delete arr[0]`删除一个数组元素后，数组的长度居然是不变的
* 如果删除了全部的数组元素，数组的长度依然是3；这种数组叫做稀疏数组
* 如果直接改length，也是可以删除数组元素的
* 因此在js中，不要随便改length
* 因此 delete 和 改length 的办法都不是好的删数组元素的方法
### 好的删数组元素的办法
* 删除头部元素： arr.shift()
* 删除尾部元素： arr.pop()
* 删除中间元素： arr.splice(index,1) //删除数组中间的一个元素
* arr.splice(2,1)// 在数组2的位置删除一个元素
* arr.splice(2,3)// 在数组2的位置删除三个元素
* arr.splice(2,1,'x'，'y','z')//在数组2的位置删除一个元素,用元素x y z替代

## 如何查看所有元素
* 使用object查看元素的方法来查看数组元素是不靠谱的;for in是用来访问对象的
* 使用for 循环
* 使用 forEach 进行查看 
* for循环里面有个break & continue,但是 forEach 里面没有

### 如何查看单个属性
* 和对象的查看方式一样: `let arr = [111,222,333] arr[0]`
* 索引越界: `arr[arr.length] === undefined arr[-1] ===  undefined`
* 查找某个元素是否在数组里:arr.indexOf(item)
* 使用条件查找元素: arr.find(item => item % 2 ==== 0)// 查看数组中的偶数
* 使用条件查找元素的索引: arr.findIndex(item => item% 2 === 0)

## 如何添加元素
* 在尾部添加: arr.push()
* 在头部添加: arr.unshift()
* 在中间添加: arr.splice(index,0,item) //在index位置一个都不删除且添加item
* 反转顺序: arr.reverse(); 修改了原来的数组

## 给数组排序
* 经典面试题: 如何把字符串反转?
* arr.sort((a,b) => a.score - b.score)

## 数组变换
### map
* n 对 n

### filter
* n 对 n-1

### reduce
* n 对 1
* 把下列数组中的偶数提取出来
* `arr = [1,2,3,4,5,6]`
* `arr.reduce( (result,item) => result.contac(item % 2 === 1 ? [] : item) ,[])`



