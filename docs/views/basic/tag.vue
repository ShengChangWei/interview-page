<template>
<div class="ex-content">
    <div class="ex-card">
    <mark>
        <textarea class="ex-mark-text">
> 1、HTML5 为什么只需要写 <!DOCTYPE HTML>？

答、（1）HTML5 不基于 SGML，因此不需要对 DTD 进行引用，但是需要 DOCTYPE 来规
范浏览器的行为（让浏览器按照它们应该的方式来运行）；（2）HTML4.01 基于 SGML，
所以需要对 DTD 进行引用，才能让浏览器知道该文档所使用的文档类型。

> 2、html5 有哪些新特性、HTML5 新标签的浏览器兼容问题如何处理?

答、html5 新增了以下的几大类元素：
* 内容元素：article、footer、header、nav、section。
* 表单控件：calendar、date、time、email、url、search。
* 控件元素：webworker, websockt, Geolocation。
<br>
移出的元素有下列这些：
* 显现层元素：basefont，big，center，font, s，strike，tt，u。
* 性能较差元素：frame，frameset，noframes。
* HTML5 已形成了最终的标准，概括来讲，它主要是关于图像，位置，存储，多任务等功能
的增加。
* 新增的元素有绘画 canvas ，用于媒介回放的 video 和 audio 元素，本地离线存储
* localStorage 长期存储数据，浏览器关闭后数据不丢失，而 sessionStorage 的数据在浏
览器关闭后自动删除。
* 新的技术：canvas,svg,webworker, websocket, Geolocation 

> 3、简述一下你对 HTML 语义化的理解。

答：（1）HTML 语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析；<br>
（2）即使在没有样式 CSS 的情况下也能以一种文档格式显示，并且是容易阅读的；<br>
（3）搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重，有利于 SEO；<br>
（4）使阅读源代码的人更容易将网站分块，便于阅读、维护和理解。

> 4、介绍一下你对浏览器内核的理解？常见的浏览器内核有哪些？

答、要或者说核心的部分是“Rendering Engine”，可大概译为“渲染引擎”，不过我们
一般习惯将之称为“浏览器内核”。负责对网页语法的解释（如标准通用标记语言下的一个
应用 HTML、JavaScript）并渲染（显示）网页。 所以，通常所谓的浏览器内核也就是浏
览器所采用的渲染引擎，渲染引擎决定了浏览器如何显示网页的内容以及页面的格式信息。
不同的浏览器内核对网页编写语法的解释也有不同，因此同一网页在不同的内核的浏览器里
的渲染（显示）效果也可能不同，这也是网页编写者需要在不同内核的浏览器中测试网页显
示效果的原因。<br>
常见浏览器内核:<br>
- Trident 内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称 MSHTML]
- Gecko 内核：Netscape6 及以上版本，FF,MozillaSuite/SeaMonkey 等。
- Presto 内核：Opera7 及以上。 [Opera 内核原为：Presto，现为、Blink;]
- Webkit 内核：Safari,Chrome 等。 [ Chrome 的：Blink（WebKit 的分支）]
- EdgeHTML 内核：Microsoft Edge。 [此内核其实是从 MSHTML fork 而来，删掉了几
乎所有的 IE 私有特性]

> 5、对 WEB 标准以及 W3C 的理解与认识?

-  标签闭合、标签小写、不乱嵌套、提高搜索机器人搜索几率、使用外链 css 和 js 脚
本、结构行为表现的分离，
-  文件下载与页面速度更快、内容能被更多的用户所访问、内容能被更广泛的设备所
访问、更少的代码和组件，
- 容易维护、改版方便，不需要变动页面内容、提供打印版本而不需要复制内容、提
高网站易用性。

> 6、Iframe 的作用？

答、用法：<br>
Iframe 是用来在网页中插入第三方页面，早期的页面使用 iframe 主要是用于导航栏
这种很多页面都相同的部分，这样可以在切换页面的时候避免重复下载。
优点：便于修改，模块分离，像一些信息管理系统会用到。
但现在基本上不推荐使用。除非特殊需要，一般不推荐使用。<br>
缺点：<br>
（1） iframe 的创建比一般的 DOM 元素慢了 1-2 个数量级 <br>
（2） iframe 标签会阻塞页面的加载，如果页面的 onload 事件不能及时触发，<br>
会让用户觉得网页加载很慢，用户体验不好.在 Safari 和 Chrome 中可以通过 js 动态设置
iframe 的 src 属性来避免阻塞 <br>
（3） iframe 对于 SEO 不友好，替代方案一般就是动态语言的 Incude 机制和 ajax
动态填充内容等. 
        </textarea>
    </mark>
    </div>
</div>
</template>
<script>
import { Mark } from '../index'
import {
    rdTag
} from 'radon-ui'

export default {
    components: {
        rdTag,
        Mark
    }
}
</script>