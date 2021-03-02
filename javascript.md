# javascript
* 一种轻量级编程语言，与java无关，控制结构(html)和样式(css);
* 以事件驱动为核心的弱类型脚本语言;
* js书写方式
```
//行内
<input type="button" value="按钮" onclick="console.log('hello world')" />

//script标签
<head>
	<script>
		alert('hhh')
	</script>
</head>

//外部js文件引入   中间不能写js代码
<script src="main.js"></script>
```
* js输出
```
* window.alert() 
* document.write() //写入html输出,仅用于测试,html文档完全加载后使用将删除已有的html
* innerHTML  //写入html元素
* console.log()  //控制台
```
--------------------------------------------------
1.变量
* 计算机内存储数据的标识符，根据变量名称可以获取存储的数据；
* 使用变量可以方便的提取或修改内存中的数据；
* 变量声明：var
* 变量命名：由字母、数字、下划线、$组成，不能以数字开头；不能是关键字；区分大小写；
* 遵守驼峰命名法，如userName;
--------------------------------------------------
2.简单数据类型
* number:数值型
```
var num1=2;var num2=07;//八进制
NaN:not a number;//与任何值都不相等，包括它本身;
isNaN:is not a number;
```
* string:字符串型
```
console.log(str.length) //字符串长度
```
* boolean:布尔型
```
true/false  区分大小写
```
* undefined:只声明未赋值的变量
* null:空值
* 获取变量类型:typeof()
```
var name='aaaa';console.log(typeof('name'))
```
--------------------------------------------------
3.数据类型转换
```//转成字符串类型
* toString()
var num=1;console.log(num.toString());
* String()
var num=1;console.log(String(num))
* 拼接字符串 + -
num + '' //返回字符串
```
```//转换成数值型
* Number()
var name='hello';console.log(Number(name)) //返回NaN
* parseInt() 取整
* parseFloat() 取小数
* +,-,-0等运算符
var str='100';console.log(+str);console.log(-str);console.log(str-0);
```
```//转换成boolean型
* Boolean()
0,""'',null,undefined,NaN 转成 false;
其他转成true;
```
--------------------------------------------------
4.比较运算符
```
> < == === !===
== 与=== 区别: ==只比较值，===比较值也比较数据类型
```
5.赋值运算符
```
+= -= *= /=
+= var num=0;num += 5;//相当于num=num+5
delete 一元运算符 关键字 var obj={a:1,b=2} delete obj.a;
```
--------------------------------------------------
6.if语句
```
if(判断条件){
	//执行语句
}else{
	//否则执行语句
}
```
```//三元运算符
var num = num % 2 === 0 ? "偶数":"奇数";
```
--------------------------------------------------
7.switch语句
```//查询周几
var day=10;
switch (day){
	case 1:
	console.log('周一');
	break;
	case 2:
	语句;
	break;
	...
	default:
	console.log('输入的值不在查询范围内');
	break;
}
```
* continue : 跳出当前循环，继续下一次循环;
* break : 跳出整个循环,循环结束;
--------------------------------------------------
8.循环语句
```//while语句
while(循环条件){
	//循环体   条件为true,执行循环体;
}
```
```//do...while语句
do{
	//循环体
}while(判断条件); //先执行再判断条件
```
```//for语句
var sum=0;
for(var i=1;i<=100;i++){
	//循环体
	sum += i;
}
console.log(sum);
```
--------------------------------------------------
9.数组 `array`
* 多个元素(同一类型)按一定顺序放入一个集合中;有序列表;
* js中,数组即对象,typeof(),返回object;
```//创建数组
var arr=[1,2,3,4,5];
var arr=new Array('a','b','c');
* 数组长度 arr.length;
* 数组索引 arr[0],arr[arr.length-1];
* 数组新增 arr[arr.length]='d';
```
```//遍历数组:对数组每个元素都访问一次;
for(var i=0;i<arr.length;i++){
	console.log(arr[i])
}
```
* 数组常用方法:
* 增删改查
```
arr.shift():删除最前面一个元素,返回被删除的元素;
arr.unshift():最前面增加一个元素,返回数组新长度;
arr.push():最后面增加一个元素,返回数组新长度;
arr.pop():删除最后一个元素，返回被删除的元素;
```
```
arr.splice(a,b):从第a位开始,删除b位,返回值是被删除元素的集合;
arr.splice(a,b,c):从第a个开始,删除b个,用c替换,返回被删除元素的集合；
arr1.concat(arr2):连接数组;
arr.reverse():翻转数组,返回翻转后的数组;
arr.join():数组换成字符串,可自定义连接符'-';
str.split():字符串转成数组;
arr.sort():对数组进行排序;
	arr.sort(function(a,b){	//用比较函数进行排序
		return a-b;//从小到大,升序
		return b-a;//从大到小,降序
	})
```
* 有兼容性问题的方法
```
//查找元素		返回索引号
arr.indexOf(a,b):查找a元素,从第b个开始查,返回第一个符合条件的元素索引,若无则返回-1;
arr.lastIndexOf(a,b):从后往前查 ;
```
* 数组遍历
```//for循环
for(var i=0;i<arr.length;i++){
	console.log(arr[i])
}
```
```//for..in循环
for(var index in arr){
	console.log('第'+index+'个元素是'+arr[index])
}
```
```//forEach()		无返回值
arr.forEach(function(value,index){
	console.log('第'+index+'个元素是'+value)
})
```
```//map()		返回值为当前方法的返回值
var arr2=arr.map(function(value,index){
	return index*value;
})
console.log(arr2);//返回新数组
```
```//filter()		过滤,返回符合条件的值
var arr2=arr.filter(function(value,index){
	return index % 2 ===0;
})
```
```//for...of
for(var value of arr){
	console.log(value);
}
```
--------------------------------------------------
10.函数 `function`
* 把一段相对独立的代码块封装起来，形成一个独立实体
* 作用:封装代码，可重复使用
* 函数声明
```//	函数声明时不会执行，只有调用时执行
function 函数名(){
	//函数体
}
	//函数表达式
	var fn=function(){
		//函数体
	}
```
* 调用函数
```
function fn(){
	var sum=0;
	for(var i=1;i<=100;i++){
		sum += i;
	}
	console.log(sum)
}
//调用 
fn();
```
* 匿名函数
```// 没有函数名的函数
(function(){
	console.log('匿名函数')
})()
* 匿名函数执行方法:函数自调用、通过事件函数调用
```
* 函数的参数:形参 实参
```
function fn(m,n){
	for(var i=m,sum=0;i<=n;i++){
		sum += i;
	}
	console.log(sum)
}
fn(a,b);
m n为形参，a b为实参;
形参没有具体的值，只起占位的作用;
函数声明时设置了形参，调用时需要传入对应的参数，传入的参数为实参;
```
* 函数通过`return`来返回值
```
function fn(m,n){
	for(var i=m,sum=0;i<=n;i++){
		sum += i;
	}
	return sum;
}
fn(a,b);
* 函数执行完`return`后会立即结束函数,return后的代码不会执行;
```
* arguments
```
* 函数内置属性，arguments对象中存储了传递的所有实参，一个伪数组,可以遍历;
function Max(){
	var max=arguments[0];
	for(var i=0;i<arguments.length;i++){
		if(max < arguments[i]){
			max=arguments[i]
		}
	}
	return max;
}
Max(1,2,3,...,n);
```
* 作用域 : 变量起作用的范围
* 全局变量:作用于全局作用域;
* 局部变量:作用于局部作用域,如函数作用域;函数中声明的变量，是函数的局部变量，只能在函数内部访问;
	函数内部定义的变量从函数外部是不可访问的;
