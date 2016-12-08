---
title: Vue优点缺点、安装及基础应用
date: 2016-12-08 19:06:59
tags: [Vue]
---

# Vue

### 因为工作需要，近端时间也在V学习ue的道路上慢慢成长

#### 有很多人问，Vue到底有什么优缺点？虽然是一个老生常谈的问题！咳咳咳~~但是因为本人最近才开始学习，不发表观点，借鉴官方文档说明总结了一下

### Vue.js

从技术角度讲，Vue.js 专注于 MVVM 模型的层。它通过双向数据绑定把View层和Model层连接了起来。实际的 DOM 封装和输出格式都被抽象为了Directives 和 Filters。Vue.js和其他库相比是一个小而美的库，作者的主要目的是通过一个尽量简单的 API 产生可反映的数据绑定和可组合的视图组件，感觉作者的思路非常清晰。


优点:

1. 简单：官方文档很清晰，比 Angular 简单易学。
2. 快速：异步批处理方式更新 DOM。
3. 组合：用解耦的、可复用的组件组合你的应用程序。
4. 紧凑：~18kb min+gzip，且无依赖。
5. 强大：表达式 & 无需声明依赖的可推导属性 (computed properties)。
6. 对模块友好：可以通过 NPM、Bower 或 Duo 安装，不强迫你所有的代码都遵循 Angular 的各种规定，使用场景更加灵活。


缺点：

1. 新生儿：Vue.js是一个新的项目，2014年3月20日发布的0.10.0 Release Candidate版本，目前github上面最新的是0.11.4版本，没有angular那么成熟。

2. 影响度不是很大：google了一下，有关于Vue.js多样性或者说丰富性少于其他一些有名的库。

3. 不支持IE8：哈哈不过AngularJS 1.3也抛弃了对IE8的支持，但是 [<font style="color:orange">@司徒正美</font>](https://www.zhihu.com/people/si-tu-zheng-mei/answers) 老师的avalon是支持IE6+的，应该下了很多努力去优化。这一点对于那些需要支持IE8的项目就不好了，不过这也是web前端开发的一个趋势，像IE低版本就应该退出历史舞台了，通过改变我们的前端思维，而不是顺应那些使用老版本而不去升级的人。 [<font style="color:orange">@玉伯</font>](https://www.zhihu.com/people/lifesinger/answers)老师就说过一句话，我觉得说的非常好“这年头，支持 IE6、7 早就不再是特性，而是耻辱(<font style="color:red">仅代表个人观点</font>)。努力推动支付宝全面不支持 IE6、7，期待更多兄弟加盟”。


作为一名Vue.js的忠实用户，我想有必要写点文章来歌颂这一门美好的语言了，我给它的总体评价是“简单却不失优雅，小巧而不乏大匠”，下面将围绕这句话给大家介绍Vue.js，希望能够激发你对Vue.js的兴趣。并进一步理解如何通过Vue.js来构建一个中大型的前端项目，同时做好相应的部署与优化工作。


## 文章将以PPT图片附加文字介绍的形式展开，不会涉及知识点的具体代码，点到为止。有兴趣的同学可以查看相应的文档进行了解。

#### Vue.js简介
![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213437156-272738874.png)

从上图的介绍中我们不难发现Vue.js是一款轻量级的以数据驱动的前端JS框架，其和jQuery最大的不同点在于jQuery通过操作DOM来改变页面的显示，而Vue通过操作数据来实现页面的更新与展示。下面便是Vue数据驱动的概念模型：

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213507734-1188887290.png)

Vue.js主要负责的是上图绿色正方体ViewModel的部分，其在View层（即DOM层）与Model层（即JS逻辑层）之间通过ViewModel绑定了DOM Listeners与Data Bingings两个相当于监听器的东西。

当View层的视图发生改变时，Vue会通过DOM Listeners来监听并改变Model层的数据。相反，当Model层的数据发生改变时，其也会通过Data Bingings来监听并改变View层的展示。这样便实现了一个双向数据绑定的功能，也是Vue.js数据驱动的原理所在。

#### Vue实例

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213528828-1360451701.png)

在一个html文件中，我们直接可以通过script标签引入Vue.js，然后就可以在页面里写Vue.js代码了。上图中我们通过new Vue()构建了一个Vue的实例，在实例中，可以包含挂在元素（el），数据（data），模板（template），方法（methods）与生命周期钩子（created等）等选项。不同的实例选项拥有不同的功能，如：

