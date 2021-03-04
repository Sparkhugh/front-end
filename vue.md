# vue	渐进式框架
* 响应式编程 组件化开发;
* 代码体积小,基于虚拟dom,数据双向绑定;
* 引入:script标签 vue-cli脚手架工程化安装;
```html
* 开发环境版本
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
* 生产环境版本
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```
* 安装
```
npm install vue
```

1. vue实例		
* 声明式渲染下的双向绑定 
	dom上的数据发生变化,app的data数据也变化
	app实例上的data数据发生变化,dom节点数据也发生变化
```html
<div id="app">
	<h1>{{msg}}</h1>
	<input type="text" v-model="msg">
	<button v-on:click="login">登录</button>
	<button v-on:click="regist">注册</button>
</div>
```
```js	
//一个vue实例,一个vue实例不允许再嵌套vue实例
var app=new Vue({
	el:'#app',	//Vue实例挂载的dom节点
	data:{
		msg:'hello vue'
	},
	methods:{
		login(){
			console.log('login')
			this.msg='hhh'
		},
		regist(){
			console.log('regist')
		}
	}
})
```
1.1 Vue实例的选项
* 数据
	data	Vue实例的数据对象 数据类型Object/Function
	props	用于接收来自父组件的数据 数据类型Array/Object
	propsData	创建实例时传递props,方便测试,只用于 new 创建的实例;
	computed	计算属性,基于响应式依赖进行缓存
	methods		用于放Vue实例中的方法
	watch			监听属性	 数据变化时执行异步/开销大的操作 无缓存性
```js
var app=new Vue({
	el:'#app',
	data:{
		firstname:'',
		lastname:''
	},
	computed:{
		fullname:function(){
			//this指向vue实例
			return this.firstname +''+ this.lastname
		}
	},
	watch:{
		fullname(val){
			console.log('fullname发生变化',val)
		}
	}
})
```

* dom
	el 	Vue实例挂载的DOM节点 根实例特有的选项
	template
	render
	renderError

* 生命周期钩子 11个 常用8个

1.2 Vue实例方法
* 数据
	app.$watch(exp/Fn,callback,[options])
	app.$set(target,propertyName/index,value)		全局Vue.set别名
	app.$delete(target,propertyName/index)			全局Vue.delete别名

* 事件
	app.$on(event,callback)						监听当前实例上的自定义事件
	app.$once(event,callback)					监听一个自定义事件,只触发一次
	app.$off([event,callback])				移除自定义事件监听器
	app.$emit(事件名,[...args])				触发当前实例上的事件,附加参数会传给监听器回调

* 生命周期
	app.$mount(ele)		手动挂载一个未挂载的实例
	app.$forceUpdate()	迫使	Vue实例重新渲染
	app.$nextTick([callback])
	app.$destroy()		完全销毁一个实例,触发beforeDestroy destroyed钩子
--------------------------------------------------
2. vue指令	 14个,常用10个
* {{}}	文本插值
* v-text	插入文本
```html
<p>{{msg}}</p>
<p v-text="msg"></p>
```
* v-html	更新元素的innerHTML	可解析a标签
```html
<div v-html="link"></div>
* js	link:'<a href="http://baidu.com">百度</a>'
```

* v-on		绑定事件		缩写 @
```
<div @click="tabClick('0')" :class="{'on':currentTab=='0'}">tab1</div>
<button @click='warn('未成功',$event)'>提交</button>
* 用特殊变量 $event 访问原始dom事件
...methods:{
	warn:function(msg,event){ if(event){ event.preventDefault() } }
}...

* 事件修饰符		顺序很重要
	@click.stop		阻止冒泡event.stopPropagation()
	@click.prevent 	调用event.preventDefault()
	@click.capture		事件监听器使用捕获模式
	@click.self		事件监听器绑定的元素本身触发才触发回调
	@keyup.enter	键修饰符
	@keyup.13		键代码
	@click.once		点击只触发一次
	@click.stop.prevent		串联修饰符 有先后顺序
	.passive	能提升移动端性能
```

* v-show	切换显示/隐藏		
	与v-if区别是,元素隐藏是display:none 做显示隐藏效果时用v-show更好
```
<h2 v-show="currentTab=='0'">tab1</h2>
```
* v-if		条件渲染		
	条件为true时显示	元素隐藏是直接删除节点	 成本比v-show更高
	v-else-if		必须跟在 v-if 或 v-else-if 后
	v-else	必须跟在 v-if 或 v-else-if 后
```
<h2 v-if="currentTab=='0'">tab1</h2>
<h2 v-else-if="currentTab=='1'">tab2</h2>
<h2 v-else-if="currentTab=='2'">tab3</h2>
<h2 v-else="currentTab=='4'">tab4</h2>
```

* v-for		列表渲染 循环  与v-if同用时,v-for优先级更高(不推荐同时用)
	使用v-for时要提供一个key值,使用字符串或数值型作为key, key是保证节点唯一性的标识
```
<div v-for="(item,index) in arr"></div>
<div v-for="(val,key) of obj">	{{key}}:{{val}}	</div>

* 强制重新排序元素,需要给元素一个key属性
<div v-for="item in items" :key="item.id">
	{{item.text}}
</div>
```
* 数组方法
```
* 变异方法		改变源数组的方法
arr.shift()
arr.pop()
arr.unshift()
arr.push()
arr.splice(start,length)
arr.sort()
arr.reverse()

* 非变异方法 	不会变更原数组,返回新数组
arr.filter()
arr.concat()
arr.slice()
```