* 块级作用域: es6中定义,{}中的代码块区域;
* 预解析:js代码执行前的过程;
			提升变量声明，不会赋值;提升函数声明,不会调用;
--------------------------------------------------
11.事件 `event`
* 事件三要素:事件源、绑定事件、事件驱动程序
```
事件源.事件=function(){
	事件驱动程序
}
```
* 事件名
```
onclick 鼠标单击; ondblclick 鼠标双击;
onkeyup 按下释放键盘; onchange 内容改变;
onfocus 获取焦点; onblur 失去焦点;
onmouseover 鼠标悬停/ onmouseout 鼠标移出;
onload 网页加载; onunload 关闭网页;
onsubmit 表单提交; onreset 表单重置;
onmouseleave / onmouseenter;
onmousemove 鼠标移动; 
```
```//js入口函数
window.onload=function(){
	//页面加载完成才执行此处，一个页面只写一次
}
```
```
div.innerHTML=input.value; //改变div标签的内容;	获取表单的值value;
input.value.trim(); //trim()  去除字符串前后空格
```
--------------------------------------------------
12.对象 `object`
* 一组无序键值对的集合，属性如无特殊说明，都为字符串;
* 创建对象
```
var obj={
	name:'hugh',	//属性:值
	age:'12',
	height:'180'
}
console.log(obj.name);//name是字符串
console.log(obj[name]);//undefined [name]是变量name;

//new一个对象
var person=new Object();
person.name='hugh';
person.age=12;
```
* Math对象
```
Math.PI π; Math.pow(r,2) 取平方;
Math.random() 取0-1之间的随机数,不能取到1;
Math.floor() 向下取整; Math.ceil() 向上取整;
Math.round() 四舍五入; Math.abs() 取绝对值;
```
* json格式
* 轻量级数据交换格式;严格的js对象格式;属性必须用双引号"";
```
var student={
	"name":"hh",
	"id":123,
	"age":18
}
```
* 遍历对象
```
var obj={
	a:'111',
	b:'222',
	c:'333'
}
for(var key in obj){
	console.log(obj[key]);
}
for(var val of obj){
	console.log(val);//报错
}
```
--------------------------------------------------
13.复杂数据类型
* object function array
* 复杂数据类型变量存储的是地址,简单数据类型存储的是值;
* 堆 : 存储复杂数据类型; 栈 : 存储简单数据类型;

* 浅拷贝		b复制a, 改变a, b也随之改变, 这是浅拷贝;
	b=a 复制的是a的引用地址,并非堆里的值,a与b指向的地址相同,a改变,b也就改变;
```
let a=[0,1,2,3];
		b=a;
		a[0]=1;
console.log(a);//[1, 1, 2, 3]
console.log(b);//[1, 1, 2, 3]
```
* 深复制		b复制a, 改变a, b不变, 这是深复制;
	深复制只针对object类型的数据		且复制的是对象各个层级的属性;
```实现深复制的三个方法:
1.通过递归函数复制所有层级的属性

2.借用JSON.parse()和JSON.stringify()方法
function deepClone(obj){
	let obj1=JSON.stringify(obj)
	objClone=JSON.parse(obj1)
	return objClone;
}
let a=[0,1,2,[3,4],5];
b=deepClone(a);
a[0]=1;
a[3][0]=4;
console.log(a);//[1,1,2,[4,4],5]
console.log(b);//[0,1,2,[3,4],5]

3.jQuery中的extend方法
	$.extend([deep],target,obj1)
	deep 是否深复制 true为深复制
let aa=[0,1,[2,3],4];
bb=$.extend(true,[],aa);
aa[0]=1;
aa[2][0]=3;
console.log(aa);//[1,1,[3,3],4]
console.log(bb);//[0,1,[2,3],4]
```
--------------------------------------------------
14.es5严格模式
* "use strict":消除代码运行不安全之处,增加运行速度;

* 严格模式下 `this`为undefined;
--------------------------------------------------
15.字符串API
* 字符串定义
```
var str="hello world";
var str=new String("hello world");
str.length:字符串长度,包括空格数;
```
* 常用方法
```
str.split():字符串变数组,参数为分隔符;
str1.concat(str2):连接两字符串;
str.toLowerCase():转小写;
str.toUpperCase():转大写;
str.trim():去除字符串两端空格;
str.replace('a','b'):用'b'替换'a',只替换首个匹配;
```
* 给字符查索引	indexOf() lastIndexOf()	找不到返回-1
```
str.indexOf():参数为字符,返回该字符的索引,从前往后
str.lastIndexOf():参数为字符,返回该字符的索引,从后往前
```
* 给索引查字符  参数为字符位置
```
str.charAt(1):返回字符;
str.charCodeAt(1):返回字符编码,若无字符返回NaN;
String.fromCharCode(104):从字符编码创建一个字符串;
数字编码范围:47-57;
大写字母编码范围:65-90;
小写字母编码范围:97-122;
```
* 字符串截取		str.slice()
```
str.slice(m,n):参数 截取开始的索引，截取结束的索引，包前不包后;
str.slice(0):从第0个到末尾;
str.slice(-2):从倒数第2个到末尾;
str.slice(5,2):前大后小，空;
```
```
str.substr(截取开始的索引,截取长度)
str.substr(0,2):从第0个开始，截取2位;
str.substr(-2):从倒数第2个到末尾;
```
```
str.substring(截取开始的索引,结束的索引)
(a,b):包左不包右；
(2):从第2个到末尾;
(5,2):自动转换成(2,5);
(-3):获取全部字符;
```
--------------------------------------------------
16.Date对象
```
var date=new Date(): 返回当前时间;
var date=new Date(0): 1970.1.1 08:00:00;

date.getFullYear() :获取当前年份;
date.getMonth() :获取当前月份(从0-11);
date.getDate() :获取当前日期;
date.getHours() :获取当前时;
date.getMinutes() :获取分钟;
date.getSeconds() :获取秒;
date.getDay() :当前星期几,从周日开始,0-6;
date.getTime() :距离1970.1.1零点的毫秒数;
//距离1970.1.1零点的毫秒数
+new Date();
Date.now();
new Date().valueOf();
```
--------------------------------------------------
17.BOM对象(浏览器对象)
* window对象
```//API
window.innerHeight/innerWidth	:浏览器窗口内部高/宽(包括滚动条);
window.location	:地址信息;
navigator.appName 浏览器名称;
alert()
confirm();
history.forward() 向前一页;
history.back() 退回一页;
```
* 可视区域浏览器宽/高
```
* 判断模式
console.log(document.compatMode);

* 标准模式 CSS1Compat
document.documentElement.clientWidth/clientHeight

* 怪异模式 BackCompat
document.body.clientWidth/clientHeight
```
* 滚动距离
```
document.documentElement.scrollTop
document.body.scrollTop

document.documentElement.scrollLeft
document.body.scrollLeft

* 页面被卷曲的宽/高
window.pageXOffset/window.pageYOffset
```
* 获取元素宽/高
```
offsetWidth/offsetHeight :不带单位;
```
--------------------------------------------------
18.定时器
```
setTimeout() :定时一次;
setInterval() :间隔循环;(闹钟)

定时器名称 = setInterval(函数,毫秒);
timer=setInterval("change()",1000,参数);

timer=setInterval(function(){
	//
},1000)

* 清除定时器
clearTimeout(定时器名)
clearInterval(定时器名)
```
--------------------------------------------------
19.DOM对象(文档对象)
* 选择器
```
var header=document.getElementById(id);
document.getElementsByTagName('标签') :返回一个数组;
document.getElementsByClassName('类名') :返回一个数组;IE8以下不能使用

document.querySelectorAll('li.one'):选中的是一个集合;
document.querySelector('li'):返回符合条件的第一个节点;
```
* 获取和设置元素内容
```
div.innerHTML="<h1>h1</h1>";//能识别标签
div.innerText="<h1>h1</h1>";//不能识别标签
```
```
header.tagName :返回标签,全大写;
header.id;
header.className;
header.title;
header.href;
header.属性='属性值':设置属性;
console.dir(header);打印
```
* 属性操作
```
header.setAttribute('属性名','属性值');
header.getAttribute('属性名'):返回属性值;
header.removeAttribute('属性名');

* h5自定义属性
<div data-index="1"></div>
div.dataset.index :1;
div.dataset["index"]=2;//设置属性值
```
* DOM节点

