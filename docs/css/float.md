# 浮动

浮动样式的出现，起先是为了实现文字环绕图片的效果，现在多用于布局。

当一个元素浮动时，它会被移出文档流，然后向右或向左平移，直到碰到父元素的边框，或者碰到另一个浮动元素。

元素脱离文档流会造成父元素的高度坍塌，即如果一个元素中只有浮动元素，那么它的高度会是 0。

浮动元素同时具备行内块元素的特点，即支持宽高，外边距不会重合。如果没有设置宽高，则由内容撑开元素。

## 清除浮动（解决父元素的坍塌问题）

方式一：将父元素设置成行内块元素。

```css
.clearfix {
	display: inline-block;
}
```

方式二：为父元素添加一个清除浮动后的 after 伪对象。

```css
.clearfix::after {
	content: "";
	display: block;
	clear: both;
	height: 0;
	font-size: 0;
	visibility: hidden;
}
/* 兼容 ie */
.clearfix {
	*zoom: 1;
}
```

或者

```css
.clearfix::before, .clearfix::after {
    content: "",
    display: table;
}

.clearfix::after {
    clear: both;
}

/* 兼容 ie */
.clearfix {
    *zoom: 1;
}
```
