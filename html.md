# html(超文本标记语言)
1.html文档结构
```
<html>
	<head>
		<title>网页标题</title>
		<meta charsert="urf-8" /> <!--编码格式(中文编码)-->
	</head>
	<body>
		//网页内容
	</body>
</html>
```
2.html标签
```
<div></div>
<span></span>
<h1>一级标题</h1>
<p>段落标签</p>
<i></i> <em></em> //设置文本倾斜
<b></b> <strong></strong>  //文本加粗
<u></u>  //文本下划线
<br />  //文本换行
<hr />  //文本中间划线
```
--------------------------------------------------
```
<ul>  //无序列表
	<li></li>
</ul>
<ol start="开始点 2">  //有序列表
	<li></li>
</ol>
<dl>  //自定义列表
	<dt>名词</dt>
	<dd>解释</dd>
</dl>
```
--------------------------------------------------
```
<a href="路径" title="提示文本" target="">超链接</a>
target="_blank" //新窗口打开链接 target="_self" //当前窗口打开链接
```
```
<img src="路径" title="提示文本" alt="图片加载不出时的提示文本" />
```
--------------------------------------------------
```//表格
<table>
	<tr>
		<td></td>
		<td></td>
	</tr>
</table>
<th></th>  //列标题
<caption></caption>  //表格标题
```
--------------------------------------------------
```//表单
<form name="表单名" method="get/post" action="路径">
	<input type="text" name="表单名" value="" size="控制框长度" maxlength="" />
	<input type="password" value="密码" />
	<input type="submit" value="提交" />
	<input type="button" value="空按钮" />
	<input type="reset" value="重置" />
	<input type="radio" value="单选" name="必填 且相同" checked="checked" />
	<input type="checkbox" value="多选" name="" disabled="disabled" />
	<input type="hidden" name="隐藏" />
	<input type="file" /> //上传文件
</form>
<select>
	<option>下拉选项1</option>
</select>
<textarea name="" cols="" rows="">表单域多行文本</textarea>
```
--------------------------------------------------
3.css(层叠样式表)
```
div{width:400px;height:200px;}
```
```//内部样式表
<style type="text/css">
	div{width:100px;}
</style>
```
```//外部样式表 引入
<link rel="stylesheet" type="text/css" href="路径" />

<style type="text/css">
	@import url("路径");
</style>
```
```//内联样式表(优先级最高) /*权重 1000*/
<div style="width:200px;color:green;">
</div>
```
--------------------------------------------------
4.css元素选择器
```
* id选择器 <div id="app"></div> #app{width:100px;}  /*权重 0100*/
* class选择器 <div class="box"></div> .box{width:100px;}  /*权重 0010*/
* 伪类选择器   /*权重 0010*/
	a:link /*未访问状态*/ a:visited /*已访问*/
	a:hover /*鼠标滑过*/ a:active /*点击*/
	a{color:red;} a:hover{color:blue;}
* 群组选择器(多个选择符用相同样式)
	#app,.box,a{color:#000;}
* 包含选择器  /*权重 求和*/
  div ul li{float:left;}
* 通配符
	*{margin:0;padding:0;}
* 伪元素选择器
```
--------------------------------------------------
5.css属性
```//文本
font-size:16px;1em;1rem; //文字大小
font-family:"Times 宋体"; //文字类型
color:green; //文字颜色
font-weight:bold/100-900; //加粗
font-style:normal; //倾斜
text-transform:none/capitalize/lowercase/uppercase;
text-align:left/right/center/justify;
vertical-align:top/middle/bottom;
line-height:20px;
text-decoration:none/underline/overline/line-through/blink; //下划线、上划线、删除线
text-indent:2px; //首行缩进
letter-spacing:2px; 
opacity:0.5;  //透明度
cursor:pointer;  //鼠标指针
```
```//列表
list-style:none;
```
```//边框
border:1px solid #eee;
```
```//背景
background:#fff url() no-repeat center top;
```
```//浮动 不占位
float:left/right/none;
```
--------------------------------------------------
6.标准盒模型
* padding:元素内容和元素边框之间的距离; 不能为负；
* margin:元素边框外部的空白区域；可为负值；
```//容器溢出
{overflow:hidden;visible;scroll;auto;inherit(继承父元素);}
```
```//空白空间
{white-space:normal;pre;nowrap(不换行);pre-wrap;}
```
```//文本溢出
{text-overflow:clip;ellipsis(显示省略号);}
```
```//元素转换
display:block;inline-block;none;flex;
```
--------------------------------------------------
7.元素定位
```
position:absolute(不占位);relative;fixed(不占位);sticky(黏性定位，参照页面顶端);static;
层叠 z-index:99;
```
```//元素水平、垂直居中
div{width:200px;height:200px;background:#000;position:fixed;left:0;right:0;top:0;bottom:0;margin:auto;}
div{width:200px;height:200px;background:#000;position:fixed;left:50%;top:50%;margin:-100px 0 0 -100px;}
```
```//锚点链接
<div id="box"></div>
<a href="#box"></a>
```
--------------------------------------------------
8.精灵图
```//圆角设置
border-radius:5px;
```
```//圆形
div{width:100px;height:100px;border-radius:50%;}
```
```//椭圆
div{width:100px;height:50px;border-radius:50%;}
```
```//胶囊型
div{
	width:100px;height:50px;border-radius:25px;//高度减一半
}
```
```//三角形
div{
	width:0;height:0;border:5px solid #eee;border-color:red transparent transparent transparent;
}
```
--------------------------------------------------
9.解决高度塌陷
```// 万能浮动清除法
.clearfix:after{
	content:"";display:block;height:0;overflow:hidden;clear:both;visibility:hidden;
}
.clearfix{*zoom:1;}
```
```
visibility:hidden;  //变空白但占位
display:none;  //消失不占位
```
--------------------------------------------------
10.伪元素选择器
```
div::after{content:""}
div::before{content:""}
div::selection{color:red;background:blue;} //定义对象选中后高亮效果
```
--------------------------------------------------
11.五大浏览器内核及代表作
* trident : IE/遨游/360/腾讯
* gecko : firefox
* webkit : chrome/safari
* presto : opera(欧朋)  //速度最快的引擎
* blink : goole和opera合作开发
--------------------------------------------------
12.常用图片格式
* jpg ：不支持动画，适合颜色丰富的图像；
* gif ：支持透明、支持动画，用于颜色较少的图像；
* png : 支持透明、不支持动画，文件较大,颜色较少；
* webp :;
--------------------------------------------------
13.bfc(块级格式化上下文)
* 独立渲染的区域
* 布局规则：
  * 内部的box会在垂直方向按顺序放置；
	* box垂直方向的距离由margin决定，同一个bfc的两相邻box的margin会发生重叠；
	* bfc区域不与浮动的box重叠;
	* bfc在页面上是一个独立渲染区域，子元素不会影响外面；
	* 计算bfc高度时，浮动元素也计入；
