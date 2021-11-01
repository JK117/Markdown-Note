# JavaScript 笔记

***
## 1 判断Object对象是否为空
### 1.1 `for ... in`遍历
```javascript
for (var i in obj) { // 如果不为空，则会执行到这一步，返回true
    return true
}
return false // 如果为空,返回false
```

### 1.2 JSON.stringfy()
```javascript
if (JSON.stringfy(data) === '{}') {
    return false // 如果为空,返回false
}
return true // 如果不为空，则会执行到这一步，返回true
```

### 1.3 ES6新增Object.keys()
```javascript
if (Object.keys(object).length === 0) {
    return false // 如果为空,返回false
}
return true // 如果不为空，则会执行到这一步，返回true
```

## 2 判断null和undefined


## 3 判断数组中是否存在某个值
### 3.1 array.indexOf()
> 判断数组中是否存在某个值，如果存在返回数组元素的下标，否则返回-1
```javascript
let arr = ['something', 'anything', 'nothing', 'anything']
let index = arr.indexOf('nothing')
// Output: 2
```

### 3.2 array.includes(searchElement[, fromIndex])
> 判断一个数组是否包含一个指定的值，如果存在返回 true，否则返回false

`searchElement`: 需要查找的元素值
`fromIndex`: 从该索引处开始查找searchElement, 默认为0

```javascript
let numbers = [12, 5, 8, 130, 44];
let result = numbers.includes(8);
// Output: true
result = numbers.includes(118);
// Output: false
```

### 3.3 array.find(callback[, thisArg])
> 返回数组中满足条件的第一个元素的值，如果没有返回undefined

`callback`: element 当前遍历到的元素, index 当前遍历到的索引, array 数组本身
`thisArg`: 指定callback的this参数

```javascript
let numbers = [12, 5, 8, 130, 44];
let result = numbers.find(item => {
    return item > 8
})
// Output: 12

let items = [
    {id: 1, name: 'something'},
    {id: 2, name: 'anything'},
    {id: 3, name: 'nothing'},
    {id: 4, name: 'anything'}
];
let item = items.find(item => {
    return item.id == 3;
});
// Output: Object { id: 3, name: "nothing" }
```

### 3.4 array.findIndex(callback[, thisArg])
> 返回数组中满足条件的第一个元素的索引（下标）, 如果没有找到，返回-1

`callback`: element 当前遍历到的元素, index 当前遍历到的索引, array 数组本身
`thisArg`: 指定callback的this参数

```javascript
let numbers = [12, 5, 8, 130, 44];
let result = numbers.findIndex(item => {
    return item > 8;
});
// Output: 0

let items = [
    {id: 1, name: 'something'},
    {id: 2, name: 'anything'},
    {id: 3, name: 'nothing'},
    {id: 4, name: 'anything'}
];
let index = items.findIndex(item => {
    return item.id == 3;
});
// Output: 2
```

## 4 判断空格字符串
### trim()
```javascript
function isSpace(test) {
    let str = test.trim();
    if (str.length == 0) {
        console.log('All Spaces');
    } else {
        console.log(test);
    }
}
```

### 正则表达式
```javascript
function isSpace(test) {
    if(test.match(/^\s+$/)){
      console.log("all space or \\n");            
    }
    if(test.match(/^[ ]+$/)){
      console.log("all space")
    }
    if(test.match(/^[ ]*$/)){
      console.log("all space or empty")
    }
    if(test.match(/^\s*$/)){
      console.log("all space or \\n or empty")
    } else {
        console.log('输入的字符串为:' + test);
    }
}
```