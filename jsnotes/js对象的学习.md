# js的object,唯一一个复杂的数据类型

## 默写对象的种类
Number
String
Symbol
Boolean
Null
Undefine
Object

## 默写5个falsy值
null undefine NaN '' 0

## object
* 无序的数据集合
* 键值对对集合
* `let obj = {'name':'mike','age':19}`
* `let obj = new Object({'name':'mike','age':20})`
* `console.log({'name':'mike','age':'19'}`
* 键名都是字符串，不是标识符，可以包含任意字符
* 引号可以省略，但是键名依然是字符串

### 变量做属性名
* `let p1 = 'name'`
* `let obj = {[p1]:'mike'}`
* 加了`[]`的键值会被当作变量求值 比如`[1+2+3]`也可以

### 对象的隐藏属性
* js每一个对象都有一个隐藏属性
* 这个隐藏属性储存着其共有属性组成的对象的地址
* 这个共有属性组成的对象叫做原型
* 因此隐藏属性储存的是原型的地址

#### 删除属性
* delete obj.xxx 或 delete obj['xxx'], 可以删除obj的xxx属性。
* 我们需要明白 属性值位为undefined 和 不含属性名 是不一样的
* `'xxx' in obj === false` 可以判断 obj 中以及不含属性名 xxx 了
* `'xxx' in obj && obj.xxx === undefined` 表示obj含有属性名xxx,但是值为undefined
* 判断obj是否有某个属性值 只能用 in;`obj.xxx === undefined` 不可以

#### 读属性
* Object.keys(obj) 返回所有的属性
* Object.values(obj) 返回所有的值
* Object.entries(obj) 返回所有的属性和值
* 但是以上的不会返回共有属性
* console.dir(obj) 可以返回所有的属性(自身属性+共有属性)
* '属性名' in obj 无法判断是否是自身属性
* obj.hasOwnProperty('属性') 可以判断是否为自身属性

### 原型
* 每个对象都有原型
* 所有对象的原型也有原型
* 这个原型包好所有对象的共有属性，是对象的根
* 这个原型也有原型，是null

#### 查看属性
* 中括号语法: obj['key'],优先使用这个语法
* 点语法: obj.key

#### 修改或者增进属性
* 只能修改自身属性
* 不建议修改原型的属性

##### 直接赋值
* `let obj = {name:'frank'}`
* `obj.name = 'frank'`
* `obj['name'] = 'frank'`

* `obj['na'+'me'] = 'frank'`
* `let key = 'name'`
* `obj[key] = 'frank'`
* 因为 obj.key 等价于 obj['key']

##### 批量赋值
* `Object.assign(obj,{age:18,gender:'man'})`

#### 直接修改原型
* `var person = Object.create(common,{name:{value:'frank'}})`
* create创造的属性是原型属性,不是person的自身属性