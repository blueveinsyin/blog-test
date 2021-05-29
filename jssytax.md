# 表达式与语句

## 表达式
* 1+2表达式的值为 3
* add(1+2) 表达式的值为函数的返回值
* console.log(3) 表达式是函数的返回值，为undefined

## 语句
* var a=1 是一个语句

## 二者区别
* 表达式 一般都有值
* 语句一般会改变环境
* 上面两句话不是绝对的

# 怎么写注释

## 不好的注释
* 把代码翻译成中文

## 好的注释
* 踩坑注解
* 为什么代码一定要这么写

# if语句
* 不要省略{}，可以避免歧义

## 三元表达式/问号冒号表达式
* return a > b ? a : b (如果a大于b，则返回啊，否则返回b)

## &&表达式
* window.f1 && console.log('f1存在')
* A && B:只要前面为假，得A，只要前面为真，得B
* console && console.log && console.log(3)

## ||表达式
* A || B || C: 取第一个真值或者C
* A = A || B

## while循环
`var a = 0.1 `
`while(a !== 1){`
`    console.log(a)`
    `a = a + 0.1`
`} `
* 这是个死循环，因为0.1是浮点数，不够精确，a无法得到1这个值

## break & continue
* break 跳出当前循环，只会跳出就近原则的一个
* continue 可以理解为next

## lable
* { foo: 1} 是一个lable 不是对象
* var obj = {foo:1} 这种情况才是对象