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
注意：fetch请求默认是不带cookie的。需要设置fetch(url, {credentials: 'include'})

2. axios
```
axios.get("") promise对象
axios.post("") promise对象
axios.put("")

axios.delete("")

axios({
  url: "/gateway?type=2&k=3553574",
  headers: {
    'X-Client-Info': '{"a": "3000", "ch": "1002", "v": "1.0.0", "e": "1"}',
    'X-Host': 'mail.cfg.common.banner'
  }
}).then(res => {
  console.log(res.data);
})

返回的数据会被包装

{
*: *,
data: 真实后端数据
}

```

### 2. 计算属性

	复杂逻辑，模板难以维护
	1. 基础例子

	2. 计算缓存 VS methods
		- 计算属性是基于它们的依赖进行缓存的。
		- 计算属性只有在它的相关依赖发生改变时才会重新求值
	3. 计算属性 VS watch
		- v-model


1. 为了实现某个字段首字母大写，可以使用函数进行转换：
	{{myname.substring(0,1).toUpperCase() + myname.substring(1)}}
	修改对应字段的值，模板中的内容会随之改变。
	将所有的计算都写在模板中，代码可读性较差，维护麻烦，所以引入了计算属性。

2. 定义的时候通过方法的形式进行定义，在使用的时候和属性的引用是相同的（不需要加括号）。
	计算属性在模板中多次调用不会重复执行，只有当依赖的状态被修改才会进行重新计算；
	获得的值会进行缓存。
		computed: {
		getMyName(） {
 		    return this.myname.substring(0,1).toUpperCase() + this.myname.substring(1)
		  }
		}
3. 通过方法也可以实现属性的计算，但是在每次调用的时候都会重新计算。调用的时候需要加括号
 		methods: {
			getMyNameMethod() {
			console.log('getMyNameMethod-调用')
			  return "123" 
			}
		},

> 通过计算属性可以很好地替换监听事件等操作。

### 3. Mixins
 24 - 1:30

### 4. 虚拟dom与diff算法key的作用

虚拟dom，动态创建 

具体讲解：https://www.bilibili.com/video/BV11K4y1x7eX?p=26