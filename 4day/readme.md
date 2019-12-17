### 4.组件间数据交互
		4.2 子组件向父组件传值
			* props传递数据原则:单向数据流
			1. 子组件通过自定义事件向父组件传递信息
				<button v-on:click='$emit("enlarge-text")'>扩大字体</button>
			2. 父组件监听子组件的事件
				<menu-item v-on:enlarge-text='fontSize += 0.1'></menu-item>
			3.子组件通过自定义事件向父组件传递信息
			<button v-on:click='$emit("enlarge-text",0.1)'>扩大字体</button>
			4.父组件监听子组件的事件
			<menu-item v-on:enlarge-text='fontSize += $event'></menu-item>
			
			
		4.3 非父子组件间传值
			1. 单独的事件中心管理组件间的通信
				let eventHub = new Vue()
			2. 监听事件与销毁事件
				eventHub.$on('add-todo',addTodo)
				eventHub.$off('add-todo')
			3. 触发事件
				eventHub.$emit('add-todo',id)
				
		5.1 组件插槽的作用
			* 父组件向子组件传递内容
			1. 插槽位置位于子组件模板的内容当中
		
		5.2 匿名插槽
			* <!-- 这里的所有组件标签中嵌套的内容会替换掉slot  如果不传值 则使用 slot 中的默认值 -->
		
		5.3 具名插槽
			* 具有名字的插槽
			* 使用<slot>中的"name"属性绑定元素
		5.4 作用域插槽
			* 父组件对子组件加工处理
			* 既可以复用子组件的slot,又可以使slot内容不一致

### 前后端交互模式
	1.1 接口调用方式
		* 原生ajax
		* 基于jQuery的ajax
		* fetch
		* axios
	1.2 URL的地址格式
		1. 传统的形式URL
		* 格式:schema://host:port/path?query#fragment
			* schema:协议.例如http,https,ftp等
			* host:域名或者IP地址
			* port:端口,http默认端口80,可以省略
			* path:路径,例如/abc/a/b/c
			* query:查询参数,例如uname=lisi&age=12
			* fragment:锚点(哈希Hash),用于定位页面的某个位置
		2. Restful形式的URL
			* HTTP请求方式
				* GET 查询
				* POST 添加
				* PUT 修改
				* DELETE 删除
### Promise用法
2. Promise方法
	2.1异步调用
	* 异步效果分析
		* 定时任务
		* Ajax
		* 事件函数
	* 多次异步调用的依赖分析
		* 多次异步调用的结果顺序不确定
		* 异步调用结果如果存在依赖需要嵌套
	2.2Promise概述
	Promise是异步编程的一种解决方案,从语法上讲,Promise是一个对象,从它可以获取异步操作的消息.
	使用Promise主要有以下好处:
	* 可以避免多层异步调用嵌套问题(回调地狱)
	* Promise对象提供了简洁的API,使得控制异步操作更加容易
	2.3Ajax的实现步骤
		1. 创建对象
		var xhr = new XMLHttpRequest();
		2. 告诉Ajax请求地址以及请求方式
		xhr.open('get','http://www.example.com');
		3.发送请求
		xhr.send();
		4.获取服务器端给与客户端的响应数据
		xhr.onload = function () {
			console.log(xhr.responseText);
		}
	2.4基于Promise处理Ajax请求
		2.发送多次ajax请求
		queryData()
			.then(function(data){
				return queryData();
			})
			.then(function(data){
				return queryData();
			})
			
			.then(function(data){
				return queryData();
			})
	2.5then参数中的函数返回值
		1.返回Promise实例对象
			* 返回的该实例对象会调用下一个then
		2.返回普通值
			* 返回的普通值会直接传递给下一个then,通过then参数中函数的参数接收该值
### 接口调用-fetch用法

#### 3.1 fetch概述

		1. 

#### 3.2 fetch API基本用法
	
```javascript
fetch('/url传输地址').then(data=>{
	return data.text();
	//text()方法食欲fetchAPI的一部分,他返回一个Promise实例对象
}).then(ret=>{
	//这里才能得到的才是最终的数据
	console.log(ret);
})
```
#### 3.3 常用配置选项

		1. 常用配置选项
			* method(String):
		2. 响应数据格式
			* text():将返回体处理成字符串类型
			* json():返回结果好JSON.parseText()一样
### 接口调用-axios用法

#### 4.1 axios 的基本特性

**axios是一个基于Promise用于浏览器和node.js的HTTP客户端.**

它具有以下特征:
* 支持浏览器和node.js
* 支持promise
* 能拦截请求和响应
* 自动转换JSON数据

#### axios的基本用法

* axios.get('/adata')
	.then(ret=>{
		// data属性名称是固定的,用于获取后台响应的数据
		console.log(ret.data)
	})
	

### 接口调用-async/await用法
### 基于接口的案例