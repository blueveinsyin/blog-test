# html5全解

## www历史
www = url + html + http

## 如何制作网页
1. 域名知识
2. http服务器知识
3. html知识
4. 其他

## html
最新版html有110个标签

### html5技术集合
1. 新标签、新属性
2. 新的通信技术：WebSockets、webRTC
3. 离线存储技术：LocalStorage、断网检测
4. 多媒体技术：视频、音频
5. 图像技术：Canvas、SVG、WebGL
6. web增强技术：HistoryAPI、全屏
7. 设备相关技术：摄像头、触摸屏
8. 新的样式技术：CSS3新的Flex、Grid布局方式

### 学会一门语言要会：
1. 语法（怎么写代码）
2. 如何调试（如何找错）
3. 在哪查资料
4. 标准制定者是谁

### 如何学：
1. 抄文档
2. 在自己的机器上运行
3. 加一点自己的想法，然后重新运行

### HTML语法
<!DOCTYPE html> 文档类型，告诉浏览器这是html文档
大小写无所谓的 一般都是小写
没有特殊字符的时候，标签的属性可以不加引号
格式都用utf-8
language 都用zh-CN

### 如何调试代码+在哪查资料
使用vscode、webstorm颜色提示
使用 node w3c validator npm
google + mdn

### 工具
jsbin 可以分享给别人，但是只能创建一个文件；
codesandbox 相当于在想的vscode

### 全局属性

#### class
写法1: `[class = class1 class2 ]`不能识别其中一个，会把class1空格class2当作一个整体
写法2: `.class1` `.class2` 可以识别一个
最好一直用class 不倒万不得已不要用id

#### contenteditable
可以使任何一个元素可以被编辑

#### tabindex
`tabindex = 1。。。。200` 按照顺序
`tabindex = 0` tab操作时，最后一个到达
`tabindex = -1` tab操作时，tab永远找不到这个标签

#### title
用来显示完整的内容

### 默认样式
因为html被发明的时候，还没有css
用chrome开发者工具查找默认样式，Elements-Styles-user agent stylesheet

### css reset
通过自己的css代码把默认样式覆盖掉

### pre、code标签
如果想保留空格、回车 就用pre标签
`<pre><h2></h2></pre>`
code标签用来展示代码
`<code></code>`


