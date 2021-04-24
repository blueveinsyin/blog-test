# css布局
固定宽度布局（960 1080） & 不固定宽度布局（根据文档流原理布局）

## 用什么css布局
如果兼容ie9，只能用float布局
如果不用兼容ie9，只兼容最新的浏览器，用grid
如果不用兼容ie9，不只兼容最新的浏览器，用flex

### float布局
在子元素上面加 float:left 和 width
在父元素上面加 .clearfix    

建议最后一个子元素不设置width，或者设置max-width
不需要做响应式，float是专门为ie准备的，大部分手机上不用ie浏览器

用float实现平均布局，要用到负margin
float的缺点需要程序员自己计算宽度

### flex布局

#### 父元素属性
flex-direction 决定主轴是row 还是 column，justify-content 调整主轴对齐方式，align-items调整次轴
flex-wrap 换行； 
align-content是多行内容对齐方式

#### 子元素属性
order 可以改变子元素的顺序
flex-grow 分配多余的空间
algin-self可以对某个子元素的对齐方式进行调整

#### 经验
尽量不要吧width & height写死
用min-width、max-width、min-height、max-height更好
flex可以满足所以需求
flex和margin-xxx:auto 配合有意外的效果

### 常用画草图工具
balsamiq
墨刀

### grid布局

#### 优点
横竖排均支持;flex只支持一个方向，grid同时支持两个方向
复习grid可用 csstricks的grid游戏