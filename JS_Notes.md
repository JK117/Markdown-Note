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
