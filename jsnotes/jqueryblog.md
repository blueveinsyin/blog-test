# 选择网页元素
* 使用jQuery的第一步，往往就是将一个选择表达式，放进构造函数jQuery()（简写为$），然后得到被选中的元素。
* 表达式可以是css选择器
```js
$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素

```
* 表达式可以是jQuery表达式
```js
$('a:first') //选择网页中第一个a元素

$('tr:odd') //选择表格的奇数行

$('#myForm :input') // 选择表单中的input元素

$('div:visible') //选择可见的div元素

$('div:gt(2)') // 选择所有的div元素，除了前三个

$('div:animated') // 选择当前处于动画状态的div元素

```
# 对结果进行筛选
```js
$('div').has('p'); // 选择包含p元素的div元素

$('div').not('.myClass'); //选择class不等于myClass的div元素

$('div').filter('.myClass'); //选择class等于myClass的div元素

$('div').first(); //选择第1个div元素

$('div').eq(5); //选择第6个div元素

```
## 选择结果附近的元素

```js
$('div').next('p'); //选择div元素后面的第一个p元素

$('div').parent(); //选择div元素的父元素

$('div').closest('form'); //选择离div最近的那个form父元素

$('div').children(); //选择div的所有子元素

$('div').siblings(); //选择div的同级元素

```


# jquery链式操作
* jQuery设计思想之三，可以对网页元素进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来
```js
$('div') //找到div元素

    .find('h3') //选择其中的h3元素

    .eq(2) //选择第3个h3元素

    .html('Hello'); //将它的内容改为Hello
```
* 这是jQuery最令人称道、最方便的特点。它的原理在于每一步的jQuery操作，返回的都是一个jQuery对象，所以不同操作可以连在一起。

## end()使结果后退一步
```js
// 使得结果集可以后退一步
$('div')

    .find('h3')

    .eq(2)

    .html('Hello')

    .end() //退回到选中所有的h3元素的那一步

    .eq(0) //选中第一个h3元素

    .html('World'); //将它的内容改为World

```

# 对网页元素进行取值和赋值
* jQuery设计思想之四，使用同一个函数，来完成取值（getter）和赋值（setter），即"取值器"与"赋值器"合一
```js
$('h1').html(); //html()没有参数，表示取出h1的值
$('h1').html('Hello'); //html()有参数Hello，表示对h1进行赋值
```
* 赋值会对所有的元素进行赋值，取值只会取出第一个值

# 移动网页的元素
* jQuery设计思想之五，就是提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。
```js
//把p元素移到div元素后面，直接移动div
$('div').insertAfter($('p')); 
// 把p元素移动div元素的前面
$('p').after($('div'));

.insertAfter()和.after()：在现存元素的外部，从后面插入元素

.insertBefore()和.before()：在现存元素的外部，从前面插入元素

.appendTo()和.append()：在现存元素的内部，从后面插入元素

.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
```

# 复制、删除和创建元素
```js
// 复制元素
.clone() 
// 删除元素但不保留
.remove()
// 删除元素但保留
.detach()
// 清空元素
.empty()
// 创建元素
$(元素字符串)
$('<div></div>')

```