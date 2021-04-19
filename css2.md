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

