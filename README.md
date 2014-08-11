亚信UED - 团队规范文档
========
##文档目录
 - [目录结构](#)
 - [命名规范](#)
 - [HTML](#)
 - [CSS](#)
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

##HTML
####基础设施
- 文档声明，文件应以“<!DOCTYPE ......>”首行顶格开始，推荐使用html5文档类型
```
<!DOCTYPE html>
<html>
    <head>
    </head>
</html>
```
- 语言种类，默认声明文档使用中文
```
<html lang="zh-cn">
    <!-- ... -->
</html>
```
- 页面编码，必须申明文档的charset编码，且与文件本身编码保持一致，推荐使用utf-8编码
```
<head>
    <meta http-equiv="content-type" content="text/html;charset=utf-8"/>
</head>
```

-  IE兼容模式，默认使用最高浏览器的渲染模式，考虑向后兼容
```
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```
-  样式和脚本，引入 CSS 和 JavaScript 时不需要指明 type
```
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
```
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
```
<a id="code_guide" class="code-guide" data-modal="toggle" href="#">Link</a>
<input name="sex" class="form-control" type="text">
<img src="photo.jpg" alt="头像">
```

####语义优化
- 根据网页中某种类型的内容，使用特定HTML语义化的标签编写页面结构
- 对a元素提供title属性，img提供alt属性，加强"资源型"内容的可访问性
- 当空标签使用背景图时，必须加上相对应的文字说明，并按需隐藏文字，加强"不可见"内容的可访问性
- 使用div代替table进行布局，但是表现具有明显表格的数据，table还是首选
- 实用高于完美，尽量的遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价
##CSS
####基础设施
- CSS文件顶格位置申明文档的编码charset，推荐使用UTF-8编码
```
@charset "utf-8";
```
- 样式表中的中文字体使用unicode转码
```
font-family: Tahoma, "\5fae\8f6f\96c5\9ed1", "\5B8B\4F53";
```
- 使用clearfix或overflow清除子元素的浮动，而不是空标签
```
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
```
- 针对某个浏览器写的样式或某个浏览器BUG的样式，必须加上注释说明
```
.clearfix{
    zoom:1; /* for IE6 IE7 */
}
```
##JavaScript
##jQuery