（1）el表明我们的Vue需要操作哪一个元素下的区域，’#demo’表示操作id为demo的元素下区域。

（2）data表示Vue 实例的数据对象，data 的属性能够响应数据的变化。

（3）created表示实例生命周期中创建完成的那一步，当实例已经创建完成之后将调用其方法。

#### Vue常用指令

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213600312-1946762337.png)

在Vue项目的开发中，我们使用的最多的应该就属Vue的指令了。通过Vue提供的常用指令，我们可以淋漓尽致地发挥Vue数据驱动的强大功能。以下便是图中常用指令的简单介绍：

（1）v-text: 用于更新绑定元素中的内容，类似于jQuery的text()方法

（2）v-html: 用于更新绑定元素中的html内容，类似于jQuery的html()方法

（3）v-if: 用于根据表达式的值的真假条件渲染元素，如果上图P3为false则不会渲染P标签

（4）v-show: 用于根据表达式的值的真假条件显示隐藏元素，切换元素的 display CSS 属性

（5）v-for: 用于遍历数据渲染元素或模板，如图中P6为[1,2,3]则会渲染3个P标签，内容依次为1，2，3

（6）v-on: 用于在元素上绑定事件，图中在P标签上绑定了showP3的点击事件

关于更多的Vue指令可以查看Vue2.0文档，地址：[<font style="color:orange">https://vuefe.cn/api/#指令</font>](https://vuefe.cn/v2/api/#search-query-nav)

#### Vue.js技术栈

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213619062-1055258578.png)

以上我们讲到可以直接在一个html页面里通过引入Vue.js来直接写Vue代码，但是这样的方式并不常用。因为如果我们的项目比较大，项目中会存在很多页面，一旦每个页面都引入一个Vue.js或者声明一个Vue实例，这样非常不利于后期的维护和代码的公用，也会存在实例名冲突的情况，所以我们需要用到Vue提供的技术栈来构建强大的前端项目。

除了Vue.js我们还需要用到：

（1）vue-cli：Vue的脚手架工具，用于自动生成Vue项目的目录及文件。

（2）vue-router： Vue提供的前端路由工具，利用其我们实现页面的路由控制，局部刷新及按需加载，构建单页应用，实现前后端分离。

（3）vuex：Vue提供的状态管理工具，用于同一管理我们项目中各种数据的交互和重用，存储我们需要用到数据对象。

（4）ES6：Javascript的新版本，ECMAScript6的简称。利用ES6我们可以简化我们的JS代码，同时利用其提供的强大功能来快速实现JS逻辑。

（5）NPM：node.js的包管理工具，用于同一管理我们前端项目中需要用到的包、插件、工具、命令等，便于开发和维护。

（6）webpack：一款强大的文件打包工具，可以将我们的前端项目文件同一打包压缩至js中，并且可以通过vue-loader等加载器实现语法转化与加载。

（7）Babel：一款将ES6代码转化为浏览器兼容的ES5代码的插件

利用以上等技术，我们便可以开始构建我们的Vue项目了。

#### 构建大型应用

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213637046-595985999.png)

<i>在构建我们的中大型Vue项目中，我们主要介绍如何利用vue-cli来自动生成我们项目的前端目录及文件，了解Vue中一切皆组件的概念及父子组件的通信问题，讲解在Vue项目中我们如何使用第三方插件，最后利用webpack来打包及部署我们的项目。</i>

#### vue-cli构建   到了安装这一步了

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213653500-764845769.png)

在使用vue-cli之前我们需要安装node.js，利用其提供的npm命令来安装vue-cli。安装node.js只需去其官网下载软件并安装即可，地址为：https://nodejs.org/en/
安装完成之后我们打开电脑的cmd命令行工具依次输入上图中的命令：

（1）npm install -g vue-cli：全局安装vue-cli

（2）vue init webpack my-project: 利用vue-cli在目录地址生成一个基于webpack的名为’my-project‘的Vue项目文件及目录

（3）cd my-project：打开刚刚创建的文件夹

（4）npm intall：安装项目所依赖的包文件

（5）npm run dev：利用本地node服务器在浏览器中打开并浏览项目页面

这样我们的一个基于webpack的vue项目目录就构建好了。

#### 单文件组件
![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213714796-114630473.png)

