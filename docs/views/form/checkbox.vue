<template>
<div class="ex-content">
    <h2></h2>
    <div class="ex-card">
        <mark>
            <textarea class="ex-mark-text">
> 1. 谈谈你对MVVM开发模式的理解

- MVVM分为Model、View、ViewModel三者。
- Model 代表数据模型，数据和业务逻辑都在Model层中定义；

- View 代表UI视图，负责数据的展示；

- ViewModel 负责监听 Model 中数据的改变并且控制视图的更新，处理用户交互操作；

- Model 和 View 并无直接关联，而是通过 ViewModel 来进行联系的，Model 和 ViewModel 之间有着双向数据绑定的联系。因此当 Model 中的数据改变时会触发 View 层的刷新，View 中由于用户交互操作而改变的数据也会在 Model 中同步。

- 这种模式实现了 Model 和 View 的数据自动同步，因此开发者只需要专注对数据的维护操作即可，而不需要自己操作 dom。

> 2. Vue 有哪些指令？

- v-html
- v-show
- v-if
- v-for

> 3. v-if 和 v-show 有什么区别？

v-show 仅仅控制元素的显示方式，将 display 属性在 block 和 none 来回切换；而v-if会控制这个 DOM 节点的存在与否。当我们需要经常切换某个元素的显示/隐藏时，使用v-show会更加节省性能上的开销；当只需要一次显示或隐藏时，使用v-if更加合理。

> 4、vue生命周期？

- `beforeCreated()` 在实例创建之间执行，数据未加载状态
- `created()` 在实例创建、数据加载后，能初始化数据，`dom`渲染之前执行
- `beforeMount()` 虚拟`dom`已创建完成，在数据渲染前最后一次更改数据
- `mounted()` 页面、数据渲染完成，真实`dom`挂载完成
- `beforeUpadate()` 重新渲染之前触发
- `updated()` 数据已经更改完成，`dom` 也重新 `render` 完成,更改数据会陷入死循环
- `beforeDestory()` 和 `destoryed()` 前者是销毁前执行（实例仍然完全可用），后者则是销毁后执行

> 5、vue的优点是什么？

- 低耦合。视图（View）可以独立于Model变化和修改，一个ViewModel可以绑定到不同的"View"上，当View变化的时候Model可以不变，当Model变化的时候View也可以不变。

- 可重用性。你可以把一些视图逻辑放在一个ViewModel里面，让很多view重用这段视图逻辑。

- 独立开发。开发人员可以专注于业务逻辑和数据的开发（ViewModel），设计人员可以专注于页面设计。

- 可测试。界面素来是比较难于测试的，而现在测试可以针对ViewModel来写。



            </textarea>
        </mark>
    </div>
</div>
</template>
<script>
import { Mark } from '../index'
import {
    rdCheckbox
} from 'radon-ui'

export default {
    components: {
        rdCheckbox,
        Mark
    }
}
</script>