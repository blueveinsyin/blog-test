# 现成的API
* Math.min
* Math.min.call(null,1,2)
* Math.min.apply(null,[1,2])
* Math看起来像Object一样是构造函数,实际上它是一个对象

# 找三个数字里面最小的数
```js
let minOf3 = ([a,b,c])=>{
    return minOf2([minOf2([a,b],c)])
}
```
# 找四个数字里面最小的数
```js
let minOf4 = ([a,b,c,d])=>{
    return minOf2([minOf3([a,b,c],d)])
}
```
# 求任意长度数组的最小值
```js
let min = (numbers)=>{
    if(numbers.length > 2){
        return min([numbers[0],min(numbers.slice(1))])
    }else{
        return Math.min.apply(null,numbers)
    }
}
```

# 正整数数组排序
1. 递归实现
2. 循环实现
## 给三个数的数组排序
```js
let sort3 = (numbers)=>{
    let index = minIndex(numbers)
    let min = numbers.[index]
    number.splice(index,1)
    return [min].concat(sort2(numbers))
}
```
## 给四个数的数组排序
```js
let sort4 = (numbers)=>{
    let index = minIndex(numbers)
    let min = numbers.[index]
    number.splice(index,1)
    return [min].concat(sort3(numbers))
}
```

## 任意数组的排序
### 递归
```js
let sort = (numbers)=>{
    if(numbers.length > 2){
        let index = minIndex(numbers)
        let min =  numbers[index]
        numbers.splice(index,1)
        return [min].concat(sort(numbers))
    }else{
        return numbers[0] < numbers[1] ? numbers : numbers.reverse()
    }
}
```
#### minIndex 函数
```js
let minIndex = (numbers)=>{
    return numbers.indexOf(min(numbers))
}
```
#### min 函数
```js
let min = (numbers)=>{
    if(numbers.length > 2){
        return min([numbers[0],min(numbers.slice(1))])
    }else{
        return Math.min.apply(null,numbers)
    }
}
```
### 用循环写排序
#### minIndex 重写
```js
let minIndex = (numbers)=>{
    let index = 0
    for(let i = 0; i < numbers.length; i++){
        if(numbers[i] < number[index]){
            index = i
        }
    }
    return index
}
```
* 所有的递归都可以改成循环
```js
let sort = (numbers) => {
    for(let i=0; i<numbers.length - 1; i++){
        let index = minIndex(numbers.slice(i)) + i
        if(index !== i){swap(numbers,index,i)}
    }
    return numbers
}

let swap = (array,i,j) => {
    let temp = array[i]
    array[i] = array[j]
    array[j] = temp
}

let minIndex = (numbers)=>{
    let index = 0
    for(let i = 0; i < numbers.length; i++){
        if(numbers[i] < numbers[index]){
            index = i
        }
    }
    return index
}
```
### 快速排序
```js
let quickSort = arr =>{
    if(arr.length <= 1){return arr}
    let pivotIndex = Math.floor(arr.length/2)
    // arr.splice(index,1)[0] 得出值，不加[0]会返回数组
    let pivot = arr.splice(pivotIndex,1)[0]
    let left = []
    let right = []
    for(let i = 0; i < arr.length; i++){
        if(arr[i]<pivot){left.push(arr.[i])}
        else{right.push(arr[i])}
    }
    return quickSort(left).concat([pivot],quickSort(right))
}
```

### 归并排序
```js
let mergeSort = arr =>{
    let k = arr.length
    if(k===1){return arr}
    let left = arr.slice(0,Math.floor(k/2))
    let right = arr.slice(Math.floor(k/2))
    return merge(mergeSort(left),mergeSort(right))
}

let merge = (a,b)=>{//a, b是array
    if(a.length === 0) return b
    if(b.length === 0) return a
    return a[0] > b[0] ?
        [b[0]].concat(merge(a,b.slice(1))) :
        [a[0]].concat(merge(a.slice(1),b))
}
```

### 计数排序
* 哈希表记录
```js
let countSort = arr =>{
    let hashTable = {}, max = 0, result = []
    for(let i=0; i<arr.length; i++){
        if(!(arr[i] in hashTable)){
            hashTable[arr[i]] = 1
        }else{
            hashTable[arr[i]] += 1
        }
        if(arr[i] > max){max = arr[i]}
    }
    for(let j=0; j<=max; j++){
        if(j in hashTable){
            for(let i = 0; i<hashTable[j]; i++){
                result.push(j)
            }
        }
    }
    return result
}

```

### 堆排序

#### queue队列
* 先进先出的数组
* 比如餐厅叫号系统

##### 栈stack
* 后进先出为栈
* 调用栈就是后进先出

##### 链表 linked list
* 比如原型链

#### 哈希表
* 哈希表的难点
* 如何读取hash['xxx']最快
* 如果做二分法，复杂度就是O(log2n)
* 如果对字符串对应的ACSII数字做索引，对索引做除法取余数，复杂度就是O(1);如果有冲突，就顺延

#### 树
* 是链表的升级，可以连接多个
* 中国的省市区，可以看作一个树
* 公司的层级结构，可以看作一个树
* 网页中的节点，可以看作一个树


