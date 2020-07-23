## Vue组件

## Vue表单修饰符

```
	<div id="box">
		<input type="text" v-model.lazy="mytext"/>
		{{ mytext }}
	</div>
```

```
	  new Vue({
	    el: "#box",
	    data: {
	      mytext: ""
	    }
	  })
```

使用 `v-model` 会实时进行同步，使用 `v-model.lazy` 时，会在输入框失去焦点的时候进行加载同步。

使用 `v-model.number` 能够限制输入数字之后不能输入字符，但是开始直接输入字符会失效。

使用 `v-model.trim` 可以去掉两边的空格。

## Vue组件

### 1. axios与fetch 实现数据请求
1. fetch
why：
	XMLHttpRequest 是一个设计粗糙的API，配置和调试方式非常混乱，而且基于事件的异步模型写起来不友好。
	兼容性不好
	polyfill：
		https://github.com/camsong/fetch-ie8

	fetch 请求不能跨域，需要在服务器进行访问。
```
	  fetch("./data/data.json").then(res => {
	    // console.log(res)
	    return res.json()
	  }).then(res => {
	    console.log(res)
	  })
```
一般不直接使用 then获取数据，将返回对象转换为 json 再进行调用。
```
	  fetch("./data/data.json").then(res => res.json()).then(res => {
	    console.log(res)
	  })
```
 