* 整个文档是一个文档节点 每个HTML元素是元素节点 HTML元素内的文本是文本节点(回车也是文本节点);
* 每个HTML的属性是属性节点 注释是注释节点;
* nodeType 返回一个整数，这个数值代表节点的类型;
```
元素节点  返回 1      
属性节点  返回 2      
文本节点  返回 3       
注释节点  返回 8      
文档节点  返回 9
文档类型节点		10	document.doctype	nodeType:10 html null
文档碎片节点		11	document.createDocumentFragment() 创建文档碎片节点
```
* nodeName 节点的名称
```
元素节点 :标签名称(大写)
属性节点 :属性名称
文本节点 :#text
注释节点 :#comment
文档节点 :#document
```
* nodeValue 节点的值
```
元素节点 :返回值是 undefined 或 null
文本节点 :返回文本内容
属性节点 :返回属性值
注释节点 :返回注释内容
文档节点 :返回 null
元素节点 :用 innerHTML/innerText/value 设置或取值
```
* div.childNodes : div的所有子节点 只算第一层的;
* div.children : 当前元素的所有子元素节点(无兼容性问题);
* div.parentNode : 当前元素的父元素(无兼容性问题);
* div.previousSibling : div前一个兄弟元素;
* div.nextElementSibling : div后一个兄弟元素 ie678不支持;
* div.previousElementSibling : 前一个类型为元素的兄弟 ie678不支持;
* div.firstElementChild : div的第一个类型为元素的子节点;
* div.lastElementChild : div的最后一个元素子节点;

* 节点操作
```
* 创建一个元素节点
var newLi=document.createElement('li');

* 给节点li添加内容
li.innerHTML="hhhhh";

* 克隆节点
newLi=li.cloneNode(true);

* 给节点最后插入一个子元素
ul.appendChild(li)

* 把newLi插到li之前
ul.insertBefore(newLi,li);

* 删除子节点
ul.removeChild(newLi);

* 自删
newLi.remove();
 
* 创建文档碎片节点
var df=document.createDocumentFragment()
```
* 元素样式操作
```
* 获取元素宽高
div.offsetHeight/div.offsetWidth;

* 只能获取行内式样式
div.style.width/div.style.bakcground

* 获取元素所有样式 第一个参数是要获取样式的元素
window.getComputedStyle(div,null).width : ie有兼容问题;
window.getComputedStyle(div,"before").color :第一个参数是要获取样式的元素 第二个参数是伪元素;

div.currentStyle["width"] :IE支持,谷歌不支持;
div.currentStyle.height;
```
--------------------------------------------------
20.事件对象 Event
* 只有事件发生时才产生事件对象;
* 事件对象的兼容写法:
```
var event = window.event || e;
```
```
* 鼠标距离页面可视区域距离
clientX/clientY

* 鼠标距离页面距离=鼠标距离页面可视区域距离+滚动距离
pageX=event.clientX+scroll().left;
pageY=event.clientY+scroll().top;

* 元素距离最近的有定位的父元素的距离
offsetLeft/offsetTop

* offsetLeft/left区别
offsetLeft=div.offsetLeft;不带单位 不可赋值 取整 输出为number型;
left=div.style.left;带单位 可赋值 可为小数 输出为string型;

* 鼠标在div里的坐标=鼠标距离页面距离-元素距离最近的有定位的父元素的距离
var x=pageX-offsetLeft;
var y=pageY-offsetTop;

* offset screen
 鼠标在div里的坐标(只适合div内部元素为空的情况,不建议用)
x=event.offsetX || event.layerX;
y=event.offsetY || event.layerY;
 鼠标距屏幕的距离
event.screenX / event.screenY;
```
* 鼠标事件
```
onload 页面完全加载后在window对象上触发;
onunload 页面完全卸载后在window对象上触发;
onmouseover / onmouseout;
onmouseenter / onmouseleave;//不会冒泡
onmousemove; onmousedown / onmouseup; //此3个事件生成拖拽效果
onchange; 
oncontextmenu 右键菜单;
oninput 文本框中增加或减少哪怕一个字符也会触发该事件;oninput=onpropertychange;
onbeforeunload;//页面关闭或刷新时的提示;

event.button:0(左) / 1(中) / 2(右)		谷歌浏览器;
						 1		2		4		IE浏览器;
event.target||event.srcElement(ie)	触发事件的对象;
```
* 键盘事件
```
onkeydown / onkeyup / onkeypress;
var code=event.keyCode || event.which;//获取按下的字符的编码;
string.fromCharCode(code);//转成字符串
```
* 组合键事件
```
event.ctrlKey :ctrl+键;
event.altKey :alt+键;
event.shiftKey :shift+键;
```
** 事件绑定
```
事件监听器 : addEventListener (IE8以下不支持)
dom.addEventListener(type,function,false);

dom.attachEvent("on"+type,function)	(ie8以下);
```
** 事件机制(按顺序):事件捕获、事件目标、事件冒泡;
* 事件冒泡:子元素发生的事件,会冒泡到父元素上,并会一直往上冒,方向是由目标元素往上级
```
事件冒泡中,最内侧元素先被处理，再处理外侧元素;

* 阻止冒泡
event.stopPropagation() || event.cancelBubble=true	(ie浏览器);
```
* 事件捕获:事件从顶端向最小的元素捕获
```
事件捕获中，最外侧元素先被处理，再处理内侧元素;
```
```
dom.addEventListener(event,function,false);
第一个参数:事件类型;
第二个参数:事件发生时的调用函数;
第三个参数:false 冒泡传播; true 捕获传播;

* 删除事件监听器
ele.removeEventListener();
```
* 阻止浏览器默认行为
```
if(event.preventDefault){
	event.preventDefault()
}else{
	return false;//IE浏览器
}

* oncontextmenu 右键菜单事件时要阻止默认行为;
* 阻止浏览器默认行为不会阻止冒泡;
```
* 事件委托
```
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>
点击不同'li',对应不同操作,li的事件会冒泡到ul上,则可把li的事件绑定到ul上,即为事件委托;
ul.onclick=function(e){
	//获取触发事件的li
	var target=event.target||event.srcElement;
}
```
--------------------------------------------------
21.正则表达式 regular expression
* 声明
```
var 变量名=/表达式/;
var 变量名=new RegExp(str,"i");
```
* 预定义类
```
\d	数字0-9;
\D	非数字;
\s	空格;
\S	非空格;
\w	字母数字下划线;
\W	非字母数字下划线;
.		除换行回车外的所有字符;
g		修饰符	表示全局匹配;
i 	不区分大小写;
\		转义符;
```
* 使用正则的方法
```
* test()	返回true/false
/\d/.test('hh1223');//返回true
/\s/.test('hhhhh');//返回false

* exec()	返回一个数组，存放匹配的字符,不符合返回null;

* search()	匹配成功返回索引,失败返回-1;

* match()		返回符合的数组,不成功返回null;

* str.replace(reg,替换词)		用作屏蔽关键字;
	str.replace(/sb/gi,"**");
```
* 量词
```
* ? 可有可无	var reg1=/a?/;

* *至少出现0次	var reg2=/a*/;

* +至少出现1次	var reg3=/a+/;

* {n}表示重复出现n次	var reg4=/a{2}/;

* {m,n} 表示重复m到n次	var reg5=/a{3,5}/;

* {4,}表示重复4次以上		var reg6=/\d{4,}/g;
```
```
^	开始
$	结束

^$ 精准匹配;
var reg=/^he$/gi;
```
* 范围类
```
| 表示或者;	var reg1=/^(0|1|2|3|4|5|6|7|8|9)$/

^在[]里面表示取反 var reg4=/^[^1-46-9a-zA-Z]$/;

[abc]	查找[]中任意字符;var reg5=/[0-9]/;//0-9之间任意一个数;

reg6=/[\u4E00-\u9FA5]/	中文检测;
```
--------------------------------------------------
22.es6
* json语法
```
* json数据转为字符串
str=JSON.stringify(json);

* 类json字符串转为json数据
json=JSON.parse(str);
```
* let
```
* 声明变量,作用于块级作用域;
* es6的块级作用域必须有大括号{};
* 不存在变量声明提升,let声明的变量一定要在声明后使用，否则报错;
* 不能预解析,不能重复定义变量;
* let和const不出现变量提升的原因是 防止在声明变量前就使用该变量;
```
* const
```
* 声明一个只读的常量,一旦声明必须赋值,否则报错,声明后常量的值不变;
* 只作用于块级作用域;
* 不存在变量声明提升,不能预解析;
* 不可重复声明变量;
```
* class
```
* 可看做一个语法糖,类的数据类型是函数;
```
* 箭头函数
```
* 一般形式函数	
var fn=function(){
	console.log('function')
}

* 箭头函数
var fn=()=>{
	console.log('箭头函数');
}
* 只有一个形参,可忽略()
var fn=a=>{
	console.log('a')
}
fn(1);
* 函数主体只有一句话,可省略{}
var fn=a=> console.log('箭头函数');
* 若函数主体里只有一句话,且是return,则可以省略return和{};
var fn=(a,b)=> a+b;//var fn=(a,b)=>{return a+b};
```
* this指向
```
* 普通函数this指向window;
* 事件函数this->事件源;
	div.onclick=function(){
		console.log(this);//div
	}
* 严格模式下,普通函数this->undefined;
* 构造函数,this->实例化对象;
	var obj=new People(){
		this.name='11';//实例化对象
	}
* 函数是对象的方法,this->方法的调用者即实例化对象; window.GetName(){ this.name }
* 定时函数 setTimeout(function(){console.log(this)},1000)		this->window;
* 箭头函数不改变this的指向;
```
* 参数打包		...arr	合并数组和对象,必须放在最后一个
```
var fn=(x,...arr)=>{
	console.log(arr)
}
fn(1,2,3,4,5,6,7);

var arr1=[1,2,3];
var arr2=[4,5,...arr1];
var obj={...obj1,...obj2};

```
* 解构赋值
* 从数组和对象中提取值，对变量进行赋值，称为解构;
```
* 数组的解构赋值
	数组的元素是按次序排列的，变量的取值由其位置决定;
let [1,2,3]=[a,b];
//a=1,b=2;

* 对象的解构赋值
let {foo,bar}={
	foo:'a',
	bar:'b'
}
let {foo:bar}={
	foo:'a',
	bar:'b'
}
//bar:'a',foo:undefined;
foo是匹配的模式，bar才是变量，真正被赋值的是变量bar;
```
* es6模板字符串
```
var name="hugh";
var age=12;
console.log('name'+name+',age'+age);
console.log(`name${name},age${age}`);
```
* Array.from()	把类似数组的对象和可遍历对象变成真正的数组
```
var li=document.getElementsByTagName('li');
liArr=Array.from(li);

//生成m个n的数组
function fn(m,n){
	var arr=Array.from({length:m},()=>{return n});
	console.log(arr);
}
```
* Set 类似于数组，但是成员的值都是唯一的，没有重复的值
```
* 可用于数组去重
var arr=[1,1,1,1,2,2,3,4,5];
var set=new Set(arr);

* set.size()	set实例长度
* set.add(value)	添加某个值
* set.delete(value)	删除某个值
* set.has(value)	判断set里是否有某个值,有返回true,无返回false;
* set.clear()		清空set数据
```
* Symbol类型
```
隐藏对象中的键值对
var obj={
	a:'1',
	b:'2'
}
var attr=Symbol();
obj[attr]="zhizhi";
console.log(obj);//Symbol():"zhizhi"
```
* promise函数(异步)