* v-bind 	动态的绑定一个或多个属性		缩写	:
```
<h1 v-bind:title="title">学生</h1>		//属性绑定
<div :class="green" v-text='msg'></div>				//class绑定
<div :class="[isGreen?'green':'red']" v-text='msg'></div>
<div :style="{'color':color,'fontSize':fontSize}">style样式绑定</div>

* css	.green{} .red{}
* js	
data:{
	title:'student',
	msg:'hello vue'，
	color:'green',
	fontSize:'18px'
}

* 修饰符
	.prop
	.camel
	.sync
```

* v-model		表单/组件和应用状态实现双向绑定 (与react的区别之一)
```
<input> <textarea> <select>
text和textarea 相当于	v-bind:value 和 @input结合;
checkbox和radio中	相当于 v-bind:checked 和 @change结合;
selcet将value作为prop,将change作为事件;

* 表单修饰符
	.lazy		取代input监听change事件		性能更优化
	.number	字符串转为number型
	.trim		清除两端空格
	v-model.trim.number.lazy='pw'
```

* v-slot	插槽 只能放在 <template> 中使用 缩写 #
```
//具名插槽
<template v-slot:header>
	header content
</template>
```
* v-pre		跳过此元素和其子元素的编译过程
```
<span v-pre> {{'不需编译'}} </span>
```
* v-cloak
```
//不会显示,直到编译结束
[v-cloak] { display:none; }	//css
<div v-cloak> {{msg}} </div>	//js
```
* v-once	只渲染元素和组件一次
```html
<div v-once>{{msg}}</div>
<my-component v-once:comment="msg"></my-component>
```
--------------------------------------------------
3. vue生命周期钩子函数		11个,常用8个
* new Vue()->实例初始化----->实例创建完成,未挂载---->实例挂载之前---->实例被挂载mounted------------>实例销毁之前---->实例销毁destroyed
												|						|									|						|				|数据更新								|								|
									beforeCreate		created				beforeMount		mounted		beforeUpdate					beforeDestroyed		destroyed
																																					|虚拟dom重新渲染				(实例仍可用)
																																				updated
```js
beforeCreate:function(){
	console.log('beforeCreate')
},
created:function(){
	console.log('created')
},
beforeMount:function(){
	console.log('beforeMount')
},
mounted:function(){
	console.log('mounted')
	//调接口、创建swiper组件等操作
},
beforeUpdate:function(){
	console.log('beforeUpdate')
},
updated:function(){
	console.log('updated')
},

activated:function(){ //不常用  用于动态组件keep-alive},
deactivated:function(){ //不常用 },

beforeDestroy:function(){
	console.log('beforeDestroy')
	//清除耗费性能的东西,定时器等
},
destroyed:function(){
	console.log('destroyed')
},

errorCaptured:function(){ //不常用 }
```
* Vue实例创建完成后触发 beforeCreate created beforedMount mounted 4个钩子函数;
* Vue实例数据更新才触发 beforeUpdate updated钩子函数;
* 使用`app.$destroy()` 手动触发组件销毁, 触发beforeDestroy destroyed钩子函数;
* 清除定时器,在 beforeDestroy 钩子函数中进行;
* 调接口、创建swiper组件等操作在 mounted钩子函数中进行;
* 需要完整的dom结构才能做初始化渲染的第三方ui库,其业务逻辑都要放在 mounted钩子函数中进行;
--------------------------------------------------
4. 响应式原理
* 利用es5中 Object.defineProperty() 把对象的定义转为getter/setter方式
	页面数据发生变化时,依赖项的setter操作触发,会通知监听器watcher,重新渲染页面;
* 前端框架有两种方式侦测数据变化,`push`和`pull`,vue响应式系统是`push`+`pull`,react是`pull`方式
```js
var app={}
//把对象定义 转化为getter/setter方式
Object.defineProperty(app,'msg',{
	get:function(){
		return value;
	},
	set:function(arg){
		value=arg
		//setter操作中 通知 watcher 更新页面
		watch(value)
	}
})
//页面数据发生变化,更新对象,触发setter操作
dom.addEventListener('keyup',function(e){
	app.msg=e.target.value; //触发setter
})
//监听器
function watch(value){
	document.getElementById('msg').innerHTML=value;
}
```
--------------------------------------------------
5. 虚拟DOM		性能优化
* MVC		model数据  view视图  control控制器
* MVVM	model数据  view视图  VM视图模型 即虚拟DOM
* 虚拟DOM 
	即一个json对象,用于描述真实DOM节点
```js
var ele={
	tagName='div',
	attr:{
		props:{
			id:'header'
		},
		styles:{
			color:'red'
		}
	}
}
```
* diff运算  difference
	Vue实例中数据发生变化,vue会拷贝一份虚拟DOM,通过diff运算,找出变化前和变化后虚拟DOM的最小差异,并把最小差异渲染到真实DOM上;
	MVVM框架中 基于虚拟DOM的diff运算减少了DOM的频繁操作,有利于性能优化,适合数据化的产品应用开发;
--------------------------------------------------
6. 组件
* 组件是可复用的Vue实例  与new Vue一样接收相同的选项,data methods computed 生命周期钩子等;
```js
// 全局注册			组件注册要放在根实例之前
	Vue.component('my-app',{	//第一个参数就是组件名
		//选项
		props:[],		//在组件上注册的自定义属性,通过props向子组件传值
		data:function(){
			return {
				//工厂模式 一个组件的data选项必须是一个函数  深拷贝
				//组件共享`data`属性 避免组件间相互影响
			}
		},
		template:`
			<div>
				<h1 v-text='text'></h1>
			</div>
		`,
		computed:{},
		methods:{
			change(id){
				//事件通信 触发父组件传递过来的自定义事件,并把子组件的变化传给父组件
				this.$emit('click',id)
			}
		}
	})
	
// 根实例
	var app=new Vue({
		el:'#app',
		data:{},
		components:{	//局部组件,只能在其注册的vue实例中使用
			'scope-component':{
				template:`<div>局部组件</div>`
			},
			'my-scope':{
				template:`<h1>局部组件</h1>`
			}
		}
	})
```
* 组件名尽量 全小写且中间包含一个连字符;
* props 存放在组件上注册的自定义属性,在组件实例中能访问这个值就像访问 data 中的值一样
	在子组件中对props进行验证 `type` `require`
