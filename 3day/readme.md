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
	* beforeMount在挂载开始之前被调用.
	* mounted el被新创建的vm.$el替换,并挂载到实例上去之后调用该钩子.
	* beforeUpdate数据更新时调用,发生在虚拟DOM打补丁之前.
	* updated由于数据更改导致的虚拟DOM重新渲染和打补丁,在这之后会调用该钩子.
	* beforeDestroy实例销毁之前调用.
	* destroyed实例销毁后调用.