* es6 export/import
```
export default function fn(){
	//输出...
}
import fn from './fn.js';  //引入
//export default 默认输出，一个模块只能使用一次，对应的import命令之后不用使用大括号{};
```
```
export function fn(){
	//输出...
}
import {fn} from './fn.js';  //引入
```
```
import * as obj from './obj.js';//引入所有方法命名为obj
import {aa as ee} from './obj.js';
import {aa,bb,cc} from './obj.js';
```
--------------------------------------------------
23.物体运动
```
* 封装匀速运动函数
function animation(dom,target){
	clearInterval(dom.timer);
	dom.timer=setInterval(function(){
		var current=dom.offsetLeft;
		var speed=current>target?-5:5;
		var next=current+speed;
		if(Math.abs(current-target)<=5){
			dom.style.left=target+'px';
			clearInterval(dom.timer);
		}else{
			dom.style.left=next+'px';
		}
	},20)
}

* 封装透明度运动函数
function move(dom,target){
	clearInterval(dom.timer);
	dom.timer=setInterval(function(){
		var current=getStyle(dom,"opacity")*100;
		var speed=target>current?5:-5;
		var next=current+speed;
		if(Math.abs(next-target)<=5){
			dom.style.opacity=target/100;
			dom.style.filter="alpha(opacity="+target+")";
			clearInterval(dom.timer);
		}else{
			dom.style.opacity=next/100;
			dom.style.filter="alpha(opacity="+next+")";
		}
	},100)
}

* 缓动函数
function move(dom,target){
	clearInterval(dom.timer);
	dom.timer=setInterval(function(){
		var current=dom.offsetLeft;
		var speed=(target-current)/10;
		speed=speed>0?Math.ceil(speed):Math.floor(speed);
		var next=current+speed;
		if(next==target){
			dom.style.left=target+'px';
			clearInterval(dom.timer);
		}else{
			dom.style.left=next+'px';
		}
	},20)
}

```
--------------------------------------------------
24.php	后台语言
* 服务器:提供某种服务的机器(计算机);
* 服务器软件:apache、nginx、nodejs;
* HTTP服务器:网站服务器,安装apache、nginx等服务器软件;
* 客户端: 服务端-->客户端		http客户端软件 浏览器;
* 前端开发:以浏览器为宿主环境,结合html css js等语言的开发;

* ip地址:给每个连接在互联网上的主机分配的一个32位地址 数字组成;
* 域名:ip地址的代号;
* DNS服务:ip地址和域名对应的服务;
* 端口:计算机与外界交流的出口;常见端口号:80 8080 3306;

