# css基础概念

## 层叠样式表
### 样式层叠
可以多次对同一选择器进行样式声明
### 选择器层叠
不同选择器对同一元素进行样式声明
### 文件层叠
可以用多个文件进行层叠

这些特性使得css极度灵活

## 怎知道哪些浏览器支持哪些特性
使用caniuse.com

## 语法
### 语法一
选择器 {
    属性名：属性值；
    /*注释*/}
注意事项：所有符号都是英文
区分大小写，a 和 A是不同的东西
没有//注释
任何地方写错了，都不会报错

### at语法
@charset "UTF-8";
@import url(2.css);
@media (min-width:100px) and (max-width:200px){语法一}

@charset必须放第一行
前两个at语法必须以分号；结尾
charset是字符集的意思，但是UTF-8是字符编码

## 如何调试
使用开发者工具：
找到标签 找到对应的选择器 看它样式是否被划掉 看它的样式是否有警告

### border调试办法
给元素加border

## 在哪里查资料
google 搜索 关键词+mdn
关键词 + css tricks
张鑫旭 + 关键词

## 素材练习


## 文档流 最重要
normal flow 指的是元素流动方向（inline、span左到右，block上到下每一个元素占一行）
inline-block也是从左到右，不会跨行
不要在inline里面写block inline会忽视width设置
div的宽度默认为能有多宽就多宽，自动计算宽度，但是可以用width设置

新的html5标准元素不分 内联元素 和 块级元素

### 高度
inline高度由line-height间接确定，跟height无关；字体会影响实际高度（行盒）
block元素高度由文档流内所有元素的总和决定的；可以设置高度
inline-block高度基本于block是一样的

### 如何脱离文档流
float
position:absolute/fixed

## css盒模型
盒模型分两种：content-box & border-box
content-box的宽度只包含content
border-box的宽度包含到border（border+内边距+内容）
一定要使用border-box

### margin合并
#### 兄弟元素合并
两个child元素的margin会合并
display:inline-block; margin就消除合并了

#### 父子元素合并
第一个child元素、最好一个child元素会和parent元素的margin重叠
如果margin之间有其他的属性就不会margin合并（加padding、border）
overflow:hidden && display:flex
只有上下重叠、左右不重叠

## 基本单位
px 像素
em 相对于自身字体的倍数







