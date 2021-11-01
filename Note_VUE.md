# VUE 笔记

***
## 1 字符串作为变量名获取变量
```javascript
runAsVar(str) {
    return this[`${text}`]
}
```
```html
<img :src="runAsVar(`Icon_${exchange.name}`)">
```

## 2 字符串作为函数名执行
```javascript
proceedAsFunc(f) {
    this[f]()
},
```
```html
<v-btn @click="proceedAsFunc(op)">
    {{ $t(`nudgepool.${op}`) }}
</v-btn>
```

## 3 锚点跳转
实现：点击页面上的某一个按钮时，快速跳转到当前页面指定的区域
### 3.1 在按钮上绑定`click`事件
```html
<div class="button_index" @click="counter1">Button</div>
```
### 3.2 在目标区域的最外层div上添加id
```html
<div class="product" id="productId"></div>
```
### 3.3 在methods中写入以下方法
```javascript
//counter1是绑定的点击事件名称
counter1() {
    //productId是将要跳转区域的id
    const returnEle = document.querySelector("#productId")
    if (returnEle) {
        // true 是默认的
        returnEle.scrollIntoView(true)
        // 平滑移动
        returnEle.scrollIntoView({behavior: 'smooth'})
    }
    //counter1是将要返回地方的id
    // document.querySelector("counter1").scrollIntoView(true); 
}
```