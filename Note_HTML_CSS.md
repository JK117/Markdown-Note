# HTML & CSS 笔记

***
## 1 a标签去下划线
```scss
//设置a标签的默认状态去除下划线
a{text-decoration: none;}

//设置a标签的访问过后的状态去除下划线
a:visited{text-decoration: none;}

//设置a标签的鼠标覆盖状态去除下划线
a:hover {text-decoration: none;}

//设置a标签的活跃状态去除下划线
a:active{text-decoration:none;}
```

## 2 a标签实现锚点跳转
### 2.1 a标签写上id名
```html
<div><a href="#productid">产品介绍</a></div>
```
### 2.2 在目标区域的最外层div上添加id
```html
<div class="product" id="productId"></div>
```

## 3 btn悬浮样式
```scss
div.some-class:hover, .btn-is-hovered {
   background-color: purple;
}
```