* 生成bfc条件：
	* 根元素html;
	* float:left/right; //浮动就会产生bfc
	* position:absolute/fixed;  //不占位的定位
	* display:inline-block/flex/...;
	* overflow不为visible:auto/hidden/scroll;
--------------------------------------------------
14.html新增标签   //<iframe>不是h5新增标签
```
<section></section>
<header></header>
<footer></footer>
<nav></nav>
<main></main>  //不常用 ie不兼容
<article></article>
<aside></aside>
<figure></figure>
<dialog></dialog>
<canvas></canvas>  //画布
```
```//表单新增属性
<input type="text" placeholder="文本框未输入时显示的提示" />
<input type="email/time/date/url/color/number/range/search" />
```
```//视频
<video src="movie.ogg" controls="controls"></video>
controls:显示控件
autoplay:自动播放
loop:重复播放
muted:静音
```
```//音频
<audio src="music.wav"></audio>
```
--------------------------------------------------
15.css3选择器
* 渐进增强:以低版本浏览器为基础构建页面再对高级浏览器进行改进；
* 优雅降级:以高版本浏览器为基础构建页面再向下兼容低版本浏览器；
```
//属性选择器
input[type="text"]:指定属性名并指定该属性的属性值；

//结构性伪类选择器
div:first-child/last-child/nth-child(n)
div:nth-of-type(n)/first-of-type

//动态伪类选择器
input:focus 匹配元素获取焦点

//层级选择器
<div>
	<ul>
		<li class="one"></li>
		<li class="two"></li>
		<li class="three"></li>
	</ul>
	<p></p>
	<p></p>
</div>
div>p : 选中div下所有的p(子选择器)
ul+p : 选中跟ul相邻的p(即选紧跟的兄弟元素)
ul~p : 选中在ul后面同级的所有p

```
--------------------------------------------------
16.css3属性
```
//文本属性
text-shadow:2px(水平) 2px(垂直) 2px(模糊距离) red;  //文本阴影
box-shadow:2px 2px 2px 2px(大小) red inset(阴影向内);

//背景
background-clip:border-box/padding-box/content-box;  //背景从哪里裁切
background-origin:padding-box/border-box/content-box;  //背景原点
background-size:200px 100px;  //length:宽 高
background-size:cover; //图片等比例扩展到完全覆盖背景区域，超出被裁切
background-size:contain;  //图片宽高等比例扩展到刚好完全适应背景区域

//颜色
color:rgba(色调,饱和度,亮度,透明度)
```
--------------------------------------------------
17.弹性盒模型 页面适应不同大小的屏幕和设备时有恰当的布局方式
```
//设为flex后，子元素的float/clear/vertical-align失效
div{ 
	display:flex;  //父元素设为弹性盒
	flex-direction:row/row-reverse/column/column-reverse;  //设置主轴方向
	flex-wrap:nowrap/wrap/wrap-reverse;  //子元素换行
	flex-flow:;
	justify-content:flex-start/flex-end/center/space-between/space-around;  //内容沿主轴对齐
	align-items:flex-start/flex-end/center/baseline/stretch(默认); //内容在侧轴对齐方式
	align-content:flex-strat/flex-end/center/space-between/space-around;  //内容的行与行之间在侧轴的对齐方式
	align-self:flex-start/flex-end/center/baseline/auto;  //单个子元素在侧轴对齐方式
	
	order:0;  //排序，数值越小，排序越靠前,默认0
	flex-grow:1;  //子元素放大比例,默认0
	flex-shrink:0;  //子元素缩小比例,默认1
	flex-basis:auto;  //分配多余空间前子元素占据的主轴空间
	// flex:0 1 auto;
}
```
--------------------------------------------------
18.怪异盒模型
div{
	box-sizing:border-box; //宽=width+margin(左右) width包括padding+border
}
--------------------------------------------------
19.常见布局方式
* 固定布局: 单位px，只设计一套尺寸;
* 可切换的固定布局:单位px，设计多套尺寸;
* 弹性布局:单位百分比，自适应一定范围内所有设备;
* 混合布局：单位px、%；
* 响应布局:相同内容不同宽度设计;
* 响应式单位：
	em:参照父元素font-size;
	rem:参照html font-size;
	vw:参照视口宽度 1vw=视口宽度1%；
	vh:参照视口高度 1vh=视口高度1%;
--------------------------------------------------
20.像素比
* 物理像素 : 设备的分辨率固定;
* 逻辑像素 : css代码使用的像素；
* 像素比=物理像素/逻辑像素;
* 用rem做移动端单位
```//iphone 6/7/8像素比为2;
document.documentElement.style.fontSize=document.documentElement.clientWidth / 3.75 + 'px';
```
--------------------------------------------------
21.css3动画
```//2D
* 背景渐变 gradient
div{
	background:-webkit-linear-gradient(top,red,black,blue); //线性渐变
	background:-webkit-radial-gradient(50% 50%,red,black,blue);  //径向渐变
}
* 过渡 transition
div{
	transition:all 5s linear 1s;
}
* 转换 transform
	div{
		transform:translate(20px,30px); //translate(x,y) 偏移
		transform:rotate(30deg); //旋转 默认顺时针
		transform:scale(2,3);  //缩放
		transform:skew(20deg,50deg);  //扭曲
		transform-origin:0 0; //旋转原点
	}
```
```//3D
@keyframes 3d{ }
div{
	animation:3d 5s linear 1s infinite normal;  //3d动画
	transform:translate3d(x,y,z);  
}
* perspective 景深  //近大远小
```
--------------------------------------------------