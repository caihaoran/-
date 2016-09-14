# js创建css样式表
## 创建一个新样式表
```
// 创建 <style> 标签
var style = document.createElement("style");
// 可以添加一个媒体(/媒体查询,media query)属性
// style.setAttribute("media", "screen")
// style.setAttribute("media", "only screen and (max-width : 1024px)")

// 对WebKit hack :(
style.appendChild(document.createTextNode(""));

// 将 <style> 元素加到页面中
document.head.appendChild(style);
```

## 插入规则
`sheet.insertRule("header { float: left; opacity: 0.8; }", 1);`