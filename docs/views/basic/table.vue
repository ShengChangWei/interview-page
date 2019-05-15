<template>
<div class="ex-content">
    <div class="ex-card">
    <mark>
        <textarea class="ex-mark-text">
> 1、CSS3 新特性有哪些？

1.颜色：新增 RGBA，HSLA 模式<br>
2.文字阴影（text-shadow）<br>
3.边框： 圆角（border-radius） 边框阴影： box-shadow<br>
4.盒子模型：box-sizing<br>
5.背景：background-size 设置背景图片的尺寸 background-origin 设置背景图片的
原点 background-clip 设置背景图片的裁切区域，以”，”分隔可以设置多背景，用于
自适应布局<br>
6.渐变：linear-gradient、radial-gradient<br>
7.过渡：transition，可实现动画<br>
8.自定义动画<br>
9.在 CSS3 中唯一引入的伪元素是 ：selection. 10. 媒体查询，多栏布局<br>
11.border-image
12.2D 转换：transform：translate(x，y) rotate(x，y) skew(x，y) scale(x，y)<br>
13.3D 转换

> 2、对 BFC 规范的理解有哪些？

* 定义：<br>

BFC(Block formatting context)直译为"块级格式化上下文"。它是一个独立的渲染区域，
只有 Block-level box 参与，它规定了内部的 Block-level Box 如何布局，并且与这个区域
外部毫不相干。<br>

* 布局规则：<br>

A. 内部的 Box 会在垂直方向，一个接一个地放置。<br>
B. Box 垂直方向的距离由 margin 决定。属于同一个 BFC 的两个相邻 Box 的 margin 会发
生重叠。<br>
C. 每个元素的 margin box 的左边， 与包含块 border box 的左边相接触(对于从左往右的
格式化，否则相反)。即使存在浮动也是如此。<br>
D. BFC 的区域不会与 float box 重叠。<br>
E. BFC 就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反
之也如此。<br>
F. 计算 BFC 的高度时，浮动元素也参与计算。<br>

* 哪些元素会生成 BFC：<br>

A. 根元素<br>
B. float 属性不为 none<br>
C. position 为 absolute 或 fixed<br>
D. display 为 inline-block， table-cell， table-caption， flex， inline-flex<br>
F. overflow 不为 visible

> 3、什么是 CSS reset 是什么？normalize.css 是什么？

- Reset 重置浏览器的 css 默认属性 ，浏览器的品种不同，样式不同，然后重置，让他们统
一。（暴力的，强制的）
- Normalize.css 是 css reset 的替代方案，保护有用的浏览器默认样式而不是完全去
掉它们（温和的，根据浏览器特性的）
- 一般化的样式：为大部分 HTML 元素提供
- 修复浏览器自身的 bug 并保证各浏览器的一致性
- 优化 CSS 可用性：用一些小技巧
- 解释代码：用注释和详细的文档来。

> 4、清除浮动有几种方式?

* 父级 div 定义 height <br>
原理：父级 div 手动定义 height，就解决了父级 div 无法自动获取到高度的问题。 简单、
代码少、容易掌握 ，但只适合高度固定的布局
- 结尾处加空 div 标签 clear：both<br>
原理：在浮动元素的后面添加一个空 div 兄弟元素，利用 css 提高的 clear：both 清除浮动，
让父级 div 能自动获取到高度 ，如果页面浮动布局多，就要增加很多空 div，让人感觉很
不好 
* 父级 div 定义 伪类：after 和 zoom <br>
原理：IE8 以上和非 IE 浏览器才支持：after，原理和方法 2 有点类似，zoom(IE 专有属性)
可解决 ie6，ie7 浮动问题 ，推荐使用，建议定义公共类，以减少 CSS 代码。<br>
清除浮动代码:
```css
.clearfix:after {
    content: "";
    display: block;
    visibility: hidden;
    height: 0;
    line-height: 0;
    clear: both;
}
.clearfix {zoom: 1}
```
- 父级 div 定义 overflow：hidden <br>
超出盒子部分会被隐藏，不推荐使用. 
- 双伪元素法：<br>

```css
    .clearfix:before,.clearfix:after {
        content: "";
        display: block;
        clear: both;
    }
    .clearfix {
        zoom: 1;
    }
```
>  5、要你出一套适应不同分辨率，不同终端的前端实现方案你有什么思路？

- 流式布局：
使用非固定像素来定义网页内容，也就是百分比布局，通过盒子的宽度设置成百分比来
根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。这样的布局方式，就
是移动 web 开发使用的常用布局方式。这样的布局可以适配移动端不同的分辨率设备。
- 响应式开发：
那么 Ethan Marcotte 在 2010 年 5 月份提出的一个概念，简而言之，就是一个网站能
够兼容多个终端。越来越多的设计师也采用了这种设计。
CSS3 中的 Media Query（媒介查询），通过查询 screen 的宽度来指定某个宽
度区间的网页布局。

<table>
    <tr>
        <td>超小屏幕（移动设备）</td>
        <td>768px 以下</td>
    </tr>
    <tr>
        <td>小屏设备</td>
        <td>768px-992px</td>
    </tr>
    <tr>
        <td>中等屏幕</td>
        <td>992px-1200px</td>
    </tr>
    <tr>
        <td>宽屏设备</td>
        <td>1200px 以上</td>
    </tr>
