# 如何发送请求
1. 用浏览器地址栏，查看network
2. 用curl命令

# 如何做出一个响应
node.js 有个http模块可以用到


# 系统学习http

## 请求
### 请求行
* 请求动词 路径加查询参数 协议名/版本

### 请求头
get 用来获取内容  
post 用来上传内容
* Host: 域名或IP
* Accept: text/html
* content-type: 请求体的格式

### 回车
空白

### 请求体
* 请求体（上传的内容）

## 响应 response
* 协议名/版本  状态码  状态字符串（状态行）
* content-type: 响应体的格式 （响应头）
* 回车（空白）
* 响应体（也就是下载内容）（响应体）

## 用curl 构造请求、响应
curl -v http://127.0.0.1:8888

* 设置请求动词
-X POST
注意大小写
* 设置路径和查询参数
直接在url后面加

* 设置请求头
-H 'Name:Value' 或者 --header 'Name:Value

* 设置请求体
-d '内容' 或者 --data '内容' 一般与POST一起使用，上传内容

## 用node.js 读取请求
* 读取请求动词
request.method

* 读取路径
request.url 带查询参数的路径
request.path 纯路径，不带查询参数
requets.query 只有查询参数

* 读取请求头
request.headers['Accept']

## 用node.js 设置响应
* 设置响应状态码
response.statusCode = 200

* 设置响应头
response.setHeader('Content-Type','text/html');

* 设置响应体
response.write('内容')
可以分写好几个response.write('内容')

## console.log()调试法

## ssh 操作阿里云服务器
* ssh root@实例ip
* 我的实例ip 8.130.31.184
* 因为root账户权限最高，一旦被攻击就完蛋了；因此我们一般不用root账户，另创建一个账户

### 如何重启应用

* 上传代码
* git push

* 下载代码
* ssh yzq@3.130.31.184
* 进入server.js文件夹
* git pull 更新代码
* killall node 关闭已开的node
* ./start
* 重启完毕

