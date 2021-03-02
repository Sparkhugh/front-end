1.let用法
* 声明变量，作用于块级作用域；var声明的变量是全局变量；
* 不存在变量提升，let声明的变量一定要在声明后使用，否则报错；var命令存在变量提升，即变量可在声明前使用，值为undefined；
* let和const不出现变量提升的原因是 防止在声明变量前就使用该变量；
* 暂时性死区，块级作用域内存在let命令，它所声明的变量就绑定这个区域，不受外部影响，即为封闭作用域，在let声明前使用这些变量就会报错，即let声明前这些变量不可用，称为暂时性死区；
* 暂时性死区本质：只要进入当前作用域，所使用变量就已经存在，但不可获取，只有等到声明变量出现，才可获取使用；
* let不允许在相同作用域内重复声明同一个变量，不能在函数内部重新声明参数；
--------------------------------------------------
2.块级作用域
* es5只有全局作用域和函数作用域，没有块级作用域，会导致：内层变量可能会覆盖外层变量；用来计数的循环变量泄露为全局变量；
* es5规定 函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明；
* es6中块级作用域内声明的函数类似let，对作用域外没有影响；
* 尽量避免在块级作用域中声明函数 :
```
{//避免此种声明；
	function fn(){
		return a;
	}
}
```
```
//若要声明函数，应使用函数表达式声明
{
	let a="aaa";
	let fn=function(){
		return a;
	}
}
//es6的块级作用域必须有大括号{}；
```
--------------------------------------------------
3.const用法
* const声明一个只读的常量，一旦声明，常量的值就不能改变；const一旦声明就必须立即赋值，不然会报错；
* const作用域与let相同，只在声明所在的块级作用域内有效；
* 不存在变量提升，存在暂时性死区，只能在声明的位置后使用；
* 不可重复声明变量；
* const声明变量的本质：不是变量的值不得改动，而是变量指向的内存地址所保存的数据不得改动；
* 简单数据类型，值就保存在变量指向的那个内存地址，等同于常量；复杂数据类型，const保证的是指向一个固定的地址，内部数据不能保证；
--------------------------------------------------
4.es6中声明变量的方法：
```
var function let const import class
```
--------------------------------------------------
5.变量的解构赋值
* 从数组和对象中提取值，对变量进行赋值，称为解构；
```
//数组的解构赋值：
let a=1;let b=2;let c=3;
//es6中
let [a,b,c]=[1,2,3];

//可从数组中提取值，按照对应位置，对变量赋值，这种写法属于“模式匹配”，只要等式两边模式相同，左边的变量就会赋予对应的值；
//如果解构不成功，变量的值为undefined;

//不完全解构：等号左边的模式只匹配一部分等号右边的数组；
let [x,y]=[1,2,3];
//x=1;y=2;
//数组的元素是按次序排列的，变量的取值由其位置决定；
```
```
//对象的解构赋值：
	对象属性没有次序，变量必须与属性同名才能取到正确的值；
let {bar,foo}={
	foo:'a',
	bar:'b'
}
//foo:'a';bar:'b';

let {abc}={
	foo:'a',
	bar:'b'
}
//abc:undefined;

let obj={
	a:'hello',
	b:'world'
}
let {
	a:aaa,
	b:bbb
}=obj;
//aaa:hello;bbb:world;

let {foo:baz}={
	foo:'aaa',
	bar:'bbb'
}
//baz:'aaa';foo:undefined;
//foo是匹配的模式，baz才是变量，真正被赋值的是变量baz；
```
--------------------------------------------------
6.class用法
* class可以看作一个语法糖，类的数据类型就是函数，类本身就指向构造函数；
--------------------------------------------------
7.export/import
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
--------------------------------------------------
8.promise对象
* 一个对象，保存着未来才会结束的事件（一般是异步操作）