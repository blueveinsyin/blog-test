# document object model文档对象模型 DOM
* dom像一个tree，有很多节点
* 当今程序员会用vue、react操作dom

## 获取元素(标签)
* window.idxxx 或者直接 idxxx
* 兼容ie,才用getElementsBy...
### 工作中优先使用下两个
* 常用 querySelector('div>span:nth-child(2)')
* 常用 querySelectorAll('div>span:nth-child(2)')[0]

## 获取特别的元素
* document.documentElement 获取HTML
* window 获取窗口    
* document.all 获得所有标签；这是第6个falsy值

## 获取的元素是什么东西？
* 显然都是一个对象，要搞清楚属性以及原型
* 用console.dir(元素) 来看元素的结构
### 元素的结构：
* 是一个对象,这个对象有6层原型
* div原型链
* 节点和元素的区别

## 创建api
* appendChild(node)
* 创建的标签默认处于js线程中，还要把其放到body标签里面

* appendChild:一个元素不能出现在两个地方，除非复制一份
* let div2 = div1.cloneNode(true) true为深拷贝

## 删除api
* 旧方法:parentNode.removeChild(childNode)
* 新方法:childNode.remove() childNode还在内存中
* childNode = null 彻底删除了

## 修改属性
* 改class: div.className = 'red blue'（全覆盖）
* 改class: div.classList.add('red')
* 改style: div.style = 'width:100px;color:blue;'
* 改style的一部分: div.style.width = '200px'
* 大小写: div.style.backgroundColor = 'white' backgroundColor表示css中的background-color
* 改data-* 属性: div.dataset.x = 'frank'

## 读属性
* div.classList/a.href
* div.getAttritube('class')/a.getAttribute('href')

## 改事件处理函数
* div.onclick默认为null，默认点击div不会有任何事情发生
* 但如果把div.onclick改为一个函数fn
* 那么点击这个函数的时候，浏览器就会调用这个函数，并且是fn.call(div,event)这样调用
* div会被当作this,event则包含点击事件所有信息
## 改文本内容
* test.innerText = 'hi' / test.textContent = 'ho'
## 改html内容
* test.innerHTML = '<strong>hi</strong>'
## 改标签
* div.innerHTML = '' //先清空
* div.appendChild(div2)//再加内容
## 改爸爸
* newParent.appendChild(div)

## 查爸爸
* div.parentNode / parent.parentElement
* test.children.length 和 test.childNodes.length 是有区别的
## 查爷爷
* node.parentNode.parentNode
## 查子代
* node.childNodes 或者 node.children
## 查兄弟姐妹
* node.parentNode.childNodes 再减去自己
* node.parentNode.children 再减去自己

## DOM操作是跨线程的
* 为什么dom操作比较慢
* 浏览器有渲染引擎和js引擎
* 在div放入页面之前，我对div的所有操作都是基于js线程中的
* 直到 div放入页面之时，浏览器会发现js意图，就会通知渲染线程在页面中渲染div对应的元素
* div放入页面后，对div的操作有可能触发重新渲染，具体看操作
* 如果对div连续操作多次，浏览器可能会合并成一次操作，也可能不会。

### 属性同步
* 如果是标准属性，比如id、className、title,对div的标准属性修改会被浏览器同步到页面中
* 还有data-* 属性也会同步
* 非标准属性:对此修改只会停留在js中，不会同步到页面中。比如x属性
* 启示:对于我们的自定义属性,又想将其同步到页面中,请使用data- 作为前缀
* js中的属性一般为properties;页面中的属性一般为attributes

### property vs attribute
* js线程中div的所有属性，叫做div的property
* 渲染引擎中div对应标签的属性，叫做attribute
* 大部分时候，同名的是相等的； 如果不是标准属性，那么这俩只会在刚开始相等，js的property变化，页面是不会立马知道的
* attribute只支持字符串;而property支持字符串、布尔等类型