在刚刚构建好的vue项目中，我们会发现一个App.vue和Hello.vue的文件，那么像这样的以.vue后缀结尾的文件便是我们Vue项目中常见的单文件组件。单文件组件包含了一个功能或模块的html、js及css。在.vue文件中，我们可以在template标签中写html，在script标签中写js，在style标签中写css。这样一个功能或模块就是一个.vue组件，对于组件公用和后期的维护也非常便捷。

#### 父子组件通信

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213739375-1485936651.png)

那么像这样在以单文件组件为核心的项目开发中，我们一定会想到一个问题，就是.vue父子组件之间是如何交换数据来实现通信的呢？在Vue2.0中提供了props来实现父组件向子组件传递数据，通过$emit来实现子组件向父组件传递数据。当然如果是较为复杂和普遍的数据交互，建议大家使用vuex来同一管理数据。详情请见：[<font style="color:orange">https://vuefe.cn/guide/components.html#使用Props传递数据</font>](https://vuefe.cn/v2/guide/components.html#search-query-sidebar)


#### 插件使用

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213755906-1375909854.png)

接下来我们介绍下在基于webpack的vue项目中我们是如何使用插件的，主要有两种情况：

（一）全局使用

（1）在index.html引入：这样的方式不推荐使用，因为存在先后加载顺序的问题，有些插件不支持这一方式。

（2）通过webpack配置文件引入：主要通过plugin配置项的webpack.ProvidePlugin()方法实现，不过只适合支持CommonJs规范并提供一个全局变量的插件，如jQuery中的$。

（3）通过import + Vue.use()引入：这种方式需要在全局.vue文件中import需要加载的插件，然后通过Vue.use(‘插件变量名’)来实现，不过此方法只支持遵循Vue.js插件编写规范的插件使用，如vue-resourece。

（二）单文件使用

（1）通过import直接引入：这种方式可以在需要调用插件的.vue文件中使用，不过需要注意和实例的创建顺序问题，或者也可以通过require引入。

（2）import + components注册：此方式为Vue组件的使用方式，可以在一个组件中注册并使用一个子组件。

#### 部署及优化

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213813953-1422773333.png)

当我们搞定整个Vue项目的前端编码阶段后，我们需要对我们的前端项目文件进行部署和优化工作，主要的几个方式如下：

（1）使用webpack的DefinePlugin指定生产环境：通过plugin中的DefinePlugin配置，我们可以声明’process.env’属性为’development’(开发环境)或者’production’(生产环境)，结合npm配置文件package.json中scripts的命令来切换环境模式十分方便。

（2）使用UglifyJs自动删除代码块内的警告语句：一般在生产环境的webpack配置文件中使用，通过new webpack.optimize.UglifyJsPlugin()来进行配置，删除警告语句可以缩减文件的体积。
（3）使用Webpack hash处理缓存：当我们需要对发布到线上的文件进行修改时，重新编译的文件名如果和之前版本的相同会引起浏览器无法识别而加载缓存文件的问题。这样我们需要自动的生成带hash值的文件名来阻止缓存。详见：[<font style="color:orange">https://segmentfault.com/a/1190000006178770#articleHeader7</font>](https://segmentfault.com/a/1190000006178770#articleHeader7)

（4）使用v-if减少不必要的组件加载：v-if指令其实很有用处，它可以让我们项目中暂时不需要的组件不进行渲染，等需要用到的时候在渲染，比如某个弹窗组件等。这样我们可以减少页面首次加载的时间和文件量。

除了以上几点的优化，还有很多优化选择，有兴趣的童鞋可以好好地了解下webpack的API文档，毕竟webpack的功能十分强大。

#### 数据驱动实例

![img](http://images2015.cnblogs.com/blog/775838/201610/775838-20161030213829593-894919977.png)

这是我之前利用Vue.js数据驱动的原理写的一个拼图游戏，希望能够供大家进一步了解Vue数据驱动的理念。

演示地址：[<font style="color:orange">拼图游戏</font>](https://luozhihao.github.io/vue-puzzle/index.html#!/)

代码地址：[<font style="color:orange">拼图代码</font>](https://github.com/luozhihao/vue-puzzle/blob/master/src/App.vue)

#### 总结

本文以PPT图片附加文字介绍的形式简单介绍了Vue.js的知识点及开发流程，并将前端自动化、组件化、工程化的理念贯穿其中，由浅入深地阐述了Vue.js“简单却不失优雅，小巧而不发大匠”的独特魅力。






