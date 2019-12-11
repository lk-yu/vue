**样式绑定相关语法细节**
```
1. 对象绑定和数组绑定可以结合使用
2. class绑定的值可以简化操作
3. 默认的class如何处理?默认的class会保留
```
**3.6样式绑定**
```javascript
1. class样式处理
	* 对象语法
	<div v-bind:class="{active:isActive}"></div>
	* 数组语法
	<div v-bind:class="{activeClass,errorClass}"></div>
2. style样式处理
	* 对象语法
	<div v-bind:style="{color:activeColor,fontSize:fontSize}"></div>
	* 数组语法
	<div v-bind:style="[baseStyle,overridingStyles]"></div>
```
### 3.7 分支循环结构
1. 分支结构
	* v-if
	* v-else
	* v-else-if
	* v-show
2. v-if与v-show的区别
	* v-if控制元素是否渲染到页面
	* v-show控制元素是否显示(已经渲染到了页面)
**v-show的原理:控制元素样式是否显示display:none**