* 搭建http服务集成环境
```
* 安装phpstudy;//安装后计算机成为一个web服务器
* 将网页文件copy到phpstudy/phptutorial/www根目录下,直接访问127.0.0.1(本机)即可;
* 本机访问本机 127.0.0.1 / localhost ;
* 不输入具体文件名,默认进入index.html;
```
* php基础
```
* 以 .php结尾,需要安装phpstudy解析php文件;
* 变量必须以 $ 开头,代码用 ; 结尾;
* 函数,条件,循环,注释,运算符都和js类似;
* 引入php文件 require('./login.php');/include('./login.php')
<?php
header('content-type:text/html;charset=utf8'); //解析中文字符
$a="hello world";
echo "hello world";

?>
```
* php操作数据库
```
* 安装navicat工具建立mysql数据库;
```	
--------------------------------------------------
25.http协议 超文本传输协议
* 由请求和响应构成;
* 客户端-->服务端 请求 request;
```
* 常用请求方法 POST GET PUT DELETE;
* 请求行		由请求方式、请求url、协议版本构成;eg:get/index.php http/1.1;
* 请求头		Host:请求主机 ...;
* 请求主体	传递给服务端的数据;
```
* 服务端-->客户端 响应 response;
```
* 状态行		协议版本号、状态码、状态信息;eg:http/1.1 200 ok;
	状态码:	200 成功;304 文档未修改;403 无权限;404 未找到;500 服务器错误;
* 响应头
* 响应主体	服务器返回给客户端的内容;
```
--------------------------------------------------
26.cookie
* 客户端--->服务端(请求)	服务端--->浏览器(cookie);
* 特点:
* cookie大小有限制,一般4kb,根据浏览器不同稍有不同;
* 数量限制,一般50条左右;
* 访问有限制,不能跨域访问;
* 时效限制,最短时效为会话级别(默认,浏览器关闭即销毁);
```
setcookie('username',$username,time()+24*3600);
setcookie('password',$password,time()+24*3600);
```

* session:存储用户信息;
* session存储在服务器中,cookie存储在本地浏览器,存在服务器中的数据更安全,但也会占用服务器资源;

* cookie与session结合使用:
* 存储在服务端,cookie中保存一个session id,具体数据保存在session中;
* 将session数据加密,保存在cookie中;

* localStorage/sessionStorage:
* localStorage 本地存储 string型;
```
window.localStorage.setItem(key,value);
window.localStorage.getItem(key);
window.localStorage.removeItem(key);
window.localStorage.clear();//全部清除

* 新事件 window.addEventListener('storage',function(){
	//只能监听到不同页面的事件
})
```
* sessionStorage 临时存储;
--------------------------------------------------
27.AJAX 异步编程
* 利用js发送异步的http请求:异步的javascript和xml;
* 异步:某程序执行时不会阻塞其他程序的执行,程序执行顺序不依赖其书写顺序;
	优势:提高整体执行效率;
* 异步函数:ajax回调函数、事件的回调函数、定时函数;
```
* 创建ajax对象
var xhr=new XMLHttpRequest;

* 发送ajax请求(get)
xhr.open('get','http://localhost/login.php?username='+uname.value+'&password='+pw.value);//请求行
//请求头		get可以不写
xhr.send(null);//请求主体

* post请求
xhr.open('post','./login.php');
xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
xhr.send('username='+uname.value+'password'+pw.value);

* 接收响应
xhr.onreadystatechange=function(){
	if(xhr.readyState==4&&xhr.status==200){
		console.log(xhr.responseText);
	}
}

xhr.onload=function(){//不建议用,xhr.status=404时后台也会打印
	console.log(xhr.responseText);
	console.log(JSON.parse(xhr.responseText));
}
```
* XMLHttpRequest对象API	xhr对象不允许跨域访问
```
xhr.open():请求行;
xhr.setRequestHeader():请求头;
xhr.send():请求主体;
xhr.onreadystatechange=function(){
	//监听响应状态
	xhr.readyState=0/1/2/3/4;//初始化xhr对象(0),发请求(1),响应头(2),响应主体(3),响应完成(4)
	xhr.status:响应码,200/404/500;
	xhr.statusText:响应信息,ok/not found/server error;
	xhr.getAllResponseHeaders():获取全部响应头信息;
	xhr.responseXML/xhr.responseText(字符串):响应主体;
}
```
* xhr对象的事件
```
var xhr=new XMLHttpRequest;
xhr.open('get','./login.php',true);//第三个参数表示是否异步执行,默认为true(异步)
xhr.timeout=1;//定时函数 异步,单位ms
xhr.withCredentials=false;//默认false,证书情况,如果为true,cookie跨域报错;
xhr.addEventListener('timeout',function(){
	console.log('timeout'+xhr.readyState)
})
```
* 封装ajax函数
```
function ajax(obj){
	var method=(obj.method||'get').toLowerCase();
	var url=obj.url;
	if(!url){
		console.error('必须传入请求路径');
		return;
	}
	var params=obj.data||{};
	var success=obj.success;
	//处理data成参数1=value1&参数2=value2的格式
	var str="";
	for(var key in params){
		str += key +'='+params[key]+'&';
	}
	//因为拼接后多个&,需要删除最后一个&
	str=str.slice(0,-1);
	//1 创建ajax对象
	var xhr;
	if(XMLHttpRequest){
		xhr=new XMLHttpRequest;
	}else{
		//兼容IE5,6
		xhr=ActiveObject('Microsoft.XMLHttp');
	}
	//2 请求
	if(method=='get'){
		xhr.open('get',url+'?'+str);
		xhr.send(null)
	}
	if(method=='post'){
		xhr.open('post',url);
		xhr.setRequestHeader("content-type","application/x-www-form-urlencoded");
		xhr.send(str);
	}
	//3 响应
	xhr.onreadystatechange=function(){
		if(xhr.status==200&&xhr.readyState==4){
			success(xhr.response)
		}
	}
}
ajax({
	method:'post',
	url:'./login.php',
	data:{
		username:'hu',
		password:'1234'
	},
	success:function(data){
		document.body.children[0].innerHTML=data;
	}
})
```

* get / post区别:
* get大小有限制约4k,post无限制;
* get传输效率更高;
* get安全性较差,get参数都拼接在地址栏中,参数长度受浏览器对url长度的限制;
* post参数都放在请求主体中,较安全;
* get可以不设请求头,post必须设请求头;
* get没有请求主体,xhr.send(null);

* XML 存放一种固定格式的数据的文件,类似html的标记语言;
	无服务器时,前端可以用xml假数据测试,	用`xhr.responseXML`可将xml字符串转为xml格式的数据;
```//data.xml
<?xml version="1.0" encoding="utf-8" ?>
<info>

</info>
```

* json	轻量级文本数据交换格式		json解析
* json作假数据,用`xhr.responseText`获取响应数据(字符串型),`JSON.parse(xhr.responseText)`转为json格式;
* php中,解析json,用`json_encode()`		`json_decode()`;
--------------------------------------------------
28.跨域	
* 同源:同域名、同协议、同端口;
* 跨域:不同源即跨域;
* 同源策略:解决跨域的方法	CORS;
```
* xhr对象不允许跨域访问;
	后台允许跨域 header('Access-Control-Allow-Origin:*');//不安全
* cookie只能同源访问;
	xhr.withCredentials=false;//默认false,cookie跨域不报错也不阻拦;设为true,cookie跨域就报错;
```
* 数据接口:请求路径;xhr只能同源请求数据接口;
* postman 测试接口的工具;可测get、post请求方式;

* jsonp		(json with padding)	(json的一种使用模式 解决跨域)
	原理:利用<script src="./json.php?callback=fn"></script>可跨域的特性,由服务端返回一个设好的js函数的调用,将服务器数据以该函数参数的形式传递过来;
	只能用于get请求;需前后端配合;
