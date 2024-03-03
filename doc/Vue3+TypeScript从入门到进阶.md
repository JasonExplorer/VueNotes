## 一、简介
### 1、认识Vue
官网： https://cn.vuejs.org/

Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。

全程是Vue.js或者Vuejs；

什么是渐进式框架呢？表示我们可以在项目中一点点来引入和使用Vue，而不一定需要全部使用Vue来开发整个项目；

![vue-start-01.png](img%2Fvue-start-01.png)


渐进式: (自底向上逐层的应用)

(1) 简单应用: 只需要一个轻量小巧的核心库

(2) 复杂应用: 可以引用各种vue插件

这里说的渐进式框架其实是与Spring类似的分层架构，Vue由5个模块组成：声明式渲染/组件系统（vue.js）、客户端路由（vue-router）、大规模状态管理（vuex/pinia）、构建工具（vue-loader/webpack/vue-cli/vite）、数据持久化（涉及到后端，没有具体方案）


目前Vue在前端处于什么地位？

目前前端最流行的是三大框架：Vue、React、Angular。
![web-framework.png](img%2Fweb-framework.png)


### 2、前端框架数据对比

谁是最好的前端框架？

当然，我不会去给出我的结论：

首先，这是一个敏感的话题，在很多地方都争论不休，就像很多人喜欢争论谁才是世界上最好的语言一样；

其次，争论这个话题是没有意义的，争论不休的话题；

但是，我们从现实的角度，分析一下，学习哪一门语言更容易找到工作？

找后端的工作：优先推荐Java、其次推荐Go、再次推荐Node（JavaScript），可能不推荐PHP、C#；

找前端的工作：优先推荐JavaScript（TypeScript）、其次Flutter、再次Android（Java、Kotlin）、iOS（OC、Swift）；

也有很多的其他方向：游戏开发、人工智能、算法工程师等等；

那么，就前端来说，学习了HTML、CSS、JavaScript，哪一个框架更容易找到工作？

如果去国外找工作，优先推荐React、其次是Vue和Angular，不推荐jQuery了；

如果在国内找工作，优先推荐、必须学习Vue，其次是React，其次是Angular，不推荐jQuery了；


### 3、Vue3带来的变化
学习vue2还是vue3？
![vue2-or-vue3.png](img%2Fvue2-or-vue3.png)

目前需要学习Vue3吗？

在2020年的9月19日，万众期待的Vue3终于发布了正式版，命名为**“One Piece”**。

- 它也带来了很多新的特性：更好的性能、更小的包体积、更好的TypeScript集成、更优秀的API设计。

- 在vue3刚刚发布时，很多人也是跃跃欲试，想要尝试vue3的各种新特性。

- 但是事实上在刚刚发布的时候我们使用vue3来写demo练习是没有问题的，真正在实际业务项目中使用vue3还需要一个相对的过程；

- 包括vue3的进一步稳定、包括社区更多vue3相关的插件、组件库的支持和完善。

那么现在是否是学习vue3的时间呢？

- 答案是肯定的

- 首先vue3在经过一系列的更新和维护后，已经是趋于稳定，并且在之前尤雨溪也宣布在今年（2021年）第二季度会将vue3作为Vue CLI的默认版本了。

- 目前社区也经过一定时间的沉淀，更加的完善了，包括AntDesignVue、Element-Plus都提供了对Vue3的支持，所以很多公司目前新的项目都已经在使用Vue3来进行开发了。

- 并且在面试的时候，几乎都会问到各种各样Vue3、Vite2工具相关的问题。

Vue3带来的变化（源码）

源码通过monorepo的形式来管理源代码：

- Mono：单个

- Repo：repository仓库

- 主要是将许多项目的代码存储在同一个repository中；

- 这样做的目的是多个包本身相互独立，可以有自己的功能逻辑、单元测试等，同时又在同一个仓库下方便管理；

- 而且模块划分的更加清晰，可维护性、可扩展性更强；

源码使用TypeScript来进行重写：

- 在Vue2.x的时候，Vue使用Flow来进行类型检测；

- 在Vue3.x的时候，Vue的源码全部使用TypeScript来进行重构，并且Vue本身对TypeScript支持也更好了；

Vue3带来的变化（性能）

- 使用Proxy进行数据劫持

- 在Vue2.x的时候，Vue2是使用Object.defineProperty来劫持数据的getter和setter方法的；

- 这种方式一致存在一个缺陷就是当给对象添加或者删除属性时，是无法劫持和监听的；

- 所以在Vue2.x的时候，不得不提供一些特殊的API，比如s e t 或 set或set或delete，事实上都是一些hack方法，也增加了开发者学习新的API的成本；

- 而在Vue3.x开始，Vue使用Proxy来实现数据的劫持，这个API的用法和相关的原理我也会在后续讲到；

删除了一些不必要的API：

- 移除了实例上的$on, $off 和 $once；

- 移除了一些特性：如filter、内联模板等；

包括编译方面的优化：

- 生成Block Tree、Slot编译优化、diff算法优化；

Vue3带来的变化（新的API）

由Options API 到 Composition API：

- 在Vue2.x的时候，我们会通过Options API来描述组件对象；

- Options API包括data、props、methods、computed、生命周期等等这些选项；

- 存在比较大的问题是多个逻辑可能是在不同的地方： 比如created中会使用某一个method来修改data的数据，代码的内聚性非常差；

- Composition API可以将 相关联的代码 放到同一处 进行处理，而不需要在多个Options之间寻找；

Hooks函数增加代码的复用性：

- 在Vue2.x的时候，我们通常通过mixins在多个组件之间共享逻辑；

- 但是有一个很大的缺陷就是 mixins也是由一大堆的Options组成的，并且多个mixins会存在命名冲突的问题；

- 在Vue3.x中，我们可以通过Hook函数，来将一部分独立的逻辑抽取出去，并且它们还可以做到是响应式的；

- 具体的好处，会在后续的课程中演练和讲解（包括原理）；




————————————————

版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。

原文链接：https://blog.csdn.net/wuyxinu/article/details/124638989