* props 子组件接收父组件的数据
	vm.$emit(事件名,[...args])  父组件接收子组件的数据变化  事件名为父组件的自定义事件名

* 自定义input组件
```
<input v-model='search'> 等价于 <input v-bind:value='search' @input='search=$event.target.value'>
* html
<my-input v-model='search'></my-input>
* js
Vue.component('my-input',{
	props:['value'],
	template:`
		<input v-bind:value='value' @input='$emit('input',$event.target.value)'>
	`
})
```

* 插槽 slot
	v-slot指令 缩写 #  插槽名默认值是default
	slot传值,仅在自己的slot中有效,有作用域限制
```
* html
<my-layout>
	<template v-slot:default></template>
	<template v-slot:header></template>
	<template #aside='scope'>
		<h1 v-text='scope.msg'></h1>
	</template>
</my-layout>

* js
template:`
	<slot></slot>
	<slot name='header'></slot>
	<slot name='aside' :msg='msg'></slot>
`
```

* 动态组件 <keep-alive> 
	切换组件后保持原来组件的状态,要求被切换到的组件必须有自己的名字,可用作tabs选项卡
```html
<keep-alive>
	<component :is='curTab'></component>
</keep-alive>
```

* 异步组件 async-component 只有组件需要被渲染的时候才加载该组件
```js
//全局注册
Vue.component('async-component',function(resolve,reject){
	setTimeout(function(){
		resolve({
			template:`<div>异步组件</div>`
		})
	},2000)
})

//局部注册  直接提供返回一个promise对象的函数
var app=new Vue({
	el:'#app',
	data:{},
	components:{
		'my-component':()=>import('./async-component')
	}
})
```

* 访问元素&组件
* 访问根实例 通过`$root property`方法实现,适合小型的有少量组件的应用
```js
this.$root.name		//获取根组件数据
this.$root.name='hh'	//写入根组件数据
this.$root.fn()		//调用根组件方法
```
* 访问父组件实例 推荐用 依赖注入 通过provide & inject选项
  通过`$parent property`方法访问父组件的实例,易失控
```js
var map=this.$parent.map || this.$parent.$parent.map
```

* 访问子组件实例 通过`ref`为子组件赋予一个id引用,可以直接操作dom节点,减少ref的使用
* ref 和 v-for 一起使用时,得到的ref是一个包含对应数据源的子组件的数组
* `$refs`只会在组件渲染完成后生效,不是响应式的,避免在模板或计算属性中访问$refs
```html
<my-input ref='username'></my-input>
```
```js
Vue.component('my-input',{
	methods:{
		getMsg(){ return this.msg}
	}
})
var app=new Vue({
	el:'#app',
	methods:{
		handle(){
			var msg=this.$refs.username.getMsg()
			return msg
		}
	}
})
```
--------------------------------------------------
7. 混入 mixin 可复用性
* 全局混入 使用全局混入会影响每一个单独创建的vue实例,慎用 推荐作为插件发布
* 组件与混入对象有同名选项时,组件优先级更高
```js
//全局混入
Vue.mixin({
	created:function(){ },
	mounted:function(){ }
})
var app=new Vue({
	el:'#app'
})

//局部混入 按需混入
var mixin={
	created:function(){ },
	data:function(){
		return {
			msg:1
		}
	}
}
var app1=new Vue({
	el:'#app1',
	mixins:[mixin]
})
```
--------------------------------------------------
8. 过滤器 filter
* 只可用于文本插值花括号和v-bind指令中
```html
<h1>{{money | rmb}}</h1>
<div v-bind:value='money | rmb'></div>
```
```js
//全局过滤器 放在vue实例前
Vue.filter('rmb',function(value){
	return '¥'+value
})

var app=new Vue({
	el:'#app',
	data:{},
	filters:{	//局部过滤器
		money:function(value){
			return '¥'+value
		}
	}
})
```
--------------------------------------------------
9. 自定义指令 directive
```html
<input v-focus>
```
```js
//全局自定义指令v-focus 自动聚焦
Vue.directive('focus',{
	bind:function(el,binding,vnode){
		//...只调用一次,此钩子函数可选
	},
	inserted:function(el){
		el.focus()
	}
})

//局部自定义指令
new Vue({
	el:'#app',
	directives:{
		focus:{
			inserted:function(el){
				el.focus()
			}
		}
	}
})
```
--------------------------------------------------
10. 事件总线 bus
* 订阅-发布模式
* 通过`bus.$emit()`和`bus.$on()`方法,实现子组件之间的直接通信
```js
var bus=new Vue()	//vue实例创建完成就会有一个bus对象
Vue.component('comp-a',{
	methods:{
		send(){
			//A发送消息
			bus.$emit('compA',this.msg)
		}
	},
	created:function(){
		//接收B发来的消息
		bus.$on('compB',(msg)=>{
			this.html += msg
		})
	}
})

Vue.component('comp-b',{
	methods:{
		send(){
			//B发送消息
			bus.$emit('compB',this.msg)
		}
	},
	created:function(){
		//接收A发来的消息
		bus.$on('compA',(msg)=>{
			this.html += msg
		})
	}
})

var app=new Vue({
	el:'#app'
})
```
--------------------------------------------------
11. 过渡&动画 <transition>
* vue过渡有6个状态, `v-enter` `v-enter-active` `v-enter-to` `v-leave` `v-leave-active` `v-leave-to`
```css
.fade-enter,.fade-leave-to{
	transition:opacity .5s;
}
```
```html
<div id="app">
	<button @click='show=!show'>显示/隐藏</button>
	<transition name='fade'>
		<p v-if='show'>vue</p>
	</transition>
</div>
```
```js
var app=new Vue({
	el:'#app',
	data:{
		show:true
	}
})
```
* 多个组件过渡,可用v-if/v-else,相同标签名切换时要设置key值
```html
<transition name='fade' mode='out-in'>
	<button v-if='show' key='1'>显示</button>
	<button v-else key='2'>隐藏</button>
</transition>
```
--------------------------------------------------
--------------------------------------------------
### 工程架构 项目环境搭建,项目初始化,本地服务
### 项目架构 项目需要的技术
### 业务开发 编写业务交互代码
### 项目部署 测试环境,打包上线

