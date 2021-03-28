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

### 如何调试代码+在哪查资料
使用vscode、webstorm颜色提示
使用 node w3c validator npm
google + mdn

### a 标签

#### 如何专业打开html文件
1. http-server 去打卡html文件 `hs -c-1` 可以打开本地服务器
    然后把html的文件名输入到url里面；手机也可以访问
2. pracel `pracel index.html` 即可
3. 使用http-server方法打开html文件，可以打开绝对路径，因为此方法的根目录就是http

#### 属性

##### 属性1：href （超级链接）
###### 网址
支持 https、http 和 //google.com（无协议网址）
//google.com 会自动选择http / https

###### 路径
绝对路径：/a/b/c 以及 相对路径：a/b/c
index.html  以及  ./index.html

###### 伪协议
`javascript:代码;`
`mailto:邮箱`
`tel:手机号`
target （在哪一个窗口打开超链接）

###### id
`href=#xxx`

##### 属性2：target
_blank 在新的页面打开
_top 在iframe链最顶的那一个打开
_parent 在parent iframe打开
_self 在当前页面打开
xxx 如果名字为xxx的窗口不存在，就创建一个新的窗口，名字为xxx
    如果xxx存在，就在xxx窗口打开
`window.name`可以查找窗口的名字（name）
iframe name 我们还可以写iframe的 name

### table标签
table
thead
tbody
tfoot
tr
td
th
#### 相关的样式
##### table-layout
auto:根据td内容的多少来设置宽度
fixed:根据表格的大小来平均没列的宽度
##### border-collapse
`border-collapse:collapse;` 使表格的每个小格合并在一起
`border-spacing:10px;` 调整小格之间的间距
### img标签
img标签会发送一个get请求，展示一张图片
alt:输入文字，在图片加载失败的时候告诉用户图片信息
height/width:只输入其中一个，另一个会自适应调整
src:图片的链接，可以是网址，绝对路径、相对路径

#### 事件
onload:图片加载成功
onerror:图片加载失败;利用这个事件可以专门设置加载失败后显示的图片

#### 响应式
`max-width:100%;`



### form标签
发送get 或 post标签，然后刷新页面
form 中必须要有 `type = submit` 的标签
#### 属性
action:去请求一个url 并返回
metho的:post / get
autocomplete: `autocomplete = on` input会给出建议
target:设定返回action中url的目标;可以指向iframe里面带有name的内容

#### onsubmit事件
input标签 和 button标签 的区别:input中不可以含有标签
但是button可以含有标签

#### 注意事项
一般不监听input的click事件，一般都是监听onfocus事件
form里面的input要有name，http会涉及到
form里面要放一个type=submit，才能触发submit事件

#### input标签type常用的类型
text、color、password、radio（单选）需要多个input有相同的name、
checkbox（多选）让几个checkbox有同样的name就可以让他们归位一组checkbox、
file（type=file multiple可以上传多个文件）、
hidden是用来给机器输入的、textarea（可以拖动，如果需要固定的也可以实现）、
select+option标签

##### input事件
onchange、onfocus、onblur

