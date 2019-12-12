### 5.Vue常用特性

**5.7生命周期**

1. 主要阶段
	* 过载(初始化相关属性)
		* beforeCreate
		* creadted
		* beforeMount
		* mounted
	* 更新(元素或组件的变更操作)
		* beforeUpdate
		* updated
	* 销毁(销毁相关属性)
		* beforeDestory
		* destroyed

2. Vue实例的产生过程
	* beforeCreate在实例初始化之后,数据观测和事件配置之前被调用.(也就是说在beforeCreate生命周期函数执行的时候,data和methods中的数据都还没初始化)
	* created在实例创建完成后被立即调用.(如果要调用methods中的方法,或者操作data中的数据,最早,只能在created中操作)
	* beforeMount在挂载开始之前被调用.(vue.js还没有将模板渲染到浏览器上面)
	* mounted el被新创建的vm.$el替换,并挂载到实例上去之后调用该钩子.(如果我们需要对我们的模板进行DOM操作,最早只能mounted)
	* beforeUpdate数据更新时调用,发生在虚拟DOM打补丁之前.
	* updated由于数据更改导致的虚拟DOM重新渲染和打补丁,在这之后会调用该钩子.
	* beforeDestroy实例销毁之前调用.
	* destroyed实例销毁后调用.

**在vue中数据相关API**

1. 变异方法(修改原有数据)
	* push()
	* pop()
	* shift()
	* unshift()
	* splice()
	* sort()
	* reverse()
2. 替换数组(生成新的数组)
	* filter()
	* concat()
	* slice()

**在vue中数组响应式变化**

3. 修改响应式数据
	* Vue.set(vm.items,indexOfltem,newValue)
	* vm.$set(vm.items,indexOfltem,newValue)
		* 参数一表示要处理的数组名称
		* 参数二表示要处理的数组的索引
		* 参数三表示要处理的数组的值

### vue组件化开发

2. 组件注册
	2.1 全剧组件注册开发语法
	
```javascript
Vue.component(组件名称,{
	data:组件数据,
	template:组件模板内容
})
```

**组件:在UI界面有很多结构相同但是数据不一样的模板,未来重复利用这些模块封装起来组件就可以重复利用的HTML结构**

2.3 组件注册注意事项
	1. data必须是一个函数
		* 分析函数与普通对象的对比
	2. 组件模板内容必须是单个根元素
		* 分析演示实际的效果
	3. 组件模板内容可以是模板字符串
		* 模板字符串需要浏览器提供支持(es6语法)

4. 组件命名方式
	* 短横线方式
	* Vue.component('my-component',{/*...*/})
	* 驼峰方式
	* Vue.component('MyComponent',{/*...*/})

2.4 局部组件注册

```javascript
let ComponentA = {/*...*/}
let ComponentB = {/*...*/}
let ComponentC = {/*...*/}
new Vue({
	el:'#app',
	'component-a':ComponentA,
	'component-b':ComponentB,
	'component-c':ComponentC,
})
```

<!-- 局部组件注册
局部组件只能在注册他的父组件中使用 -->

4. 组件间数据交互
	4.1 父组件向子组件传值
		1. 组件内部通过props接收传递过来的值
		Vue.component('menu-item',{
			props:['title'],
			template:'<div>{{title}}</div>'
		})
		2. 父组件通过属性将值传递给子组件
		<menu-item title='来自父组件的数据'></menu-item>
		<menu-item :title='title'></menu-item>
		3. props属性名规则
			* 在props中使用驼峰形式,模板中需要使用短横线的形式
			* 字符串形式的模板中没有这个限制
		Vue.component('menu-item',{
			//在javaScript中是驼峰式的
			props:['menuTitle'],
			template:`<div>{{menuTitle}}</div>`
			<!-- 在html中是短横线方式的 -->
			<menu-item menu-title="nihao"></menu-item>
		})
		4. props属性值类型
			* 字符串String
			* 数值Number
			* 布尔值Boolean
			* 数组Array
			* 对象Object
