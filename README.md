# tips
## scrollTop兼容
### 兼容写法
var scrollTop = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
### 注意
有时候取到的值可能都是0 注意下是否是因为设置了body的高度


body设置高度为100%时，Sarfari浏览器取到的值总是0
