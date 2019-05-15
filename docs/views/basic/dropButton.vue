<template>
<div class="ex-content">
    <div class="ex-card">
    <mark>
        <textarea class="ex-mark-text">
> 1、什么是 HTML？

答、HTML 并不是真正的的程序语言，他是一种标记语言 ，用来结构化和含义化你想要放
在 web 网站上的那些内容。它由一系列的元素（elements）所组成，这些元素可以用来
封装你的内容中担任不同工作的各部分和各个角色。

> 2、什么是 CSS？

答、就像 HTML，CSS 也不是真正的编程语言。它是样式表语言，也就是说，它允许你有
选择性的为 HTML 文档的元素添加样式。

> 3、什么是 JavaScript？

答、JavaScript（缩写：JS）是一门成熟的动态编程语言，当应用于 HTML 文档时，可以
在网站上提供动态交互性。

> 4、其他了解知识！

答、JS 发明者（JS 之父、Brendan Eich 布兰登·艾奇）
前端权威论坛：MDN W3C
<br/>
前端权威书籍：JS 高级程序设计 JS 权威指南

        </textarea>
    </mark>
    </div>
</div>
</template>
<script>
import { Mark } from '../index'
import {
    rdButton,
    rdDropButton
} from 'radon-ui'

export default {
    components: {
        rdButton,
        rdDropButton,
        Mark
    }
}
</script>