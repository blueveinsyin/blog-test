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