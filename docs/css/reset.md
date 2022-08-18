# CSS RESET（样式重写）

在 HTML 中，很多标签拥有默认样式，比如，p 标签带有上下边距，h1 标签的字体加粗等。这些默认样式在开发时往往不是我们想要的效果，而且在不同浏览器中，部分标签可能表现不同。所以，CSS reset 诞生了，它的做法是引入 reset.css，用 CSS 覆写所有标签的默认样式，让浏览器成为一张“白纸”，从而更好的统一效果。但这是一种暴力的解决方案，存在着很多弊端。

1. CSS reset 引入的是全局规则，网页中的标签可能匹配一条或者多条规则。极端的情况下，某个标签可能匹配了上十条规则，但样式没有丝毫改变，这会徒增浏览器的解析成本。

2. 当项目发展到一定规模后，很多样式都依赖于 CSS reset，这时再想从中去掉是十分困难的。

3. CSS reset 会破坏依赖于默认样式的第三方样式库。

所以，更好的做法是按需使用，或者局部设置。

考虑到复用性，局部设置 CSS reset 可以结合类选择器或者预处理器（less、scss 等）一起使用。

```HTML
<style lang="css">
	/* 重写 h1~h6 的样式 */
	/* 需要重置 h1~h6 样式时，可以添加这个类名 */
	.reset-heading {
		font-weight: normal;
	}
</style>

<body>
	<h1 class="reset-heading">Hello CSS reset</h1>
</body>
```

```HTML
<!-- 这里是 less，需要编译成 css 才能在 html 中使用 -->
<style lang="less">
	/* 重写 h1~h6 的样式 */
	/* 需要重置 h1~h6 样式时，可以使用这个 mixin（混入） */
	#reset-heading() {
		font-weight: normal;
	}

	.title {
		#reset-heading();
	}
</style>

<body>
	<h1 class="title">Hello CSS reset</h1>
</body>
```

## 表单

### 输入框（input）

```CSS
input {
	display: inline-block;
	box-sizing: border-box;
	width: 100%;
	height: 40px;
	border: 1px solid #dcdfe6;
	border-radius: 4px;
	outline: 0;
	margin: 0;
	padding: 6px 10px;
	font-size: 14px;
	line-height: 40px;
}

/* 输入时（输入框处于焦点时） */
input:focus {
	border-color: #f56c6c;
	outline: 0;
}
```

### 复选框（input type="checkbox"）

```CSS
input[type="checkbox"] {
	/* 隐藏复选框的默认样式 */
	-webkit-appearance: none;
	-ms-appearance: none;
	/* 重写复选框的样式 */
	position: relative;
	display: inline-block;
	box-sizing: border-box;
	width: 13px;
	height: 13px;
	border: 1px solid #767676;
	border-radius: 2.5px;
	margin: 0;
	outline: 0;
	padding: 0;
	background-color: #fff;
	overflow: hidden;
	font-size: 12px;
	text-align: center;
	line-height: 1;
	font-weight: normal;
	cursor: pointer;
	vertical-align: middle;
}

/* 未选中且鼠标悬停时 */
input[type="checkbox"]:hover {
	border-color: #4f4f4f;
}

/* 选中 */
input[type="checkbox"]:checked {
	border-color: #0075ff;
	background-color: #0075ff;
}

/* 选中且鼠标悬停时 */
input[type="checkbox"]:checked:hover {
	border-color: #005cc8;
	background-color: #005cc8;
}

/* 选中时为复选框添加一个伪元素（对勾√） */
input[type="checkbox"]:checked::before {
	content: "";
	position: absolute;
	top: -1px;
	left: 50%;
	width: 2px;
	height: 5px;
	border: 2px solid #fff;
	border-left-color: transparent;
	border-top-color: transparent;
	transform: translateX(-50%) rotate(45deg);
}
```

### 按钮（button / input type="submit"）

```CSS
button,
input[type="submit"] {
	display: inline-block;
	-webkit-appearance: none;
	-ms-appearance: none;
	box-sizing: border-box;
	background-color: #f56c6c;
	border: 1px solid #f56c6c;
	border-radius: 4px;
	cursor: pointer;
	outline: 0;
	margin: 0;
	padding: 6px 10px;
	font-size: 14px;
	color: #fff;
	font-weight: 500;
	line-height: 1;
	text-align: center;
	white-space: nowrap;
}

/* 鼠标悬停时 */
button:hover,
input[type="submit"]:hover {
	background: #f78989;
	border-color: #f78989;
}

/* 鼠标点击时 */
button:active,
input[type="submit"]:active {
	background: #dd6161;
	border-color: #dd6161;
}
```
