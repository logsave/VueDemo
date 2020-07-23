# Vue
## 1. Vue概述

Vue：渐进式JavaScript框架
[Vue文档](https://cn.vuejs.org/v2/guide/)
[Vue Api](https://cn.vuejs.org/v2/api/)

## 2. Vue基本使用

### 2.1 传统开发模式对比
1. 原生JS
```html
<div id="msg"></div>
<script type="text/javascript">
  var msg = 'Hello World';
  var div = document.getElementById('msg');
  div.innerHTML = msg;
</script>

```

2. JQuery
```html
<div id="msg"></div>
<script type="text/javascript" src="js/jquery.js"></script>
<script type="text/javascript">
  var msg = 'Hello World';
  $('#msg').html(msg);
</script>
```

### 2.2 Vue.js之Hello World基本步骤
3. Vue
```html
<div id="app">
  <div>{{msg}}</div>
</div>
<script type="text/javascript" src="js/vue.js"></script>
<script type="text/javascript">
  new Vue({
    el: '#app',
    data: {
      msg: 'Hello World'
    }
  })
</script>
```