* 生产环境 production 项目部署到线上
* 开发环境 development 编写业务代码
* `npm install --save` 自动把模块和版本号加到dependencies,生产环境要用到的
* `npm install --save-dev` 自动把模块和版本号添加到devdependencies,开发环境要要用到

### 工程架构

# Vue脚手架搭建项目 Vue-CLI
1. 安装
```
npm install -g @vue/cli
# or
yarn global add @vue/cli
```
1.1 安装完成后用于检测vue/cli版本
```
vue --version
```

2. 创建一个项目
```
vue create vue-project
# or
vue ui
```

3. 启动项目
```
cd vue-project
npm run serve
# or
npm start (修改package.json文件中scripts命令 "start":"npm run serve")
```

4. 项目执行ESLint检测
```
npm run lint
```
* ESLint 代码是否符合规范的检测工具
[ESLint官网](https://eslint.bootcss.com/)
* 三种规则管理工具:
* off/0 关闭;
* warn/1 警告;（不会影响退出码）
* error/2 将规则视为一个错误 (退出码为1)
* vue项目中,修改ESLint验证规则:package.json文件中配置,配置完成后,重启服务器才生效
```
"eslintConfig":{
	"rules":{
		"no-console":0
	}
}
```

5. 项目打包上线		(项目部署阶段)
```
npm run build
```
* 生成一个 /dist 目录,将目录发送给运维工程师上线部署
* .map文件是静态资源的映射关系的配置文件
* .vue 单文件组件
* main.js 入口文件
* src/assets 项目的静态资源
* /public 静态资源服务器


6. 项目结构
6.1  /src开发目录
* 用`@`代表`/src`根目录,如'@/components/Home.vue'
* `src/main.js` 程序的入口文件
* `src/App.vue` app主组件	主组件中的自动生成的'id:app'不是挂载的'#app'
* `src/components` 组件目录
* `src/assets` 程序的静态资源目录
* `/public` 本地服务器的静态资源目录
* 引用`/public`中的静态资源时,直接用'/'表示'/public'根目录,如`/icon`
* `/dist` 执行`npm run build`生成的目录

6.2 .vue文件 单文件组件
* 结构
```.vue
<template lang="html">
	# html模板
</template>

<script> 
	# js代码
	import HelloComponent from './HelloComponent.vue'
	
	export default{
		//
	}
</script>

<style lang="scss" scoped>
	# css样式代码
</style>
```
* `scoped`表示作用局部
* 一个`.vue`文件就是一个组件
* SPA: 单页面web应用,加载单个html页面并在用户与应用交互时更新页面的应用
* SPA优点:前后端分离开发,服务器压力小,交互体验良好
* SPA缺点:SEO难度大,初次加载耗时多
--------------------------------------------------
### 项目架构

7. css相关 预处理器(Sass/Less/Stylus)
* 使用sass
* [sass官网](https://www.sass.hk/)
* 安装
```
npm install node-sass -D
npm install sass-loader -D

# 查看sass版本
sass -v
```
```
# .vue文件
<style lang="scss">
	@import '@/assets/css/common.scss';
	.app{
		&>div{
			color:$color1;
		}
	}
</style>

# common.scss文件
$color1:green;
```

* 若安装node-sass失败,使用以下命令进行安装:
```
npm install node-sass --sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
```
[node-sass 安装失败报错的原因及解决办法(整理)](https://www.cnblogs.com/gitnull/p/10188030.html)

--------------------------------------------------
8. 路由 Vue-Router
* 安装
```
npm install vue-router -S
```
```js
// /src目录下创建router.js文件
import Vue from 'vue'
import VueRouter from 'vue-router'

//Vue.use()注册路由
Vue.use(VueRouter)

//路由懒加载  使用vue异步组件,返回一个promise的工厂函数
const Home = () => import('@/views/Home.vue')

//创建router实例
const router=new VueRouter({
	mode:'hash',		//路由模式 hash history
	routes:[
		{
			path:'/',
			component:Home,
			//异步组件component:()=>import('@/views/Home.vue')
			name:'home'		//路由名称
		}
	]
})
export default router

//在main.js文件中将路由挂载在根实例上
import router from './router.js'
new Vue({
	router,		//缩写 router:router
	render:h=>h(App)
}).$mount('#app')
```

* 路由实现,使用`router-view`和`router-link`组件
```html
<div id="app">
	<!-- 声明式路由跳转 -->
	<!-- router-link组件相当于a链接 -->
	<!-- to 指定跳转到哪个路由 -->
	<!-- tag 指定用什么html标签来替换渲染router-link -->
	<!-- activeClass 指定导航选项卡的高亮样式 -->
	<!-- exact 精确匹配-->
	<router-link to='/home' tag='span' active-class='on' exact>Home</router-link>
	
	<!-- 路由出口 -->
	<!-- 路由匹配到的组件渲染在这里,相当于路由视图容器 -->
	<router-view></router-view>
</div>
```

* 路由模式 默认为hash模式
```
const router=new VueRouter({
	mode:'hash/history',
	routes:[...]
})
```
* hash模式
	url地址栏中拼接了一个'#',缺点是不够美观;
	部署到服务端不会有404这个问题,本质利用`location.hash`实现url跳转;
* history模式
	利用`history.pushState`方法完成url跳转,url中没有'#';
	打包部署到服务端,需要后端配合对路由进行处理,否则返回404;

* 路由命名视图 默认为default
```html
<router-view name='default'></router-view>
<router-view name='a'></router-view>
```
```js
routes:[
	{
		path:'/',
		components:{
			//一个页面中两个容器
			default:Home,
			a:User
		}
	}
]
```

* 路由命名与别名
* 路由别名等同于路由小名
```js
routes:[
	{
		path:'/user',
		component:User,
		name:'user',		//路由名称
		alias:'/my'		//路由别名
	}
]
```
```html # 可以给to属性传一个对象
<router-link :to="{name:'user',params:{id:01}}">User</router-link>
```
等价于
```js
this.$router.push({name:'user',params:{id:01}})
```

* 重定向
```js
routes:[
	{
		path:'/*',		//含有通配符的路由放在最后
		redirect:'/'		//重定向到首页
	}
]
```

* 动态路由	路径参数用`:`标记
* 嵌套路由 要配置`children`
```html
<div id="app">
	<!-- 第一层路由视图 -->
	<router-view></router-view>
</div>
```
```js
const User={
	template:`
		<div class='user'>
			<!-- 动态路径参数 -->
			<h2>User{{ $route.params.id }}</h2>
		</div>
		<!-- 嵌套第二层路由视图 -->
		<router-view></router-view>
	`
}
const router=new VueRouter({
	routes:[
		{
			//动态路径参数 以冒号开头
			//当匹配到一个路由时,参数值会被设置到 this.$route.params中
			path:'/user/:id',
			component:User,
			//当 /user/:id/student 匹配成功，
			//Student会被渲染在User的<router-view>中
			children:[
				{
					path:'student',		//子路由不要加`/` 
					component:Student
				}
			]
		}
	]
})
```

* 编程式路由跳转 router.push()
* vue实例内部可以通过`$router`访问路由实例,调用`this.$router.push()`
```js
//编程式 用于列表信息跳转
router.push({path:'/home'})
router.push({name:'user',params:{id:'11'}})
//如果提供了path, params会被忽略
this.$router.push('/user/'+id+'/'+name)

//声明式 用于导航选项
<router-link :to=''></router-link>
```
* router.replace()与router.push()很像,不同的是它不会向history添加新纪录,而是替换掉当前的history记录
```js
//编程式
router.replace()
//声明式
<router-link :to='' replace></router-link>
```

* 路由传参
```js
//用 this.$route.params 接收参数		$route可访问路由信息
export default{
	computed:{
		val(){
			return this.$route.params.value
		}
	},
	mounted:function(){
		console.log(this.$route.params.id)
	}
}

const router = new VueRouter({
  routes: [
    {
			path: '/user/:id/:value', //路径后用 : 
			component: User
		}
  ]
})
```
* `$router`与`$route`区别:
	`$router`是路由实例对象,包含了路由跳转方法,钩子函数等
	`$route`是路由信息对象,包括`params` `hash`等路由信息参数

* 路由守卫		一般用于用户登录前拦截
* 全局守卫: `router.beforeEach` `router.beforeResolve` `router.afterEach`
* 路由独享守卫: `beforeEnter:(to,from,next)=>{...}`
* 路由组件内守卫: `beforeRouteEnter` `beforeRouteUpdate` `beforeRouteLeave`

* 全局前置守卫	异步执行		一般用于管理系统
```js
const router=new VueRouter({...})
router.beforeEach((to,from,next)=>{
	//to:route 即将进入的路由目标对象
	//from:route 从哪个路由离开
	//next() : 进行管道中下一个钩子
	//next('/') next({path:'/'}): 跳转到一个不同的地址
})
```
```js
//用户验证身份失败,重定向到`/login`
router.beforeEach((to, from, next) => {
  if (to.name !== 'login' && !isAuthenticated) next('/login')
  else next()
})
```

* 局部守卫 组件内部实现路由拦截,常用于电商网站,个人中心登录注册
```js
const router=new VueRouter({
	routes:[
		{
			path:'/goods',
			component:Goods,
			beforeRouteEnter:(to,from,next)=>{
				//不能获取组件实例的`this`, 守卫执行前组件实例未被创建
				//在组件路由确认confirm前调用
				const isLogin=localStorage.getItem('isLogin')
				if(isLogin==1) next()
				else next('/login')
			}
		}
	]
})
```
* 登录成功 在`localStorage`中加`token`,重定向到`/`
* 退出登录 要移除`localStorage`中的`token`,重定向到`/login`
```js
//使用Element UI中的弹框组件
localStorage.removeItem('token')
localStorage.removeItem('isLogin')
this.$router.replace('/login')
```
--------------------------------------------------
9. 状态管理 Vuex  开发中大型单页应用
* 采用集中式存储管理应用的所有组件的状态,并以相应的规则保证状态以一种可预测的方式发生变化;
* 状态管理包含三个部分: state view actions
	state:驱动应用的数据源;
	view:以声明方式将state映射到视图
	actions:响应在view上的用户行为导致状态变化
* 应用核心为store(仓库),相当于一个容器,store包含着应用的state(状态)
* vuex响应式状态存储,不能直接改变store中的状态
* 改变store状态只能通过显式提交mutation的方式修改
* vuex核心技术:			
*  						Backend(后端API)
											|
			 _____________Actions_____________
			|		dispatch							commit	|
	Vue Components										Mutations <-->Devtools
			|___render_____State____mutate____|

* 完成前端静态页面布局后,先用假数据自测,再基于接口文档进行前后端接口联调
* 自测时可以用`/public`中的假数据测试接口,自行创建`/public/db/`
* 前后端接口联调:前端调取数据激活并在页面动态显示的过程
* 使用vuex,切换页面时不需重新调接口,有利于性能优化,vuex可以缓存数据

* 安装		(只要涉及到数据交互就用vuex) 
```
npm install vuex --save
```
* 核心概念:
* state	状态 在computed选项中引入

* mutations		在methods选项中引入
	改变store状态的唯一方法是提交mutation,
	mutations通过`$store.commit()`触发,状态改变会记录在devtools里
	mutation必须是同步函数

* actions  在methods选项中引入
	action提交的是mutation,不是直接变更状态
	action可以包含异步操作,调用后端接口
	actions通过`$store.dispatch()`触发

* getters  相当于store的计算属性,在computed选项中引入
	可以传参,第一个参数是state,第二个参数可以是其他getters(可选)
	获取getters中的值 如`$store.getters.info`
	
* modules 模块 将store分割成多个module 
	每个module都要添加`namespaced: true`使其成为带命名空间的模块
	尽量避免模块间命名冲突,以减少代码复杂性
```js
//创建 /src/store/index.js文件放总store
import Vue from 'vue'
import Vuex from 'vuex'

//引入所有子store
import userStore from './userStore.js'

//注册vuex
Vue.use(Vuex)

//创建store实例
const store=new Vuex.Store({
	modules:{
		userStore,
		homeStore,
		orderStore
	}
})
export default store

//在main.js中将store实例挂载在app上
import store from './store.js'
new Vue({
	store,
	render:h=>h(App)
}).$mount('#app')
```
```js
// 模块1:userStore.js
const userStore = {
	namespaced: true,		//添加命名空间
	state:{
		count:1,
		msg:'vuex'
	},
	getters:{
		info(state){
			return state.msg + '-hello'
		}
	},
	mutations:{
		add(state,payload){
			state.num += payload
		},
		changeMsg(state,payload){
			state.msg=payload
		}
	},
	actions:{
		msgAsync({commit}){
			setTimeout(()=>{
				commit('changeMsg','hello')
			},1000)
		}
		//等价于
		//msgAsync(userStore){
		//	setTimeout(()=>{
		//		userStore.commit('changeMsg','hello')
		//	},1000)
		//}
	}
}
export default userStore
```
```js
// .vue文件		在组件内引入模块

// mapState 映射 可一次获取多个状态
// 可以向$store.commit()中传入额外的参数,即mutation的载荷payload
// actions支持载荷,如`$store.dispatch('msgAsync',{amount:10})`
import {mapState, mapMutations, mapActions, mapGetters} from 'vuex'
export default{
	computed:{
		...mapState('userStore',['count','msg']),	//将this.count映射为this.$store.state.count
		//...{
		//	 count(){
		//	 	return this.$store.state.count
		//	 },
		//	 msg(){
		//	 	return this.$store.state.msg
		//	 }
		//}
		...mapGetters('userStore',['info']),	//将`this.info`映射为`this.$store.getters.info`
		
		//当orderStore和userStore中的state有重名时
		...mapState('orderStore',{
			orderMsg:(state)=>state.msg		//将orderStore中的msg输出为orderMsg
		})
	},
	methods:{
		...mapMutations('userStore',['add','changeMsg']),	//将`this.add()`映射为`this.$store.commit('add')`
		...mapActions('userStore',['msgAsync']),	//将`this.msgAsync()`映射为`this.$store.dispatch('msgAsync')`
		
		//当orderStore和userStore中的mutations有重名时
		...mapMutations('orderStore',{
			changeOrderMsg:(commit,payload)=>{
				commit('changeMsg',payload)		//将orderStore中的changeMsg输出为changeOrderMsg
			}
		}),
		//当orderStore和userStore中的actions有重名时
		...mapActions('orderStore',{
			orderMsgAsync:(dispatch)=>{
				dispatch('msgAsync')		//将orderStore中的msgAsync输出为orderMsgAsync
			}
		}),
		
		addClick(){
			this.add(100)  //等价于 this.$store.commit('add',100) payload=100
		},
		getMsg(){
			this.msgAsync() //等价于 this.$store.dispatch('msgAsync')
		},
		getOrderMsg(){
			this.changeOrderMsg('change order msg')
		},
		getOrderMsgAsync(){
			this.orderMsgAsync()
		}
	}
}
```
--------------------------------------------------
10. vue.config.js 配置参考文件
* 与 package.json文件同级,需要手动创建
* 改端口号,代理需要用vue.config.js(解决跨域)
* 使用代理后需要重启项目
```js
module.exports={
	devServer: {
		port:4000, //自定义前端端口号
		// proxy: 'http://localhost:4000' 代理到本机
	  proxy: {
	    '/api': { //根据关键字请求目标服务器
	      target: '<url>', //目标服务器url
				//ws: true, 	//websocket
	      changeOrigin: true
	    }
	  }
	}
}
```
--------------------------------------------------
11. Devtools工具		用于调试vue程序
* 提交mutation使得state改变,都会记录在devtools里
* 安装
```
# 克隆github地址:https://github.com/vuejs/vue-devtools.git
npm install /yarn install
npm run build / yarn run build
```
* 打开谷歌浏览器-设置-扩展程序-开发者模式-加载已解压的扩展程序-选择shells/chrome
* 设置好后需重启浏览器,即可在控制台调试vue

--------------------------------------------------
12. axios工具 调后端接口	基于promise对象
* 安装
```
npm install axios -S
```
* 封装axios方法
```js
//创建/src/utils/fetch.js文件存放axios方法
//创建/src/utils/api.js文件存放数据接口方法
import axios from 'axios'
import {Message} from 'element-ui'	//可以用element UI库中的`message`组件提示响应信息

var baseURL='http://localhost:8080'	//baseURL:要请求的服务端数据接口的baseurl,配置vue.config.js文件,代理到本机

//创建axios实例
const fetch = axios.create({		//fetch是一个promise对象
	baseURL:baseURL,
	timeout:5000,			//设置接口请求超时的时间
	headers:{'Content-Type': 'application/json;chartset=UTF-8'}		//指定数据提交的格式
})

//添加请求拦截器 发生在请求发起之前
fetch.interceptors.request.use(config => {
	//对请求进行处理
	var token=localStorage.getItem('token')
	config.headers.Authorization=token		//token用户鉴权
  return config
}, error => {
	//请求错误时
  return Promise.reject(error)
})

//添加响应拦截器 发生在客户端接收响应之前
axios.interceptors.response.use(response => {
	//对响应数据进行处理
  return response
}, error => {
	//响应错误时
  return Promise.reject(error)
})

export default fetch

//在main.js中将所有api.js中的接口方法导出挂载在Vue原型上,命名为$http
import http from '@/utils/api'
Vue.prototype.$http = http
//调用api中的接口方法changeList(),可通过$http直接调用,不用引入api.js
this.$http.changeList()
```
* get请求
```js
import axios from 'axios'
axios({
	method:'get',
	url:''
})
.then(res=>{
	console.log('res',res)
})
.catch(err=>{
	console.log('err',err)
})
.then(()=>{
	//最终都会执行
})
```
* post请求 用`data:{}`传参
```js
axios({
	method:'post',
	url:'',
	data:{
		name:'hugh',
		age:20
	}
})
.then(res=>{
	console.log('res',res)
})
.catch(err=>{
	console.log('err',err)
})
```
--------------------------------------------------
13. 使用Element ui组件库
* 安装
```
npm i element-ui -S
```
```js
//main.js文件
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
  el: '#app',
  render: h => h(App)
});
```
--------------------------------------------------
14. Font-Awesome	字体图标库
[Font-Awesome](http://fontawesome.dashgame.com/)
[BootstrapCDN](https://www.bootcdn.cn/) 提供开源CDN加速服务的网站

* CDN引入	引入到静态资源服务器`/public/index.html`中
```
<link href="//netdna.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
# 若失效则在`bootCDN`网站中找
<link href="https://cdn.bootcss.com/font-awesome/5.11.2/css/all.min.css" rel="stylesheet">
```
* 使用
```
# CSS前缀`fa`，再加上图标名称
<i class="fa fa-camera-retro"></i> fa-camera-retro(图标名)
```
--------------------------------------------------
15. momentjs	js日期处理类库
[momentjs](http://momentjs.cn/)
* 安装
```
npm install moment --save   # npm
yarn add moment             # Yarn
```
```js
import moment from 'moment'
moment().format('YYYY-MM-DD HH:mm:ss')	//获取当前时间 2020-02-02 02:02:02
```
--------------------------------------------------
--------------------------------------------------

# vue实现移动端webapp

1. 移动端用rem布局
* rem: html根元素的font-size
* 设备像素比 DPR(devicePixelRatio) dpr=1/2/3
* dpr=设备物理像素 / 设备独立像素(css代码像素)
* 设备物理像素=屏幕能显示的实际像素,设备独立像素=屏幕可视区域宽度
* 使用`window.devicePixelRatio`可以动态地获取到硬件设备的dpr

* 封装rem函数
```js
//创建rem.js文件,在`/public/index.html`中引入
function resetRootFZ() {
	var oHtml = document.querySelector('html')
	var w = oHtml.getBoundingClientRect().width
	//设置根字体的大小等于html节点的宽度的十分之一
	oHtml.style.fontSize = w / 10 + 'px'
}
resetRootFZ()

//当window窗口尺寸变化时,重新设置根字体的大小
window.addEventListener('resize', function() {
	resetRootFZ()
})
```
* 编辑器中安装px转换成rem的插件,设置其`fontSize=75`,即可将px自动转换成rem单位;
* `vs code`中的插件有`cssrem`,`px to rem`--设置--扩展--root fontSize ;
* `hbuilder`中 工具--设置--编辑器配置--px转rem比例 ;

* [使用WebApp meta标签](https://guide.aotu.io/docs/html/webapp.html)
* rem布局时,一定要指定`meta`标签:
```html
<meta name="viewport" content="width=device-width,initial-scale=1.0">
```
--------------------------------------------------
2. touch事件		移动端特有的事件
* Click事件在移动端，会有300毫秒延迟，用于区分移动设备上的单击、双击事件
* 给网页指定WebApp meta元数据后，可以降低click事件延迟时间
* Touch事件由`touchstart``touchmove``touchend`组件，仅在移动端Web中被支持，在PC Web中不支持
--------------------------------------------------
3. 移动端底部导航TabBar组件
* 在`Home` `Find` `User`等外页组件中引入,内页组件中不引入

* 自测时可以用`/public`中的假数据测试接口 `/public/db/`
--------------------------------------------------
4. vant (vue移动端ui组件库)
* 安装
```
npm i vant -S
```
* CDN引入(最简单的方法)
```html
<!-- 引入样式文件 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/vant@2.2/lib/index.css">
<!-- 引入 Vue 和 Vant 的 JS 文件 -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/vant@2.2/lib/vant.min.js"></script>
<script>
	// 在 #app 标签下渲染一个按钮组件
	new Vue({
		el: '#app',
		template: `<van-button>按钮</van-button>`
	});
	
	// 调用函数组件，弹出一个 Toast
	vant.Toast('提示');
</script>
```
```js
//在main.js中全局引入vant,注册
import Vue from 'vue';
import Vant from 'vant';
import 'vant/lib/index.css';

Vue.use(Vant);
```
```js
//使用swiper组件		如果vant全局注册就无需再引入swiper组件
import Vue from 'vue';
import { Swipe, SwipeItem } from 'vant';

Vue.use(Swipe).use(SwipeItem);

//实现图片懒加载
//autoplay属性设置自动轮播间隔 	配合 Lazyload 组件实现图片懒加载
<van-swipe :autoplay="3000">
  <van-swipe-item v-for="(image, index) in images" :key="index">
    <img v-lazy="image" />
  </van-swipe-item>
</van-swipe>
export default {
  data() {
    return {
      images: [
        'https://img.yzcdn.cn/vant/apple-1.jpg',
        'https://img.yzcdn.cn/vant/apple-2.jpg'
      ]
    }
  }
}
```
* 蓝湖 ui组件库
* Mint UI
--------------------------------------------------
--------------------------------------------------
# 1.服务端渲染 SSR

* 即在服务端把vue实例渲染成html返回给客户端
* 前后端不分离,对SEO友好,初次加载速度快
* 服务端渲染应用程序要处于`nodejs`运行环境,只支持`beforeCreate` `created`两个钩子函数
* 缺点:不灵活,前后端耦合程度高,服务端负载多
* 安装
```
npm install vue -S
npm install vue-server-renderer --save
```
* 使用 把vue实例渲染成html
```js
// 第 1 步：创建一个 Vue 实例
const Vue = require('vue')
const app = new Vue({
  template: `<div>Hello World</div>`
})

// 第 2 步：创建一个 renderer
const renderer = require('vue-server-renderer').createRenderer()

// 第 3 步：将 Vue 实例渲染为 HTML
//服务端渲染核心方法 renderToString() 只是把vue代码渲染成html字符串,不能做逻辑交互处理
renderer.renderToString(app, (err, html) => {
  if (err) throw err
  console.log(html)
  // => <div data-server-rendered="true">Hello World</div>
})
```

* BSR 客户端渲染
* 前后端分离,方便前后端各自维护
* 对SEO不友好,加载速度慢
--------------------------------------------------
# 2.Nuxt.js框架 基于vue.js开发SSR应用的框架
* 一个nuxt项目相当于一个vue项目融合一个nodejs server项目
* 安装
```
npm install --save nuxt
```
* 使用`create-nuxt-app`脚手架
```
npx create-nuxt-app <项目名>
```
* 目录结构
* `/pages`:用于组织路由及视图
* Nuxt路由:Nuxt.js 依据`pages`目录结构自动生成 vue-router 模块的路由配置
* 声明式路由:<nuxt-link>，支持`active-class`属性
* Nuxt嵌套路由:创建内嵌子路由，你需要添加一个 Vue 文件，同时添加一个与该文件同名的目录用来存放子视图组件
* Nuxt动态路由:创建对应的以下划线作为前缀的*.Vue 文件或目录,如`/pages/user/_id.vue`,`path:'/user/:id'`
* 编程式路由:`this.$router.push()`等等
* Nuxt视图:在`/layout`目录下的 default.vue 即根组件的模板了，用<nuxt>指定视图容器
* Nuxt子视图:<nuxt-child>用于渲染二级的子视图组件
* 在Nuxt项目中使用axios请求后端数据，使用`asyncData`属性
```js
// 异步数据请求
asyncData() {
  return axios.get(url).then(res=>{
    // 这里是无法访问当前组件的this对象
    console.log('this', this)
    console.log('res34', res.data.data.song.list.length)
    // 在这里return 的数据，在页面组件中可以直接使用
    return {
      list: res.data.data.song.list
    }
  })
}
```
* 在Nuxt项目中使用Vuex，Nuxt项目建议Vuex状态分模块（即多个module）
* 创建`/store`目录用于组织应用的vuex文件,`/store/index.js`根模块
```js
//将状态导出为函数，将变量和操作作为`store/index.js`中的对象导出
//`/store/todo.js`子模块
export const state = () => ({
  list: []
})
export const mutations = {
  add(state, text) {
    state.list.push({
      text,
      done: false
    })
  },
  remove(state, { todo }) {
    state.list.splice(state.list.indexOf(todo), 1)
  },
  toggle(state, todo) {
    todo.done = !todo.done
  }
}
```
--------------------------------------------------
# 3.项目部署
* 云服务器介绍
* 域名、IP地域、DNS域名解析器、域名备案等
* 如何把本地代码转移至远程服务器上？使用Git，或者使用其它文件上传软件
* 如何部署前端项目？使用Nginx
* 反向代理:用户不知道要访问的服务端地址
* 正向代理:用户知道要访问的服务端地址
--------------------------------------------------
# 4.vue项目性能优化
* 路由懒加载,使用异步组件
* 图片懒加载
* 不频繁切换用`v-if`,频繁切换用`v-show`
* `v-for`遍历加`key`,`v-for`不与`v-if`同时使用
* 第三方插件按需引入
* SSR服务端渲染
* 压缩代码,压缩图片
--------------------------------------------------