```
* 封装ajax函数(带jsonp的)
function ajax(option){
	//获取默认值
	var method=(option.method||'get').toLowerCase();
	var url=option.url;
	if(!url){
		console.error('必须输入请求路径');
		return;
	}
	var data=option.data||{};
	var params="";//处理请求参数/请求主体
	for(var key in data){
		params += key +'='+data[key]+'&';
	}
	params=params.slice(0,-1);
	var success=option.success;//获取响应成功的回调函数
	var error=option.error;//获取响应出错的回调函数
	var dataType=(option.dataType||'json').toLowerCase();//是否使用xhr对象请求数据/用script标签请求jsonp数据
	var jsonp=option.jsonp||"callback";//如果使用script标签请求数据,传给后台回调函数名的键,默认是callback
	var cbName=option.cbName||('hu'+new Date().getTime()+Math.random().toString().slice(2));//如果使用script标签请求数据,传给后台的回调函数名,默认是随机
	//使用xhr对象(json)请求数据
	if(dataType=='json'){
		var xhr=new XMLHttpRequest;//创建xhr对象
		if(method=='get'){//请求
			xhr.open('get',url+'?'+params);
			xhr.send(null);
		}
		if(method=='post'){//请求
			xhr.open('post',url);
			xhr.setRequestHeader('content-type','application/x-www-form-urlencoded');
			xhr.send(params);
		}
		xhr.onreadystatechange=function(){//响应
			if(xhr.readyState==4){
				if(xhr.status==200){
					success(xhr.response);
				}else{
					if(error){
						error();
					}
				}
			}
		}
	}
	//使用script标签请求(jsonp)数据
	var script=document.createElement('script');//创建script标签
	script.src=url+'?'+params+'&'+jsonp+'='+cbName;//设置该标签的src属性
	//定义一个全局函数,以备调用
	window[cbName]=function(data){
		success(data);
		script.remove();
	}
	document.body.appendChild(script);
}

* ajax函数调用实例(百度关键字接口)
ajax({
	dataType:'jsonp',
	url:'https://www.baidu.com/sugrec',
	data:{
		pre:1,
		p:3,
		ie:'utf-8',
		json:1,
		prod:'pc',
		from:'pc_web',
		sugsid:[1445,21092,18560,29518,28519,29099,29568,28833,29220,26350,29589],
		wd:keyword,
		req:2,
		pbs:'%E7%99%BE%E5%BA%A6%E7%BF%BB%E8%AF%91',
		csor:5,
		pwd:'baid',
		_:1563970627537
	},
	success:function(data){
		//console.log(data);
		var result=data.g;
		var str="";
		for(var i=0;i<result.length;i++){
			str += "<li>"+result[i].q+"</li>";
		}
		ul.innerHTML=str;
	}
})

```
* promise函数	(异步编程)
	一个对象,存放将来完成的事情;
	三种状态:pending(进行中)、fulfilled(成功)、reject(失败);
	promise状态不受外界影响,一旦状态改变就不会再变,任何时候都可得到这个结果;
```
var promise=new Promise(function(resolve,reject){
	setTimeout(function(){
		var a=Math.random();
		if(a>0.5){
			resolve(a)
		}else{
			reject(a)
		}
	},2000)
}).then(function(a){
	console.log('resolve'+a)
},function(a){
	console.log('reject'+a)
})

* promise.then(function(){
},function(){})
	不做说明默认返回resolve函数

//捕捉错误
promise.catch(function(e){
	console.log(e)
})

try{
	//要检测是否有错误的代码
}
catch(e){//捕捉错误
	console.log(e)
}
```
* ajax与promise封装在一起
```
function ajax(option){
	return new Promise(function(resolve,reject){
		...
				if(xhr.status==200){
					resolve(xhr.response)
				}else{
					reject()
				}
		...
		window[cbName]=function(data){
			resolve(data);
			script.remove()
		}
		...
	})
}
* 调用实例
ajax({
	url:'./login.php'
}).then((data)=>{
	console.log(data);
	return ajax({
		url:'./test.php'
	})
}).then((data)=>{
	console.log(data)
})

```
--------------------------------------------------
29.面向对象:闭包 原型链

29.1 闭包:函数外部可以访问函数作用域中变量的函数;
* 作用:一般函数执行完后变量会被回收处理掉,闭包会在函数执行完后将变量存在内存中;
	缺点:函数变量长期存在内存中,容易导致内存泄露		节约全局变量;
	原理:函数内定义一个变量a,返回一个可以操作该变量的函数,通过该返回值就可以操作函数内部变量a,这就是闭包;
```//闭包举例
function fn(){
	var a=1;
	return function aa(){
		a+=1;
		console.log(a);
	}
}
var result=fn();//即为函数aa
result();//调用返回值(函数aa)

* 事件函数改闭包
document.body.onclick=(function(){
	return function(){
		document.body.background='blue'
	}
})()
```
* 构造函数 
```//函数名首字母大写
function Human(name,age){
	this.name=name;
	this.age=age;
}
console.dir(Human);//详细打印
//实例化对象	每个实例化对象地址不同
	var h1=new Human('hu',22);
	var h2=new Human('hu',22);
```
* this指向
```
* 普通函数中this->window,严格模式中this->undefined;
* 定时函数中this->window;
* 构造函数中this->实例化对象;
* 函数为对象中的方法,this->方法的调用者,h1.getColor(this.color);//this->h1
* 事件函数中this->事件源;
* 箭头函数不改变this的指向;
```
* 改变this的指向:call apply bind
```
function Fn(name,age){
	this.name=name;
	this.age=age;
}
var obj={
	a:1,
	b:2
}
Fn.call(obj,'hu',22);//改变Fn中的this指向->obj,只改变本次,同时执行函数
Fn.apply(obj,['hu',22]);//改变Fn中的this指向->obj,只改变本次,同时执行函数
var fn=Fn.bind(obj);//改变Fn中的this指向->obj,只改变本次,不执行函数
fn('hh',22);

* apply与call区别:apply后面参数以数组的形式
Math.max.apply(null,arr);//求数组最大值
Math.max(...arr);
```
29.2 原型 prototype	对象自带的属性
* 构造函数的原型上有一个constructor属性,指向构造函数本身;
* 实例化对象的__proto__指向其构造函数的原型;
* 实例化对象的__proto__上的属性和方法都能被实例对象使用;
* 系统定义的构造函数:Array Function Set Object RegExp Date Promise;
* 精确判断数据类型:
	Object.prototype.toString.call(arr);//[object array];
