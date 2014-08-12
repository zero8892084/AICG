亚信UED - 团队规范文档
========
##文档目录
 - [目录结构](#)
 - [命名规范](#)
 	* [Class类名](#)
 	* [JavaScript 变量命名](#)
 - [HTML](#)
 	* [基础设施](#)
 	* [书写格式](#)
 	* [语义优化](#)
 	* [注释方法](#)
 - [CSS](#)
 	* [基础设施](#)
 	* [书写格式](#)
 	* [注释方法](#)
 - [JavaScript](#)
 - [jQuery](#)


##目录结构
```
├── aimd
│   └── dist
│      ├── cg (code-guide) 编码规范
│      ├── fe (front-end) 前端技术
│      ├── be (back-end) 后端技术
│      ├── ui (user interface) 界面规范
│      ├── ue (user experience) 交互规范
│      └── tools (development tools) 开发工具
│
└── index.md
```
##命名规范
####Class 命名
- 保持 Class 命名为全小写，可以使用短划线（不要使用下划线和 camelCase驼峰式命名）
- 短划线应该作为相关类的自然间断。(例如，`.btn` 和 `.btn-danger`)。
- 避免过度使用简写。.btn 可以很好地描述 button，但是 .s 不能代表任何元素。
- Class 的命名应该尽量短，也要尽量明确。
- 使用有意义的名称；使用结构化或者作用目标相关，而不是抽象的名称。
- 命名时使用最近的父节点或者父 class 作为前缀
- 使用 .js-* classes 来表示行为(相对于样式)，但是不要在 CSS 中包含这些 classes。

		/* Bad example */
		.t { ... }
		.red { ... }
		.header { ... }

		/* Good example */
		.tweet { ... }
		.important { ... }
		.tweet-header { ... }

####JavaScript 变量命名
- 标准变量采用驼峰标识
- 使用的ID的地方一定全大写
- 使用的URL的地方一定全大写, 比如说 reportURL
- 涉及Android的，一律大写第一个字母
- 涉及iOS的，一律小写第一个，大写后两个字母
- 常量采用大写字母，下划线连接的方式
- 构造函数，大写第一个字母

		var thisIsMyName;

		var goodID;

		var AndroidVersion;

		var iOSVersion;

		var MAX_COUNT = 10;

		function Person(name) {
		    this.name = name
		}


##HTML
####基础设施
- 文档声明，文件应以“<!DOCTYPE ......>”首行顶格开始，推荐使用html5文档类型

		<!DOCTYPE html>
		<html>
		    <head>
		    </head>
		</html>

- 语言种类，默认声明文档使用中文

		<html lang="zh-cn">
		    <!-- ... -->
		</html>

- 页面编码，必须申明文档的charset编码，且与文件本身编码保持一致，推荐使用utf-8编码
		
		<head>
		    <meta http-equiv="content-type" content="text/html;charset=utf-8"/>
		</head>


-  IE兼容模式，默认使用最高浏览器的渲染模式，考虑向后兼容

		<meta http-equiv="X-UA-Compatible" content="IE=Edge">

-  样式和脚本，引入 CSS 和 JavaScript 时不需要指明 type

		<!DOCTYPE html>
		<html lang="zh-cn">
			<head>
			    <meta http-equiv="content-type" content="text/html;charset=utf-8">
			    <title>HTML规范</title>
			    <link rel="stylesheet" href="style.css"/>
			    <style></style>
			</head>
			<body>
			    <script src="script.js"></script>
			</body>
		</html>

####书写格式
- 代码保持简洁的树形结构，必须使用四个空格的TAB键来进行代码缩进
- HTML标签名、属性和值全部小写，属性不能为空且必须加双引号
- 不要使用`&nbsp`进行缩进
- 不要使用行内样式
- 不要在内联元素中嵌入块级元素
- 不要在自动闭合标签结尾处使用斜线
	- `<img src="photo.png" alt="头像">`
- 不要在`Boolean`属性值中声明取值的属性
	- `<input type="text" disabled>`
- HTML 属性应该按照特定的顺序出现以保证易读性
	- `id`
	- `class`
	- `name`
	- `data-*`
	- `src`,`for`,`type`,`href`
	- `title`, `alt`

			<a id="code_guide" class="code-guide" data-modal="toggle" href="#">Link</a>
			<input name="sex" class="form-control" type="text">
			<img src="photo.jpg" alt="头像">

####语义优化
- 根据网页中某种类型的内容，使用特定HTML语义化的标签编写页面结构
- 对a元素提供title属性，img提供alt属性，加强"资源型"内容的可访问性
- 当空标签使用背景图时，必须加上相对应的文字说明，并按需隐藏文字，加强"不可见"内容的可访问性
- 使用div代替table进行布局，但是表现具有明显表格的数据，table还是首选
- 实用高于完美，尽量的遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价

####注释方法
- 代码说明的注释方法，采用标签闭合的写法，与HTML标签保持格式统一
		
		<!-- 头部 -->
		<div class="header">
		    <!-- 导航 -->
		    <ul class="nav">
		        <li><a href="#">nav1</a></li>
		        <li><a href="#">nav2</a></li>
		    </ul>
		    <!-- /导航 -->
		</div>
		<!-- /头部 -->

- 代码本身的注释方法，单行代码的注释也保持在同行，两端空格；多行代码的注释起始和结尾都另起一行并左缩进对齐
		
		<!-- <h1 class="header"><a href="#">LOGO</a></h1> -->
		<!--
		<ul class="nav">
		    <li><a href="#">nav1</a></li>
		    <li><a href="#">nav2</a></li>
		</ul>
		-->

- 注释在IE6中的BUG
	- 如果两个浮动元素之间存在注释，那么可能导致布局错位或文字的BUG
	- 通常这种情况，把注释去掉是最好的解决方案


##CSS

####基础设施
- CSS文件顶格位置申明文档的编码charset，推荐使用UTF-8编码

		@charset "utf-8";

- 样式表中的中文字体使用unicode转码

		font-family: Tahoma, "\5fae\8f6f\96c5\9ed1", "\5B8B\4F53";

- 使用clearfix或overflow清除子元素的浮动，而不是空标签

		.clearfix:after{
		    visibility:hidden;
		    display:block;
		    font-size:0;
		    content:" ";
		    clear:both;
		    height:0;
		}
		.clearfix{
		    zoom:1;
		}

- 针对某个浏览器写的样式或某个浏览器BUG的样式，必须加上注释说明
		
		.clearfix{
		    zoom:1; /* for IE6 IE7 */
		}

- 不使用影响页面性能expression表达式与filter，实现必要的特殊效果时，允许使用

		/* expression */
		.class{width:expression(this.width>100?'100px':'auto');}

		/* filter */
		.class{filter:alpha(opacity=50);}

####书写格式
- 使用四个空格的TAB键来进行代码缩，保证代码在各种环境下显示一致
- 为了代码的易读性，在每个声明的左括号前增加一个空格。
- 声明块的右括号应该另起一行
- 选择器、属性和值都使用小写，并且为选择器中的属性取值添加引号`input[type="text"]`
- 使用组合选择器时，保持每个独立的选择器占用一行
- 使用逗号分隔的取值，都应该在逗号之后增加一个空格。比如说`box-shadow`
- 最后一个属性值也以分号结尾，避免后期对维护带来的麻烦
		
		.selector,
		.selector-secondary,
		.selector[type="text"] {
		    padding: 15px;
		    margin-bottom: 15px;
		    box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
		}

- 所有的十六进制值都应该使用小写字母，并且使用缩写方式 `color:#fff;`
- 当值为0时省略单位 `margin:0;`
- `z-index`一般以5为一个步长（如50,55,60），方便以后增加或修改

		.ui-box1 {
		    z-index: 50;
		}
		.ui-box2 {
		    z-index: 55;
		}

- 省略url引用中的引号，其他需要引号的地方使用双引号

		.ui-box {
		    background:url(bg.png);
		}
		.ui-box:after {
		    content:".";
		}

- 先写带有浏览器私有标志的，并且通过缩进使取值垂直对齐以便多行编辑。

		.ui-box {
		    -webkit-box-shadow:0 0 0 #000;
		       -moz-box-shadow:0 0 0 #000;
		            box-shadow:0 0 0 #000;
		}

- 不建议使用`!important`，不建议使用`@import`，
- 原则上不允许使用Hack，不兼容问题可以通过改变方法和思路来解决，对于浏览器自身的缺陷，可以允许使用适当的Hack
- 当使用属性简写时你必须设置所有取值，常见的属性滥用包括
	- `padding`,`margin`,`font`,`background`,`border`,`border-radius`

			/* Bad example */
			.element {
			    margin: 0 0 10px;
			    background: red;
			    background: url("image.jpg");
			    border-radius: 3px 3px 0 0;
			}

			/* Good example */
			.element {
			    margin-bottom: 10px;
			    background-color: red;
			    background-image: url("image.jpg");
			    border-top-left-radius: 3px;
			    border-top-right-radius: 3px;
			}

- 根据属性的重要性按顺序书写
	1. Positioning 位置
	2. Box model 盒模型
	3. Typographic 排版
	3. Visual 外观

			.declaration-order {
			    /* Positioning */
			    position: absolute;
			    top: 0;
			    right: 0;
			    bottom: 0;
			    left: 0;
			    z-index: 100;

			    /* Box-model */
			    display: block;
			    float: right;
			    width: 100px;
			    height: 100px;

			    /* Typography */
			    font: normal 13px "Helvetica Neue", sans-serif;
			    line-height: 1.5;
			    color: #333;
			    text-align: center;

			    /* Visual */
			    background-color: #f5f5f5;
			    border: 1px solid #e5e5e5;
			    border-radius: 3px;

			    /* Misc */
			    opacity: 1;
			}



##JavaScript
####
##jQuery

