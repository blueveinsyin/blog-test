# css定位
布局是屏幕平面上的，定位是垂直与平面上的
div的分层:文字元素 - 浮动元素 - 没有浮动的块级子元素 - border - background

# css动画

## 浏览器渲染过程
根据HTML构建HTML树(DOM)
根据css构建css树(cssom)
将两棵树合并成一颗渲染树(render tree)
layout布局(文档流、盒模型、计算大小和位置)
paint绘制(把边框颜色、文字颜色、阴影等)
compose合成(根据层叠关系展示画面)

### 如何查看性能
开发这工具里的rendering-painting flash 可以可视化查看渲染过程
css渲染过程一次包含布局、绘制、合成
布局和绘制有可能被省略

## 如何更改样式
有三种办法更改样式：
js/css - sytle - layout - paint - composite
js/css - style - paint - composite
js/css - style - composite
transform属于第三种，transform只需要render composite，不需要render layout或者 paint
https://csstriggers.com/ 帮助我们查找更改样式会render哪些

## transform
位移 translate
缩放 scale
旋转 rotate
倾斜 skew

## transition 动画  
不是所有的属性都可以过渡:
display不可以

## animation动画
animation: 动画时长 | 模式 | 延时 ｜ 重复次数 ｜ 方向 ｜animationName;

@keyframes animationName{
    from{}
    to{}
}

@keyframes varanimationNameiable{
    0%{}
    50%{}
    100%{}
}