* 原型prototype开发者编程使用,__proto__浏览器内部使用;
```
function Human(name,age){
	this.name=name;
	this.age=age;
}
Human.prototype.getName=function(){
	console.log(this.name)
}
var h1=new Human('hu',22);
h1.getName();

* Human.prototype.constructor=Human;
* h1.__proto__=Human.prototype;
* Human.prototype.__proto__=Object.prototype;
* 原型链		-->指的是__proto__
	h1-->Human.prototype-->Object.prototype-->null;
	
function Student(grand,score,name,age){
	Human.call(this,name,age);//构造函数继承
	this.grand=grand;
	this.score=score;
}
Student.prototype=h1;//改变Student的原型
Student.prototype.getScore=function(){
	console.log(this.score)
}
var s1=new Student('1916',100,'hh',20);
* 通过原型链继承
	s1-->h1-->Human.prototype-->Object.prototype-->null;
* 通过构造函数继承
* 组合继承(原型链+构造函数)
```
* 面向对象方法
```
* 属性判断
	in 可判断本身属性及原型链上的属性
	hasOwnProperty 只能判断本身属性
	console.log('name' in s1);//true
	console.log(s1.hasOwnProperty('age'));//false
	
* 实例判断	instanceof 只要在原型链上都能判断为true
	console.log(s1 instanceof Student);//true
	console.log(s1 instanceof Function);//false
	console.log(Human instanceof Object);//true
	console.log(Human instanceof Function);//true
	console.log(arr instanceof Function);//false

* 定义对象的属性	Object.defineProperty
var obj={a:1,b:2}
Object.defineProperty(obj,'c',{
	value:3,
	writable:true,
	enumberable:true //for...in循环是否能枚举obj的key
	//configurable:true		总开关,一旦为false 就不能设置value writable...
})
//get set不能与value writable...同时用
Object.defineProperty(obj,'c',{
	get:function(){
		console.log('观察者模式 获取值')
	},
	set:function(){
		console.log('观察者模式 设置值')
	}
})
obj.c=5;

* 合并对象  Object.assign 作用同{...obj1,...obj2}
var obj1={a:1,b:[2]}
var obj2={b:[3],c:4}
console.log({...obj1,...obj2});//b:[3]
var obj=Object.assign(obj1,obj2);
console.log(obj);//b:[3]

* arguments.callee-->函数本身
```
* es6类class继承
```
class Human{
	constructor(name,age){
		this.name=name;
		this.age=age
	}
	getName(){
		console.log(this.name)
	}
}
class Student extends Human{
	constructor(grand,score,name,age){
		super(name,age);
		this.grand=grand;
		this.score=score;
	}
	getScore(){
		console.log(this.score)
	}
}
var s1=new Student('1920',100,'h',22);
console.dir(s1);
```
* 脚本设置状态栏(ie浏览器可,新版浏览器禁用) window.status='hello world';
* 面向对象编程
```
class Drag{
	constructor(id){
		//
	}
	init(){
		//
	}
}
var one=new Drag('one');
one.init();
```
--------------------------------------------------
30.jQuery		(一个js库)
* [jQuery](https://jquery.cuishifeng.cn/index.html)
* 引jquery包;写入口函数;
* $==jQuery;
```
* CDN引入
<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
* 使用前要写入口函数,jquery入口函数可以写多个
$(function(){
	//js代码		ajax
	$.ajax({
		url:'',
		data:'',
		dataType:'jsonp',
		jsonp:'callback',
		success:function(data){
			console.log(data)
		}
	})
})
$(document).ready(function(){
	//
})
```
--------------------------------------------------
#### 前端快速开发工具

31.Bootstrap	用于响应式布局、移动设备优先
* [bootstrap](https://v3.bootcss.com/);
* 既能适应pc端,又能适应移动端;
* Bootstrap的所有JavaScript插件都依赖`jQuery`, jQuery必须在Bootstrap之前引入;
```//CDN引入
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js"></script>
```
--------------------------------------------------
32.Echart		使用js实现的开源可视化库 图表
* [echart](https://echarts.apache.org/zh/index.html)
```
* 引入		(下载)
<script src="echarts.min.js"></script>
```
--------------------------------------------------
33.swiper		开源的触摸滑动插件库(轮播图)
* [swiper](https://www.swiper.com.cn/)
* 需要用到的文件有`swiper-bundle.min.js`和`swiper-bundle.min.css`文件
```
<link rel="stylesheet" href="dist/css/swiper-bundle.min.css">
<script src="dist/js/swiper-bundle.min.js"></script>
var swiper=new Swiper('.swiper-container',{
	
})
```
--------------------------------------------------
34.模板引擎 artTemplate
* html和js语法混写;
* 引包;书写模板:模板必须有一个id,type="text/html";
```
* 原始语法	凡是js代码都包裹在<%%>里面,如果是取变量值,加=号;
<% if (user) { %>
  <h2><%= user.name %></h2>
<% } %>

* 标准语法
{{if user}}
  <h2>{{user.name}}</h2>
{{/if}}
```
--------------------------------------------------
35.gulp		自动化构建工具
* 搭建web服务器;	压缩代码;	项目上线前压缩代码
```
* 安装		npm i gulp 

* 根目录下创建gulpfile.js文件,为配置运行文件

* 运行本地文件		npx gulp 任务名	(gulp本地安装)

* gulp.task	定义任务(第一个参数任务名,第二个参数执行函数)
* gulp.src	读取文件的数据流
* gulp.dest	给文件写入数据流(参数 写入文件的路径)
* gulp.watch('要监听的文件',文件发生变化的回调函数)

* gulp.series(任务1,任务2,...) 串行
* gulp.parallel(任务1,任务2,...) 并行

var gulp=require('gulp');
gulp.task('js',function(done){
	gulp.src('./src/js/*.js')
	.pipe(load.uglify())					//压缩js
	.pipe(load.rename('index.min.js'))
	.pipe(gulp.dest('./dist/js/'));
	done();
})

gulp.task('server',gulp.series(gulp.parallel('html','css','js')),function(done){
	brower.init({
		server:'./dist',
		port:8080
	})
	//gulp.task('save',function(done){}) 服务器重启
	gulp.watch('./src/',gulp.series('save'));
	done();
})
```
* gulp常用插件
```
* gulp-load-plugins 自动加载插件
	var load=require('gulp-load-plugins')();//引入后不需要引入其他插件包	load.concat() load.uglify()
	
* gulp-uglify 压缩js文件
* gulp-minify-css 压缩css文件
* gulp-minify-html 压缩html文件
* gulp-imagemin 压缩图片
* gulp-concat 合并文件
* gulp-babel es6转es5语法
* gulp-rename 重命名
* browser-sync 开启静态服务器
	var browser=require('browser-sync').create();
```
--------------------------------------------------
36.sass		css的预编译 兼容css3格式(另一种形式的css,不能直接在浏览器中运行)
* 使用 
* 1.先搭建环境 gulpfile.js文件;
* 2.编译环境搭建,gulp.task('sass',function(done){	...	done()});
* 3.开启自动刷新服务器;
* .scss文件 		css3语法扩充版
* .sass文件		不使用花括号,不用分号,使用换行分割
* 定义变量 定义函数 if判断 for循环 嵌套 @mixin @include;
```//index.scss
@import url('./a.css');
@import 'a';//a.scss
ul{
	background:green;//静默注释
	color:red;/*css注释*/
	li{
		div{
			background:green;
			h1{
				h1.one{color:red}
				h2.two{color:blue}
				a{
					color:black;
					&:hover{color:red;}
				}
			}
		}
	}
}

//变量定义
$nav-color:#000;
$width:200px;
nav{
	color:$nav-color;
	width:$width;
}

//sass循环语句		@for

//sass判断语句 	@if 条件成立输出{}中的代码

//mixin函数
@mixin rounded-corner{
	-moz-border-radius:5px;
	-webkit-border-radius:5px;
	border-radius:5px;
}
.main{
	background:green;
	border:2px solid #eee;
	@include rounded-corner;
}
```
--------------------------------------------------
37.git	分布式版本管理工具
* svn 集中式版本管理工具 repository(源代码库) checkout 提取;commit 提交;update 更新;
* git与svn区别:git把更多的内容放在了本地仓库;

* 先安装gitbash工具;安装完成后配置个人信息;
* 初始化一个仓库: git init		-->产生一个隐形文件夹.git
* workplace ; index/stage 暂存区;repository 本地仓库;remote 远程仓库;
```
git add 文件路径;//添加一个文件到暂存区
git add .		:添加所有文件到暂存区

git commit -m "本次提交的简介"	:提交文件

git reset --hard 提交的版本号		:退回指定版本

git branch 分支名	:创建分支;
git checkout master 	:切换到主分支;

.gitignore文件 	写想被git忽略的文件,如node_modules
```
* github 代码仓库	用户名Sparkhugh

* xss	跨站脚本攻击	解决办法:用正则过滤和转义;
--------------------------------------------------
38.nodejs		基于chrome V8引擎的js运行时构建的平台 web服务器软件
* [nodejs](http://nodejs.cn/api/)
* 下载并安装		检查是否安装成功:shift+右键--此处打开命令行窗口-- node -v -->显示版本号则安装成功;
* npm	随nodejs一起安装的包管理工具;
* 浏览器中有chrome v8引擎、js引擎、渲染引擎,nodejs里只有v8引擎;
```
* 检查版本 
npm -v;

* 安装模块	
npm install 模块名@版本号/npm i 模块名@版本号;

* 全局安装 可当命令行使用(安装目录在c盘)
npm i nodemon -g;

* package.json	管理和记录下载的模块
npm init:创建package.json文件;
npm i :根据package.json中依赖包目录下载模块;

* 卸载模块
npm uninstall 模块名;

```
* nodejs模块导入导出
```
* 运行js文件
	打开命令行-- node 路径/文件名 (可省略.js后缀)
	
* 导出模块
	module.exports.fn=function(){
		
	}
* 导入模块
	var mod=require('./index.js')
	
* 常用全局变量
	__dirname:当前文件所在目录的绝对路径;
	__filename:当前文件的绝对路径;
	console,module,exports,require;

* url模块		解析url地址
	var url=require('url');
	url.parse(string);//解析路径,结果中的pathname是路由,query是url参数;

* querystring模块		把参数格式跟json格式转换
	var querystring=require('querystring');
	querystring.parse('a=1&b=2')--->json格式
	querystring.stringify(json)--->编码格式
	
* path模块		解析路径
	var path=require('path');

* fs模块			读写文件
	var fs=require('fs');

* http模块		
	var http=require('http');
	http.createSever();开启web服务器
	
* listen()	设置监听端口号;
	端口号尽量写8000以上;
```
* nodemon 当js文件代码改变时,自动重启node环境
```
* 安装 npm i nodemon -g
```
* 淘宝镜像
	[淘宝镜像](https://developer.aliyun.com/mirror/NPM?from=tnpm)
```
* 全局安装 
	npm install cnpm -g --registry=https://registry.npm.taobao.org
* 使用淘宝镜像
	cnpm install gulp
```
* 模块化开发
	优点:避免变量污染、命名冲突;提高代码复用率;提高可维护性;方便依赖关系管理;
```
* es6module		打开phpstudy,用localhost/文件路径打开
	html文档: <script type="module" src="./index.js"></script>
	export default fn;
	import fn from './index.js';

* commonjs:代表nodejs		打开命令行 node 文件名 运行;
	module.exports={
		fn:fn
	}
	var fn=require('./index.js')

* AMD 异步模块定义	代表requirejs 模块加载器 提前执行
	导出 define			导入 require

* CMD 通用模块定义 延迟执行 defer

```
* nodejs配置环境变量
```
* 电脑右键-属性-高级属性-高级-环境变量;
C:\Users\Administrator.2013-20160723MS\AppData\Roaming\npm
```
--------------------------------------------------
39.nodejs项目

* mongodb	分布式文件存储数据库	数据格式:json

* robo3T	连接本地mongodb服务		mongodb的可视化工具

* express		基于nodejs平台的web开发框架
```
npm i express -S		安装
npm i express-generator -g	(脚手架工具)
express --view=ejs project	(创建一个ejs模板的express项目)

/bin/www	入口文件	规定端口
package.json 中设置项目启动命令	npm start
app.js	项目主页	路由router配置
ejs模板引擎	html和js混写		index.ejs网站首页
/public	静态资源服务器		/css/	默认访问静态资源 /public 中的/css/
```
* postman	接口测试工具
* 测接口命令	 
```
* get请求	用gitbash工具
curl http://localhost:8000

* post请求
curl -d '' -X POST http://localhost:8000
```
* 文章发布 渲染到页面上用`xheditor`插件
* <form>标签的enctype属性能上传文件
```
* application/x-www-form-urlencoded 用于提交普通数据
* multipart/form-data		用于上传文件
	指定<form enctype="multipart/form-data"></form>
* nodejs端要使用`multiparty`插件解析文件数据
* nodejs端使用`fs`管道流,客户端要上传的文件都放在静态资源里`/public`
```
* 登录拦截 session与cookie	app.js中配置session
* 网站加favicon图标,放到 /public 里去

* websocket 		html5新增的api 
	建立客户端到服务端的双向交互通信	实时通信
* socket.io 一个开源库,对websocket进行封装
```
var socket=io('http://localhost:8848)
```
* socket 长连接,未出现故障和人为操作,服务端和客户端连接上就不会断开;
* http是短连接,无状态,一次信息传输完成即断开;
--------------------------------------------------
40.跨域问题
* 跨域是由浏览器的同源策略造成的 不同源即跨域
* 同源策略:同协议 同域名 同接口,只对ajax对象有限制,对script标签无限制

* 解决跨域问题的方法(3种): jsonp  代理 cors后端允许跨域访问

* jsonp		通过浏览器请求数据
	前端通过script标签调用接口,后端配合用jsonp方式返回数据
	只能用于get请求,需要前后端配合
```//html
<script>
	function fetch(res){console.log(res)}
</script>
<script src="http://localhost:8080/user?callback=fetch"></script>
```
```//第二种写法
<script>
	function fetch(res){console.log(res)}
	
	var script=document.createElement('script');
	script.src='http://localhost:8080/user?callback=fetch';
	document.body.appendchild(script);
</script>
```

* 代理 	通过代理软件请求数据,不需要通过浏览器	前端或者后端代理即可
	使用`http-proxy-middleware`中间件实现代理		eg:vpn即是一种代理工具
	nodejs中使用`http-proxy-middleware`进行接口代理
	后端使用`nginx`进行接口代理
	前端可用`webpack`进行接口代理
	正向代理:知道访问的服务端;反向代理:不清楚要访问谁 数据源不公开;
```
const app=require('express')();
const proxy=require('http-proxy-middleware');
app.use('/user',proxy({
	target:'http://10.36.136.111:8080',
	changeOrigin:true
}))
```

* CORS	只能后端工程师修改请求头 允许跨域访问
```
const app=require('express')();
//设置跨域访问 (前端需清除缓存,才能再次测试跨域)
app.all('*',function(req,res,next){
	res.header("Access-Control-Allow-Origin","*");
	res.header("Access-Control-Allow-Headers", "X-Requested-With");
	res.header("Access-Control-Allow-Methods","PUT,POST,GET,DELETE,OPTIONS");
	res.header("X-Powered-By",' 3.2.1')
	res.header("Content-Type", "application/json;charset=utf-8");
	next();
})
```
--------------------------------------------------
41.Token 鉴权 识别用户是否安全的规范
* [JSON Web Tokens](https://jwt.io/)
* cookie可以在客户端被随意篡改,安全性较低, token安全性更高;
* token在服务端生成,用户登录时或调用指定接口时,会返回token给客户端
	客户端在收到token后,保存在前端(如localstorage中),之后再请求其他有访问权限的后端接口时需要把token带上传给后端验证;
```
* 三部分组成 由 HS256算法 用户data 和 验证签名 组成;
var token="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
```
* token传给后端 一般会把token放在headers中进行传递
```//jQuery.ajax例
$.ajax({
	type:'get',
	url:'http://192.168.0.222:8080/api',
	data:{},
	headers:{
		token:"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
	},
	success:function(data){
		console.log(data)
	}
})
```
--------------------------------------------------