</table>
由于响应式开发显得繁琐些，一般使用第三方响应式框架来完成，比如 bootstrap 来
完成一部分工作，当然也可以自己写响应式。
> 6、移动 WEB 和响应式有什么分别？

| 开发方式        | 移动web开发+PC开发 | 响应式开发  |
| :------------- |:-------------|:--------------|
| 应用场景：      | 一般在已经有pc端的网站，开发移动站的时候，只需单独开发移动端      | 针对新建站的一些网站，现在要求适配移动端，所以就一套页面兼容各种终端，灵活      |
| 开发：      | 针对性强，开发效率高。       | 兼容各种终端，效率低      |
| 适配:    | 只适配移动设备，pad上体验相对较差       | 可以适配各种终端    |
| 效率:    | 代码简洁，加载块       | 代码相对复杂，加载慢    |

> 7、px em rem 取用选择依据？

- px 像素（Pixel）。绝对单位。像素 px 是相对于显示器屏幕分辨率而言的，是一
个虚拟长度单位，是计算机系统的数字化图像长度单位，如果 px 要换算成物理长度，需要
指定精度 DPI。
- em 是相对长度单位，相对于当前对象内文本的字体尺寸。如当前对行内文本的字
体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。它会继承父级元素的字体大小，因
此并不是一个固定的值。
- rem 是 CSS3 新增的一个相对单位（root em，根 em），使用 rem 为元素设定字
体大小时，仍然是相对大小，但相对的只是 HTML 根元素。
- 区别：IE 无法调整那些使用 px 作为单位的字体大小，而 em 和 rem 可以缩放，rem
相对的只是 HTML 根元素。这个单位可谓集相对大小和绝对大小的优点于一身，通过它既
可以做到只修改根元素就成比例地调整所有字体大小，又可以避免字体大小逐层复合的连锁
反应。目前，除了 IE8 及更早版本外，所有浏览器均已支持 rem。

>  8、水平垂直居中的方式有几种？

```html
<div class="parent">
    <div class="child">Demo</div>
</div>
```
- 1.absolute + transform：绝对定位加+转换<br>

```CSS
.parent {
    position: relative;
}
.child {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}
```
- 2.inline-block + text-align + table-cell + vertical-align（单元格方式）<br>

```css
.parent {
    display：table-cell;
    text-align：center;
    vertical-align：middle;
}
.child {
    display： inline-block;
}
```
- 3.flex + justify-content + align-items（弹性模型）

```css
.parent {
    display： flex;
    justify-content： center; /* 水平居中 */
    align-items：center; /*垂直居中*/
}
```
> 9、如何实现单行和多行出现省略号?

- 单行出现省略号.....

```css
p{
　//注意一定要设置宽度
  width:110px;
  //强制文字换行
 white-space:nowrap;
 //溢出隐藏
 overflow:hidden;
 //出现省略号
 text-overflow:ellipsis;
}
```
- 多行出现省略号......

```css
p{
  //类似于display:flex;
  display:-webkit-box;
  //垂直的，竖立的
  -webkit-box-orient:vertical;
  //设定文字显示几行
  -webkit-line-clamp:3;
  //溢出隐藏
  overflow:hidden;
}
```
> 10、解释圣杯布局、双飞翼布局实现三栏水平布局

- 要求：允许增加额外的DOM节点，但不能修改现有节点顺序。

```html
<div class="container"> 
　　<div class="main">main</div> 
　　<div class="left">left</div> 
　　<div class="right">right</div> 
</div>
```

- 方法一：圣杯布局

```css
.container {
    padding: 0 300px 0 200px;
}
.left, .main, .right {
    position: relative;
    min-height: 130px;
    float: left;
}
.left {
    left: -200px;
    margin-left: -100%;
    background: green;
    width: 200px;
}
.right {
    right: -300px;
    margin-left: -300px;
    background-color: red;
    width: 300px;
}
.main {
    background-color: blue;
    width: 100%;
}
```
- 方法二：双飞翼布局 <br>

他的HTML结构发生了变化：

```html
<div class="container"> 
　　<div class="main">
    　　<div class="content">main</div> 
    </div>
　　<div class="left">left</div> 
　　<div class="right">right</div> 
</div>
```

```css
.left, .main, .right {
    float: left;
    min-height: 130px;
    text-align: center;
}
.left {
    margin-left: -100%;
    background: green;
    width: 200px;
}

.right {
    margin-left: -300px;
    background-color: red;
    width: 300px;
}
.main {
    background-color: blue;
    width: 100%;
}
.content{
    margin: 0 300px 0 200px;
}
```


> 11、src 与 href 的区别

- src（source）指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在
请求 src 资源时会将其指向的资源下载并应用到文档中，如 js 脚本，img 图片和 iframe 等
元素。
- 当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行
完毕，类似于将所指向资源嵌入当前标签内。
- href（hypertext reference/超文本引用）指向网络资源所在位置，建立和当前元素（锚点）
或当前文档（链接）之间的链接，如果我们在文档中添加<link href="common.css" rel="stylesheet"/>那么浏览器会识别该文档为 css 文件，就会并行下载资源并且不会停止
对当前文档的处理。
        </textarea>
    </mark>
    </div>
</div>
</template>
<script>
import { Mark } from '../index'
export default {
    components: {
        Mark
    }
}
</script>