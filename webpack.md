
# webpack

[toc]

<!-- [webpack](https://github.com/zhangwen0424/sass-test/blob/master/single/test.scss) -->

<!-- ## webpack问题 -->
### 什么是webpack
webpack是一个打包模块化javascript的工具，在webpack里一切文件皆模块，通过loader转换文件，通过plugin注入钩子，最后输出由多个模块组合成的文件，webpack专注构建模块化项目。
WebPack可以看做是模块打包机：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其打包为合适的格式以供浏览器使用。

### 分别介绍什么是loader?什么是plugin?
loader：模块转换器，用于将模块的原内容按照需要转成你想要的内容  
plugin：在webpack构建流程中的特定时机注入扩展逻辑，来改变构建结果，是用来自定义webpack打包过程的方式，一个插件是含有apply方法的一个对象，通过这个方法可以参与到整个webpack打包的各个流程(生命周期)。  

### 几个常见的loader
file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件  
url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去  
source-map-loader：加载额外的 Source Map 文件，以方便断点调试  
image-loader：加载并且压缩图片文件  
babel-loader：把 ES6 转换成 ES5  
css-loader：加载 CSS，支持模块化、压缩、文件导入等特性  
style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。  
eslint-loader：通过 ESLint 检查 JavaScript 代码  

### 几个常见的plugin
define-plugin：定义环境变量  
terser-webpack-plugin：通过TerserPlugin压缩ES6代码  
html-webpack-plugin 为html文件中引入的外部资源，可以生成创建html入口文件  
mini-css-extract-plugin：分离css文件  
clean-webpack-plugin：删除打包文件  
happypack：实现多线程加速编译  
commons-chunk-plugin：提取公共代码  
uglifyjs-webpack-plugin：通过UglifyES压缩ES6代码  

### Loader和Plugin的不同？
不同的作用  
Loader直译为"加载器"。Webpack将一切文件视为模块，但是webpack原生是只能解析js文件，如果想将其他文件也打包的话，就会用到loader。 所以Loader的作用是让webpack拥有了加载和解析非JavaScript文件的能力。  
Plugin直译为"插件"。Plugin可以扩展webpack的功能，让webpack具有更多的灵活性。 在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。  
不同的用法  
Loader在module.rules中配置，也就是说他作为模块的解析规则而存在。 类型为数组，每一项都是一个Object，里面描述了对于什么类型的文件（test），使用什么加载(loader)和使用的参数（options）  
Plugin在plugins中单独配置。 类型为数组，每一项是一个plugin的实例，参数都通过构造函数传入。  

### webpack有哪些优点
专注于处理模块化的项目，能做到开箱即用，一步到位
可通过plugin扩展，完整好用又不失灵活
使用场景不局限于web开发
社区庞大活跃，经常引入紧跟时代发展的新特性，能为大多数场景找到已有的开源扩展
良好的开发体验

### webpack的缺点
webpack的缺点是只能用于采用模块化开发的项目

### 分别介绍bundle，chunk，module是什么
bundle：是由webpack打包出来的文件，  
chunk：代码块，一个chunk由多个模块组合而成，用于代码的合并和分割。  
module：是开发中的单个模块，在webpack的世界，一切皆模块，一个模块对应一个文件，webpack会从配置的entry中递归开始找出所有依赖的模块。

### 什么是模块热更新？
模块热更新是webpack的一个功能，他可以使得代码修改过后不用刷新浏览器就可以更新，是高级版的自动刷新浏览器。
devServer中通过hot属性可以空时模块的热替换
1，通过配置文件
```
const webpack = require('webpack');
const path = require('path');
let env = process.env.NODE_ENV == "development" ? "development" : "production";
const config = {
  mode: env,
 devServer: {
     hot:true
 }
}
  plugins: [
     new webpack.HotModuleReplacementPlugin(), //热加载插件
  ],
module.exports = config;
```
2，通过命令行
```
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "NODE_ENV=development  webpack-dev-server --config  webpack.develop.config.js --hot",
  },
```
### 什么是Tree-shaking
Tree-shaking可以用来剔除javascript中不用的死代码，它依赖静态的es6模块化语法，例如通过哦import 和export 导入导出，Tree-shaking最先在rollup中出现，webpack在2.0中将其引入，css中使用Tree-shaking需要引入Purify-CSS  

### 通过webpack处理长缓存  
浏览器在用户访问页面的时候，为了加快加载速度，会对用户访问的静态资源进行存储，但是每一次代码升级或是更新，都需要浏览器去下载新的代码，最方便和简单的更新方式就是引入新的文件名称。在webpack中可以在output纵输出的文件指定chunkhash,并且分离经常更新的代码和框架代码。通过NameModulesPlugin或是HashedModuleIdsPlugin使再次打包文件名不变。  

### 如何提高webpack的构建速度
1.通过externals配置来提取常用库  
2.利用DllPlugin和DllReferencePlugin预编译资源模块 通过DllPlugin来对那些我们引用但是绝对不会修改的npm包来进行预编译，再通过DllReferencePlugin将预编译的模块加载进来。
3.使用Happypack 实现多线程加速编译  
要注意的第一点是，它对file-loader和url-loader支持不好，所以这两个loader就不需要换成happypack了，其他loader可以类似地换一下  
4.使用Tree-shaking和Scope Hoisting来剔除多余代码
5.使用fast-sass-loader代替sass-loader
6.babel-loader开启缓存

babel-loader在执行的时候，可能会产生一些运行期间重复的公共文件，造成代码体积大冗余，同时也会减慢编译效率
可以加上cacheDirectory参数或使用 transform-runtime 插件试试
// webpack.config.js
```
use: [{
    loader: 'babel-loader',
    options: {
        cacheDirectory: true
}]
// .bablerc
{
    "presets": [
        "env",
        "react"
    ],
    "plugins": ["transform-runtime"]
}
```
### 不需要打包编译的插件库换成全局"script"标签引入的方式
比如jQuery插件，react, react-dom等，代码量是很多的，打包起来可能会很耗时
可以直接用标签引入，然后在webpack配置里使用 expose-loader  或 externals 或 ProvidePlugin  提供给模块内部使用相应的变量
```
// @1
use: [{
    loader: 'expose-loader',
    options: '$'
    }, {
    loader: 'expose-loader',
    options: 'jQuery'
    }]
// @2
externals: {
        jquery: 'jQuery'
    },
// @3
        new webpack.ProvidePlugin({
            $: 'jquery',
            jQuery: 'jquery',
            'window.jQuery': 'jquery'
        }),
```

### 优化构建时的搜索路径
在webpack打包时，会有各种各样的路径要去查询搜索，我们可以加上一些配置，让它搜索地更快
比如说，方便改成绝对路径的模块路径就改一下，以纯模块名来引入的可以加上一些目录路径
还可以善于用下resolve alias别名 这个字段来配置
还有exclude等的配置，避免多余查找的文件，比如使用babel别忘了剔除不需要遍历的

### 与webpack类似的工具还有哪些？谈谈你为什么最终选择（或放弃）使用webpack？
同样是基于入口的打包工具还有以下几个主流的：  
webpack  
rollup  
parcel  
从应用场景上来看：  
webpack适用于大型复杂的前端站点构建  
rollup适用于基础库的打包，如vue、react  
parcel适用于简单的实验性项目，他可以满足低门槛的快速看到效果  
由于parcel在打包过程中给出的调试信息十分有限，所以一旦打包出错难以调试，所以不建议复杂的项目使用parcel  

### webpack的构建流程是什么?从读取配置到输出文件这个过程尽量说全
Webpack 的运行流程是一个串行的过程，从启动到结束会依次执行以下流程：  
初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数；  
开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译；  
确定入口：根据配置中的 entry 找出所有的入口文件；  
编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理；  
完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系；  
输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会；  
输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统。  
在以上过程中，Webpack 会在特定的时间点广播出特定的事件，插件在监听到感兴趣的事件后会执行特定的逻辑，并且插件可以调用 Webpack 提供的 API 改变 Webpack 的运行结果。  

### 是否写过Loader和Plugin？描述一下编写loader或plugin的思路？
Loader像一个"翻译官"把读到的源文件内容转义成新的文件内容，并且每个Loader通过链式操作，将源文件一步步翻译成想要的样子。  
编写Loader时要遵循单一原则，每个Loader只做一种"转义"工作。 每个Loader的拿到的是源文件内容（source），可以通过返回值的方式将处理后的内容输出，也可以调用this.callback()方法，将内容返回给webpack。 还可以通过 this.async()生成一个callback函数，再用这个callback将处理后的内容输出出去。 此外webpack还为开发者准备了开发loader的工具函数集——loader-utils。  
相对于Loader而言，Plugin的编写就灵活了许多。 webpack在运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。  

### webpack的热更新是如何做到的？说明其原理？
webpack的热更新又称热替换（Hot Module Replacement），缩写为HMR。 这个机制可以做到不用刷新浏览器而将新变更的模块替换掉旧的模块。  
原理：  
首先要知道server端和client端都做了处理工作  
第一步，在 webpack 的 watch 模式下，文件系统中某一个文件发生修改，webpack 监听到文件变化，根据配置文件对模块重新编译打包，并将打包后的代码通过简单的 JavaScript 对象保存在内存中。  
第二步是 webpack-dev-server 和 webpack 之间的接口交互，而在这一步，主要是 dev-server 的中间件 webpack-dev-middleware 和 webpack 之间的交互，webpack-dev-middleware 调用 webpack 暴露的 API对代码变化进行监控，并且告诉 webpack，将代码打包到内存中。  
第三步是 webpack-dev-server 对文件变化的一个监控，这一步不同于第一步，并不是监控代码变化重新打包。当我们在配置文件中配置了devServer.watchContentBase 为 true 的时候，Server 会监听这些配置文件夹中静态文件的变化，变化后会通知浏览器端对应用进行 live reload。注意，这儿是浏览器刷新，和 HMR 是两个概念。  
第四步也是 webpack-dev-server 代码的工作，该步骤主要是通过 sockjs（webpack-dev-server 的依赖）在浏览器端和服务端之间建立一个 websocket 长连接，将 webpack 编译打包的各个阶段的状态信息告知浏览器端，同时也包括第三步中 Server 监听静态文件变化的信息。浏览器端根据这些 socket 消息进行不同的操作。当然服务端传递的最主要信息还是新模块的 hash 值，后面的步骤根据这一 hash 值来进行模块热替换。
webpack-dev-server/client 端并不能够请求更新的代码，也不会执行热更模块操作，而把这些工作又交回给了 webpack，webpack/hot/dev-server 的工作就是根据 webpack-dev-server/client 传给它的信息以及 dev-server 的配置决定是刷新浏览器呢还是进行模块热更新。当然如果仅仅是刷新浏览器，也就没有后面那些步骤了。  
HotModuleReplacement.runtime 是客户端 HMR 的中枢，它接收到上一步传递给他的新模块的 hash 值，它通过 JsonpMainTemplate.runtime 向 server 端发送 Ajax 请求，服务端返回一个 json，该 json 包含了所有要更新的模块的 hash 值，获取到更新列表后，该模块再次通过 jsonp 请求，获取到最新的模块代码。这就是上图中 7、8、9 步骤。
而第 10 步是决定 HMR 成功与否的关键步骤，在该步骤中，HotModulePlugin 将会对新旧模块进行对比，决定是否更新模块，在决定更新模块后，检查模块之间的依赖关系，更新模块的同时更新模块间的依赖引用。
最后一步，当 HMR 失败后，回退到 live reload 操作，也就是进行浏览器刷新来获取最新打包代码。
### 如何利用webpack来优化前端性能？（提高性能和体验）
用webpack优化前端性能是指优化webpack的输出结果，让打包的最终结果在浏览器运行快速高效。  
压缩代码。删除多余的代码、注释、简化代码的写法等等方式。可以利用webpack的UglifyJsPlugin和ParallelUglifyPlugin来压缩JS文件， 利用cssnano（css-loader?minimize）来压缩css  
利用CDN加速。在构建过程中，将引用的静态资源路径修改为CDN上对应的路径。可以利用webpack对于output参数和各loader的publicPath参数来修改资源路径  
删除死代码（Tree Shaking）。将代码中永远不会走到的片段删除掉。可以通过在启动webpack时追加参数--optimize-minimize来实现
提取公共代码。  
### 如何提高webpack的构建速度？
多入口情况下，使用CommonsChunkPlugin来提取公共代码  
通过externals配置来提取常用库  
利用DllPlugin和DllReferencePlugin预编译资源模块 通过DllPlugin来对那些我们引用但是绝对不会修改的npm包来进行预编译，再通过DllReferencePlugin将预编译的模块加载进来。  
使用Happypack 实现多线程加速编译  
使用webpack-uglify-parallel来提升uglifyPlugin的压缩速度。 原理上webpack-uglify-parallel采用了多核并行压缩来提升压缩速度  
使用Tree-shaking和Scope Hoisting来剔除多余代码  
### 怎么配置单页应用？怎么配置多页应用？
单页应用可以理解为webpack的标准模式，直接在entry中指定单页应用的入口即可，这里不再赘述  
多页应用的话，可以使用webpack的 AutoWebPlugin来完成简单自动化的构建，但是前提是项目的目录结构必须遵守他预设的规范。 多页应用中要注意的是：  
每个页面都有公共的代码，可以将这些代码抽离出来，避免重复的加载。比如，每个页面都引用了同一套css样式表  
随着业务的不断扩展，页面可能会不断的追加，所以一定要让入口的配置足够灵活，避免每次添加新页面还需要修改构建配置  
### npm打包时需要注意哪些？如何利用webpack来更好的构建？
Npm是目前最大的 JavaScript 模块仓库，里面有来自全世界开发者上传的可复用模块。你可能只是JS模块的使用者，但是有些情况你也会去选择上传自己开发的模块。 关于NPM模块上传的方法可以去官网上进行学习，这里只讲解如何利用webpack来构建。  
NPM模块需要注意以下问题：
要支持CommonJS模块化规范，所以要求打包后的最后结果也遵守该规则。
Npm模块使用者的环境是不确定的，很有可能并不支持ES6，所以打包的最后结果应该是采用ES5编写的。并且如果ES5是经过转换的，请最好连同SourceMap一同上传。
Npm包大小应该是尽量小（有些仓库会限制包大小）
发布的模块不能将依赖的模块也一同打包，应该让用户选择性的去自行安装。这样可以避免模块应用者再次打包时出现底层模块被重复打包的情况。
UI组件类的模块应该将依赖的其它资源文件，例如.css文件也需要包含在发布的模块里。
基于以上需要注意的问题，我们可以对于webpack配置做以下扩展和优化：

CommonJS模块化规范的解决方案： 设置output.libraryTarget='commonjs2'使输出的代码符合CommonJS2 模块化规范，以供给其它模块导入使用
输出ES5代码的解决方案：使用babel-loader把 ES6 代码转换成 ES5 的代码。再通过开启devtool: 'source-map'输出SourceMap以发布调试。
Npm包大小尽量小的解决方案：Babel 在把 ES6 代码转换成 ES5 代码时会注入一些辅助函数，最终导致每个输出的文件中都包含这段辅助函数的代码，造成了代码的冗余。解决方法是修改.babelrc文件，为其加入transform-runtime插件
不能将依赖模块打包到NPM模块中的解决方案：使用externals配置项来告诉webpack哪些模块不需要打包。
对于依赖的资源文件打包的解决方案：通过css-loader和extract-text-webpack-plugin来实现，配置如下：

### 如何在vue项目中实现按需加载？
Vue UI组件库的按需加载 为了快速开发前端项目，经常会引入现成的UI组件库如ElementUI、iView等，但是他们的体积和他们所提供的功能一样，是很庞大的。 而通常情况下，我们仅仅需要少量的几个组件就足够了，但是我们却将庞大的组件库打包到我们的源码中，造成了不必要的开销。  
不过很多组件库已经提供了现成的解决方案，如Element出品的babel-plugin-component和AntDesign出品的babel-plugin-import 安装以上插件后，在.babelrc配置中或babel-loader的参数中进行设置，即可实现组件按需加载了。  
单页应用的按需加载 现在很多前端项目都是通过单页应用的方式开发的，但是随着业务的不断扩展，会面临一个严峻的问题——首次加载的代码量会越来越多，影响用户的体验。  
通过import(*)语句来控制加载时机，webpack内置了对于import(*)的解析，会将import(*)中引入的模块作为一个新的入口在生成一个chunk。 当代码执行到import(*)语句时，会去加载Chunk对应生成的文件。import()会返回一个Promise对象，所以为了让浏览器支持，需要事先注入Promise polyfill  



### install webpack
```
cnpm install --save-dev webpack  //安装webpack
cnpm install --save-dev webpack@<version>  //安装webpack某版本
cnpm install --global webpack  //全局安装
```

### clone webpack demos
mac: git clone https://github.com/zhangwen0424/webpack_test.git


### webpack
webpack – 构建文件  
webpack -p – 发布  
webpack --watch – 监听项目  
webpack -d – 包含 source maps方便调试  
webpack --colors – 让打包界面更好看  


## start create webpack demos
```
mkdir webpack-demos && cd webpack-demos
mkdir demo01 && cd demo01
cnpm init
```
### create package.json
$ cnpm init  
<!-- package.json  
"start": "webpack --config webpack.config.js" -->