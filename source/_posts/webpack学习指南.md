---
title: webpack学习指南
date: 2016-10-17
updated: 2016-10-18
categories: 前端
tags:
    - Webpack
    - 工具
    - 前端
---

## 前言
&nbsp;&nbsp;&nbsp;&nbsp;前端工程化已成为趋势，善于使用各种工具无疑能极大的提高工作效率，所以这段时间将陆续会有几篇关于这些工具的介绍文章，文章的内容大多是关于这些工具的文档的翻译。
&nbsp;&nbsp;&nbsp;&nbsp;本文所有资料来源都是 webpack 官网，有意看原文的戳链接： [webpack document](http://webpack.github.io/docs/.html)

<!--more-->


## 开始学习

### 模块系统

现在的网页应用有以下特点：
* 有越来越多的JavaScript代码；
* 现代浏览器能提供越来越多的接口；
* 虽然有越来越多的代码，但很少会一次加载完。  

这些代码需要得到有序管理，模块系统随之产生。

在JavaScript中，有许多不同的方式用来引入数据以及定义依赖关系，常见的有以下几种：
- 通过`<script>`标签引入（没有模块系统）
- CommonJS
- AMD及其相关
- ES6模块
- 其他……

** `<script>` 标签**

如果不利用模块系统的话，通过`<script>`标签引入如下：
```
<script src="module1.js"></script>
<script src="module2.js"></script>
<script src="libraryA.js"></script>
<script src="module3.js"></script>
```
这些数据的接口将连接到全局对象中。常见的问题如下：
- 在全局对象中产生冲突；
- 数据引入顺序非常重要；
- 开发者需要手动管理引入模块的依赖关系；
- 在数据较多的情况下会导致引入列表过长，难以管理。

**CommonJS：同步请求**  

通过利用`require`方法来加载依赖，同时返回一个接口，如下所示：

```
require("module");
require("../file.js");
exports.doStuff = function() {};
module.exports = someValue;
```

特点：
- 服务器端的模块可以重用
- 有很多已写好的模块（npm）
- 简单易用

缺点：
- 网络的阻塞调用效果不太好，而且网络请求是异步的
- 复合模块不能并行请求

应用：
- node.js
- browerify
- modules-webmake
- wreq

**AMD：异步请求**  

[异步的模块的定义](https://github.com/amdjs/amdjs-api/wiki/AMD)
有一些浏览器在处理同步引入模块时会有一些问题，为此引入了异步加载模块，具体方式如下：
```
require(["module", "../file"], function(module, file) { /* ... */ });
define("mymodule", ["dep1", "dep2"], function(d1, d2) {
  return someExportedValue;
});
```
特点：
- 符合异步加载网络请求的模式
- 并行加载符合模块

缺点：  
- 读写难度较大
- 类似于一种变通方式  

应用：  
- require.js
- curl

更多关于[CommonJS](http://webpack.github.io/docs/commonjs.html)以及[AMD](https://github.com/amdjs/amdjs-api/wiki/AMD)的内容。

**ES6模块**

ES6加入了一些JavaScript构造器，这就组成了一种模块系统，如下：
```
import "jquery";
export function doStuff() {}
module "localModule" {}
```
特点：
- 静态分析变得简单
- 指明了ES标准的方向

缺点：
- 本地浏览器支持还需要时间
- 已有的模块较少

**转移**

因为模块需要在客户端执行，那么就必须将它们从服务器端转移到浏览器端。
有两种极端的转移情况：
- 每个模块一个请求
- 所有的模块在一个请求

这两种情况都是存在的，但都不是最优的：
- 每个模块一个请求：
  - 优点：按需加载模块
  - 缺点：更多的请求以为着更多的工作量
  - 缺点：应用启动速度慢
- 所有模块在一个请求：
 - 优点：请求工作量较少，延迟较低
 - 缺点：不需要（或暂不需要）的模块也会被一并加载

**Chunked 转移方式**

面对上面两种方式所带来的问题，在大多数的案例中，采用折中的方案会取得比较好的效果。

→ 编译所有模块:将模块组合分成较小一些的组（chunks）。  
这样做能够使得初始化是没有被请求的数据在被请求时再加载，能起到加快启动速度的同时加载比需要更多的代码。

“代码分割点”可以由开发者自己决定。

→  大代码库成为可能！

注：这个构思来自于 [Google's GWT.](https://developers.google.com/web-toolkit/doc/latest/DevGuideCodeSplitting)

更多关于 [代码分割。](http://webpack.github.io/docs/code-splitting.html)

**为什么只应用在JavaScript？**

为什么模块系统仅仅用于管理JavaScript？还有许多其他资源需要管理：
- 样式
- 图片
- 字体
- html文件
- 等等  

以及转化过或者处理过的：
- coffeescript → JavaScript
- elm → JavaScript
- less stylesheets → css stylesheets
- 等等

这些处理起来非常简单，如：
```
require("./style.css");
require("./style.less");
require("./template.jade");
require("./image.png");
```
想达到这种效果，需要用到loader，更多阅读 [loader。](http://webpack.github.io/docs/using-loaders.html)

---

### Webpack及安装

**Webpack介绍**

**Webpack是一种模块打包机。**  
Webpack用于处理有依赖关系的模块，它会生成一些静态文件来表示这些模块。简单而言，如下图所示：  
![Webpack](http://webpack.github.io/assets/what-is-webpack.png)

**为什么还需要模块打包机？**  
简单而言，是因为现在的打包机无法满足大型的单页应用。而真正促使开发新型打包机的原因是代码分割和静态文件在模块化的过程中需要无缝连接。我尝试过拓展现存的打包机，但是都不能达到这些要求（注：Webpack作者）。

**目标**  
- 将依赖分割成不同的chunk，按需加载
- 让初始加载时间较少
- 每个静态文件都应该是一个模块
- 能将第三方的库整合成模块
- 打包机本身可高度定制
- 适合大型项目

**Webpack有什么不同？**  

[代码分割](http://webpack.github.io/docs/code-splitting.html)  
Webpack的依赖关系有两种类型：同步和异步。
异步依赖相当于分割点，会形成一个新的chunk。当chunk之间的关系最优化之后，每个chunk都会有一个相关文件。   

[Loaders](http://webpack.github.io/docs/loaders.html)  
 Webpack只能在本地处理JavaScript，而利用loaders能够将其他资源转化成JavaScript，通过这种手段，所有的资源都能形成模块。  

**智能解析**  
Webpack的智能解析功能使得它基本上能够处理所有第三方库，甚至允许模块以下面这种方式来表示依赖关系：`require("./templates/" + name + ".jade").`它能兼容常见的模块模式，如 [CommonJS](http://webpack.github.io/docs/commonjs.html) 以及 [AMD](http://webpack.github.io/docs/amd.html)。

[插件系统](http://webpack.github.io/docs/plugins.html)  
Webpack的强大离不开其强大的插件系统的支持。这也使得Webpack具有高度定制性，也吸引人们创造更多的开源插件

**安装**
**node.js**  
首先安装 [node.js](http://nodejs.org/)，里面包含了一种包管理工具，叫做npm。  

**Webpack**  
用npm来全局安装Webpack，全局安装的话就可以在全局环境中直接用 `Webpack` 命令了，命令行如下：  
`$ npm install webpack -g`  

**在项目中引入**  
做项目的时候最好以项目依赖的方式引入Webpack，那样的话就不会去依赖全局的Webpack了。  
首先利用npm新建一个package.json配置文件，命令行如下：  
`$ npm init`  
上面提到的项目依赖的方式安装Webpack可以通过以下命令行实现：  
`$ npm install webpack --save-dev`

**版本**  
有两个版本的Webpack可供下载，一个是稳定版本，另一个是测试版本。测试版本有`-beta`的后缀，这个版本会包含一些带有实验性质的性能，而且也没有经过大量的测试。所以建议对稳定性能要求较高的同志们选择稳定版本，命令行如下：  
`$ npm install webpack@1.2.x --save-dev`

**开发者工具**  
如果需要使用开发者工具，就需要安装了，命令行如下：  
`$ npm install webpack-dev-server --save-dev`

---

### 基本用法

**安装**
上面已经提到可全局安装或者以项目依赖的方式安装。在实际项目中，建议都以项目依赖的方式安装，本文为了方便展示，都是以全局安装为例的。  

**开始使用**  
- 首先用CommonJS语法创建一个模块化的JavaScript项目，名字为`cat.js`，代码如下：  
```
    // cats.js
    var cats = ['dave', 'henry', 'martha'];
    module.exports = cats;
```
  ```
    // app.js(Entry Point)
    cats = require('./cats.js');
    console.log(cats);
  ```
  `Entry Point`是项目接入模块的入口，Webpack也是从这个接口开始检查各个模块之间的依赖关系的。

- 打包文件：Webpack需要指定入口文件（app.js），同时也需要明确的指定输出文件的名字（app.bundle.js），指令如下：  
  `webpack ./app.js app.bundle.js`  
  然后Webpack会解读入口文件同时分析其依赖（以及依赖的依赖），分析完以后，会将所有的依赖绑定输出到输出文件中（本例为app.bundle.js）。
  ![webpack](https://dtinth.github.io/webpack-docs-images/usage/how-it-works.png)

- 然后就可以运行了，在node中运行及结果如下：
```
node app.bundle.js
["dave", "henry", "martha"]
```
  当然了，也可以在浏览器的环境下运行。  

**使用进阶**  
webpack具有很多高级功能，很多功能通过命令行工具很难体现出来，这时候我们就需要去创建配置文件了。

- 项目结构：在实际的生产环境中，我们会将源文件和输出文件放在不同的文件夹中以便于管理，典型的例子如下图所示：
  ![folders](https://raw.githubusercontent.com/dtinth/webpack-docs-images/2459637650502958669ea6b11bf49dc0b3b083ae/usage/project-structure.png)

 > *在实际的生产环境中会有很多类似但并不完全相同的项目结构，比如有些项目会将 src 文件夹命名为 APP ，会将 bin 文件夹命名为 dist 或者是 build ，等等诸如此类，其实都是一样的。*

- 配置文件：当项目变得越来越庞大复杂的时候，手动设置这些就显得不是那么明智了，这时候可以创建一个配置文件，名字叫做`webpack.config.js`:
 1. 创建一个`webpack.config.js`的配置文件：
   ```
       module.exports = {
        entry: './src/app.js',
        output: {
            path: './bin',
            filename: 'app.bundle.js'
        }
    };
   ```
 2. 将配置文件放在合适的位置，现在运行webpack只需要以下代码：
    `webpack`
    然后webpack就会去解析配置文件，并按照配置文件中的配置来解读接入文件以及输出文件到指定位置。

- 引入loaders：webpack本身只支持JavaScript模块，为了支持其他模块，就需要引入各种loader了。loader能够将其他资源加载成webpack能够识别的JavaScript。典型的例子如 babel-loader，json-loader等，如下图：
  ![babel-loader](https://dtinth.github.io/webpack-docs-images/usage/babel-loader.png)
  ![json-loader](https://dtinth.github.io/webpack-docs-images/usage/json-loader.png)
  ![yaml-loader](https://dtinth.github.io/webpack-docs-images/usage/yaml-loader.png)

- 以babel-loader为例说明如下：
  1. 安装Babel：
     ` npm install --save-dev babel-core babel-preset-es2015`
  2. 安装babel-loader：
     ` npm install --save-dev babel-loader`
  3. 新建一个.babelrc文件，这个文件用来配置Babel，使其利用预先设置的语法（es2015）来解析。.babelrc的内容如下：
     ` { "presets": [ "es2015" ] }`
  4. 更改 webpack.config.js 文件，使的所有的 .js 文件都用 babel-loader 来处理：
  ```
      module.exports = {
      entry: './src/app.js',
      output: {
          path: './bin',
          filename: 'app.bundle.js',
      },
      module: {
          loaders: [{
              test: /\.js$/,
              exclude: /node_modules/,
              loader: 'babel-loader'
          }]
      }
    }
  ```
   > *注意：这里讲node_modules文件排除在外了，因为不排除的话，这些外部的插件库也会被Babel处理，从而减缓编译速度*  

  5. 安装所需要的其他库（以jQuery为例）：
     ` npm install --save jquery babel-polyfill`
   > *注意：这里没有用 --save-dev，因为这些库只有在项目运行时才会使用，同时为了能在低版本的浏览器中使用ES6的特性，这里安装了babel-ployfill。*

  6. 编辑 `src/app.js` 文件：
  ```JavaScript
    import 'babel-polyfill';
    import cats from './cats';
    import $ from 'jquery';

    $('<h1>Cats</h1>').appendTo('body');
    const ul = $('<ul></ul>').appendTo('body');
    for (const cat of cats) {
        $('<li></li>').text(cat).appendTo(ul);
    }
  ```
  7. 用webpack来打包模块：
     `webpack`
  8. 创建一个index.html文件，并将打包好的文件引入，以便于在浏览器中展示出来：
  ```JavaScript
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
        </head>
        <body>
            <script src="bin/app.bundle.js" charset="utf-8"></script>
        </body>
    </html>
  ```
    当打开index.html时，不出意外的话会看到下图：
    ![cats](https://dtinth.github.io/webpack-docs-images/usage/cats.png)

- 引入插件：在实际生产环境中，我们可能会需要使用一些插件来处理打包好的文件，比如说我们可能会想压缩文件以便于更快的加载速度，这时候就需要使用插件了，以 `uglify` 插件为例：
 ```JavaScript
    const webpack = require('webpack');

    module.exports = {
        entry: './src/app.js',
        output: {
            path: './bin',
            filename: 'app.bundle.js',
        },
        module: {
            loaders: [{
                test: /\.jsx?$/,
                exclude: /node_modules/,
                loader: 'babel-loader',
            }]
        },
        plugins: [
            new webpack.optimize.UglifyJsPlugin({
                compress: {
                    warnings: false,
                },
                output: {
                    comments: false,
                },
            }),
        ]
    }
 ```
由于webpack本身自带 Uglify 这个插件，所以使用时不需引入，但是如果需要使用其他没有内置的插件的时候，还是需要手动引入的，而且自己也可以写插件。

---

### 使用 Loaders

**什么是 loaders ？**  
loaders是一些对你的项目中的资源进行转化的工具，它们是一些把源文件的路径作为参数的函数，然后通过函数返回新的路径。
例如，webpack中可以通过使用loader来加载CoffeeScript或者是JSX。

loader的特征：
- loaders 可以链式应用（如上一节提到的.yml文件的解析）。链式应用的中间文件的格式可以是任意的，只要最后输出的格式是JavaScript格式即可
- loaders 可以是同步的或者是异步的；
- loaders 可以在nodejs环境下运行，也可以实现所有可能实现的功能；
- loaders 可接受查询参数，可以利用这个功能来配置loader；
- loaders 可以在配置文件中被绑定到正则表达式或者扩展中；
- loaders 可以通过npm来发布或者是安装；
- 一般的模块都可以通过 `package.json loader` 在输出` main `之外还输出一个 loader ；
- loaders 可以读取配置文件；
- 插件可以使 loaders 的功能更强大；
- loaders 可以生成任意的附加文件；
- [等等](http://webpack.github.io/docs/loaders.html)

**解析loaders**  
loaders 的解析方式和模块类似，loader 模块一般会输出一个 nodejs 能够识别的函数。通常情况下我们会用 npm 来管理 loaders ，但是我们也可以以文件的形式直接放在应用文件夹中。

- 引用 loaders
  按照惯例，我们通常将 loaders 命名为` xxx-loader `其中 xxx 表示的就是具体的名称，比如 `json-loader`。在引用的时候，既可以用全名，也可以用简写（不包括loader部分）。
  loader 的命名规则以及搜索优先顺序被定义在 webpack 配置 API 文件 ` resolveLoader.moduleTemplates` 中。
  loader 的命名规则有时候会派上用场，尤其是利用 `require()` 来引用它们的时候。

- 安装 loaders
  只要 npm 中有你需要的 loaders， 那么那就可以通过以下任意一种方式来安装它们：
  `$ npm install xxx-loader --save` 或者是 `$ npm install xxx-loader --save-dev`
  (其中后者是以生产依赖的方式安装，前者为普通安装。以生产依赖的方式安装会自动改变 webpack 的配置文件中的依赖部分)

**用法**
有很多途径都能在项目中应用 loaders：
- 直接通过 `require` 声明来引用
- 通过配置文件来配置
- 通过 CLI 来配置


以下将分别就这三种方式进行说明：  
- 通过 `require` 方式  
> *注意：如果你不能确定你的脚本的运行环境，那么就尽可能不要使用这种方式，而是利用配置规则来使用 loaders。*

  利用 `require `声明（或者 `define`, `require.ensure` 声明 ）是可以规范化使用 loader 的，只要通过使用 `!` 符号将需处理文件和 loader 隔开。如果有多个 loader， 那么将遵循从右到左的顺序依次解析。 具体例子如下：
  ```JavaScript
    require("./loader!./dir/file.txt");
    // uses the file "loader.js" in the current directory to transform
    // "file.txt" in the folder "dir".

    require("jade!./template.jade");
    // uses the "jade-loader" (that is installed from npm to "node_modules")
    // to transform the file "template.jade"
    // If configuration has some transforms bound to the file,
    // they will still be applied.
    // 如果此时配置文件中规定了需要处理这个文件，那么这时候会处理

    require("!style!css!less!bootstrap/less/bootstrap.less");
    // the file "bootstrap.less" in the folder "less" in the "bootstrap"
    // module (that is installed from github to "node_modules") is
    // transformed by the "less-loader". The result is transformed by the
    // "css-loader" and then by the "style-loader".
    // If configuration has some transforms bound to the file,
    // they will not be applied.
    // 由于此处在规则的最前面加了前缀 “！”， 如果配置文件中规定了需要处理这个文件，
    // 那么这时候仍然不会处理。
  ```


- [配置文件方式](http://webpack.github.io/docs/configuration.html)
   在配置文件中可以通过用正则表达式的方式来绑定 loaders ，如下所示：
    ```JavaScript
        {
            module: {
                loaders: [
                    { test: /\.jade$/, loader: "jade" },
                    // => "jade" loader is used for ".jade" files

                    { test: /\.css$/, loader: "style!css" },
                    // => "style" and "css" loader is used for ".css" files
                    // Alternative syntax:
                    { test: /\.css$/, loaders: ["style", "css"] },
                ]
            }
        }
    ```

- [CLI 方式](http://webpack.github.io/docs/cli.html)
   可以通过命令行工具来绑定 loaders， 如下所示：
    `$ webpack --module-bind jade --module-bind 'css=style!css'`
     上面的例子会使得利用 `jade-loader` 来处理 `.jade` 文件， 用`css-loader & style-loader` 来处理 `.css` 文件。

**查询参数**
  可以通过使用 `?` 的方式来决定是否使用 loader，比如 `url-loader?mimetype=image/png` 表示就是，如果媒体文件都是图片格式， `mimetype=image/png`，那么就使用 `url-loader`来进行处理。
  注意：查询语法根据不同的 loader 可能会不一样，具体情况需要查询相应的文档。但是一般而言，都支持常见的查询语法，如 `(?key=value&key2=value2) `，或者JSON对象如 `(?{"key":"value","key2":"value2"})`

与上面提到的三种方式相对应的，利用查询的写法如下：
- 通过 `require()` 方式：
  `require("url-loader?mimetype=image/png!./file.png");`
- 通过配置文件：
  `{ test: /\.png$/, loader: "url-loader?mimetype=image/png" }`
  或者写的好看一下：
```JavaScript
    {
    test: /\.png$/,
    loader: "url-loader",
    query: { mimetype: "image/png" }
    }
```
- CLI方式：
  `webpack --module-bind "png=url-loader?mimetype=image/png"`

---

### 使用插件

使用插件能够增强 webpack 的功能，比如，利用 [ BellOnBundlerErrorPlugin](https://github.com/senotrusov/bell-on-bundler-error-plugin) 插件就能提示在打包过程中出现的错误。

**内置插件**
对于内置插件，如果在 webpack 的配置文件中有用到它们的功能，那么就会将这些插件包含在模块中。例如：
```JavaScript
    // webpack should be in the node_modules directory, install if not.
    var webpack = require("webpack");

    module.exports = {
        plugins: [
            new webpack.ResolverPlugin([
                new webpack.ResolverPlugin.DirectoryDescriptionFilePlugin("bower.json", ["main"])
            ], ["normal", "loader"])
        ]
    };
```

**外部插件**
外部的插件可以通过 `npm` 来安装，例如：
`npm install component-webpack-plugin`
安装完之后就可以使用了，如下：
```JavaScript
    var ComponentPlugin = require("component-webpack-plugin");
    module.exports = {
        plugins: [
            new ComponentPlugin()
        ]
    }
```
当使用 `npm` 来安装第三方插件的时候，建议使用这个工具: https://www.npmjs.com/package/webpack-load-plugins ，它会自动检测依赖中的所有插件，然后在需要的时候懒加载它们。

**更多阅读**
[了解更多，可查看插件列表](http://webpack.github.io/docs/list-of-plugins.html)

---

### 故障排查

**解析过程**
- 常见故障：
    - 利用 `--display-error-details` 可以得到详细信息
    - 阅读配置文件，关于故障分析的部分都在 `resolve`
    - loaders 的配置文件中有对应的故障分析 `resolveLoader`


- npm 链接模块找不到所需依赖
  &nbsp;&nbsp;&nbsp;&nbsp;node.js 的模块解析算法非常简单：系统寻找模块依赖时，会在所需模块的父文件夹的 `node_modules` 文件夹中寻找。如果你 npm 链接的带有同级依赖的模块没有放在根目录下，那么系统就无法找到这些模块（你可能会认为带有 `npm link` 的 `peerDependencies` 是 node.js 的设计缺陷）。需要注意的是应用的依赖也是一种 `peerDependencies`， 即使这种依赖并没有在模块的 `package.json` 文件中列出来。
   &nbsp;&nbsp;&nbsp;&nbsp;要在 webpack 中分析这个问题其实很简单：只需要将应用的 `node_modules` 文件夹放在解析路径中，具体的设置例子如下：
    ```JavaScript
        module.exports = {
          resolve: { fallback: path.join(__dirname, "node_modules") },
          resolveLoader: { fallback: path.join(__dirname, "node_modules") }
        };
    ```

**监测过程**
- 监测过程中， webpack 不会在资源有变动时重编译

- 监测到文件变化，但是文件并没有更新
   &nbsp;&nbsp;&nbsp;&nbsp;可以确定的是，在 webpack 中，如果运行时加上了 `-progress` 标签，那么资源的变动将不会被监测。如果保存时能看到进展但却没有文件输出，那么就可能是配置上的问题，而不是文件监测问题了。
    `webpack --watch --progress`

- 监测器不够
   &nbsp;&nbsp;&nbsp;&nbsp;首先需要确认你的系统中是否有足够可用的检测器，如果可用数量太少，那么 webpack 中的检测器可能就检测不到变化了：
    `cat /proc/sys/fs/inotify/max_user_watches `
    对于 Arch 用户，将 `fs.inotify.max_user_watches=524288` 加到 `/etc/sysctl.d/99-sysctl.conf` 文件中，然后执行 `sysctl --system`。对于 Ubutu 用户：`echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p. `

- OS-X FSevents bug
   在 OS-X 系统中，文件夹可能会崩溃，具体可参考下面的文章：
    [OS X FSEvents bug may prevent monitoring of certain folders](http://feedback.livereload.com/knowledgebase/articles/86239-os-x-fsevents-bug-may-prevent-monitoring-of-certai)

- Windows 路径
   &nbsp;&nbsp;&nbsp;&nbsp;在 webpack 中的很多配置选项默认都是绝对路径。 `__dirname + "/app/folder"` 这种写法是错误的，因为在 Windows 系统中路径的分隔符是 `\`。这有时候会产生一些问题。建议使用正确的分隔符，比如 `path.resolve(__dirname, "app/folder")` 或者 `path.join(__dirname, "app", "folder").`

- Vim
   &nbsp;&nbsp;&nbsp;&nbsp;有些型号的机器上，Vim 的 ` backupcopy option` 会被默认设置成 `auto`。这有可能会影响到系统的文件监测机制。所以建议将这个选项设置为 `yes`，这样的话就会在保存的时候覆盖原文件并保存一份副本。Vim 中的设置如下：
    `:set backupcopy=yes`

- WebStorm
   &nbsp;&nbsp;&nbsp;&nbsp;当使用 JetBrains 的 WebStorm 的 IDE 的时候，你可能会发现在保存更改过的文件时并没有触发预想中的检测器。这时候就需要设置 `safe write` 选项了，这个选项决定了是否在保存更改过的文件前保存一份原文件在临时路径中： 取消下列设置
    `File > Settings... > System Settings > Use "safe write" (save changes to a temporary file first).`

---

## 实例操作

> 文档比较混乱，所以先放一放，后面的部分写好再来。

---

## 指导文件

### CommonJs
为了解决JS中作用域的问题， CommonJS 小组定义了一种模块格式，这可以确保所有的模块都在自己的命名空间执行。
怎样能到达到这个目的呢？其一需要在模块中明确的输出那些适用于全局作用域的变量，其二需要定义其他模块需要的变量。
为了达到这个效果， CommonJS 给我们提供了两个工具：
- 利用 `require()` 函数可以将一个指定的模块引入到现在的作用域；
- 利用 `module` 对象可以将现在作用域中内容输出；

**简单的例子**
下面是一个不用 CommonJS 的例子：
首先在一个js文件中定义一个变量，这个文件在之后其他的文件中将会被用到：
```JavaScript
// salute.js
var MySalute = "hello";
```
然后在另一个文件中应用这个变量：
```JavaScript
// world.js
var Result = MySalute + " world!"
```

**定义模块**
上面的例子中将会因为 `MySalute` 没有被定义而报错，我们应该将这些文件定义为模块：
```JavaScript
// salute.js
var MySalute = "hello";
module.exports = MySalute;
```
```JavaScript
// world.js
var Result = MySalute + "hello world!";
module.exports = Result;
```
在这两个例子中，我们将变量传入到了一个特殊的变量 `module` 中，这样一来 CommonJS 的模块系统就知道模块中需要被输出的对象了： `salute.js` 中输出 `MySalute` 对象，  `world.js` 中输出  `Result` 对象。

**模块依赖**
上面已经很接近了，但是还差一步：定义依赖。虽然都分别定义了自个为独立的模块，但是 `world.js` 还是不知道在哪里找到 `MySalute` 的定义：
```JavaScript
// salute.js
var MySalute = "hello";
module.exports = MySalute;
```
我们需要做的最后一步就是在 `world.js` 中引入模块的依赖：
```JavaScript
// world.js
var MySalute = require("./salute");  // This is it!
var Result = MySalute + "world!";
module.exports = Result;
```
需要注意，在我们利用 `require` 引用的时候，并没有使用 `salute.js` 的全名，意思就是我们可以省略后缀。 `./` 符号表示的是相对路径：引用文件和被引用文件在同一个文件夹目录下。

**最后的例子**
```JavaScript
// moduleA.js
module.exports = function( value ){
    return value*2;
}
```
```JavaScript
// moduleB.js
var multiplyBy2 = require('./moduleA');
var result = multiplyBy2( 4 );
```

---

### AMD
AMD (Asynchronous Module Definition) 的产生是因为有些人认为 CommonJS 的模块系统暂时还不适合浏览器环境，因为从本质上来说 CommonJS 的模块是同步加载的。
AMD 指出了一种模块化 JavaScript 的规范， 按照这个规范模块能够异步加载它们的依赖，这就解决了同步加载带来的问题。

**规范说明**
在 AMD 中，模块是利用` define` 来定义的。
*define*
在 AMD 规范中利用 `define` 函数定义模块的形式如下：
`define(id?: String, dependencies?: String[], factory: Function|Object);`
*id*
模块的名字，为可选项
*dependencies*
这个参数是用来指出正在被定义的这个模块所需要依赖的其他模块，这个参数是个数组，里面包含了依赖模块的标识符。这也是一个可选参数，如果省略不写，默认值则是：` ["require", "exports", "module"]`
*factory*
这个参数是用来定义模块的。它可以是个函数（这个函数应该会被调用），或者是个对象。如果这个参数是个函数，那么函数的返回值将会是这个模块的输出值。

**例子**
简单的来看一些例子。

- 具名模块
  定义一个依赖 `jquery` 的名字为 `myModule` 的模块：
```JavaScript
define('myModule', ['jquery'], function($) {
    // $ is the export of the jquery module.
    $('body').text('hello world');
});
// and use it
require(['myModule'], function(myModule) {});
```
 注意：在 webpack 中一个具名模块只在本地有效，而在 Require.js 中则是全局有效的。

- 匿名模块
  定义一个匿名模块：
```JavaScript
define(['jquery'], function($) {
    $('body').text('hello world');
});
```

- 复杂模块
  定义一个具有多重依赖的模块，需要注意的是每个模块的输出都会传到 `factory` 函数中：
```JavaScript
define(['jquery', './math.js'], function($, math) {
    // $ and math are the exports of the jquery module.
    $('body').text('hello world');
});
```

- 输出值
  定义一个输出自身的模块：
```JavaScript
define(['jquery'], function($) {

    var HelloWorldize = function(selector){
        $(selector).text('hello world');
    };

    return HelloWorldize;
});
```

- 定义一个利用 `require` 来加载依赖的模块：
> 因为没有定义依赖， webpack 将将上面提到的默认值传入后面的函数 ，然后就可以利用这些参数做文章了。

    ​```JavaScript
    define(function(require) {
        var $ = require('jquery');
        $('body').text('hello world');
    });
    ​```

---

### 代码分割
&nbsp;&nbsp;&nbsp;&nbsp;对于大型的网页应用而言，把所有的代码放在一个文件中往往会效率低下，特别是当其中有些代码块只需要在特定环境下加载的时候。 webpack 中有一个特性，这个特性能够将代码分割成许多的 `chunks` ，这些代码块只会在被需要的时候才加载。有些其他的打包机将被分割的代码块称作为 `layers`, `rollups` 或者 `fragments`。这个特性就叫做“代码分割”。
&nbsp;&nbsp;&nbsp;&nbsp;这是一个可选的特性。我们可以在代码中定义代码分割点，然后 webpack 内部来处理依赖关系，输出文件和执行环境等事物。
&nbsp;&nbsp;&nbsp;&nbsp;在这里需要澄清一个概念：代码分割的功能不仅仅是将普通的代码提取分割成共享的代码块（chunk），它最重要的功能其实是将代码分割成能够 **按需加载** 的代码块。这样就会减少网页应用的初始加载量，并使得其他代码能够按需加载。

**定义分割点**
AMD 和 CommonJS 通过不同的方式使得代码按需加载。这些方法都是有效的，分别如下所示：

- CommonJS： `require.ensure`
    ```JavaScript
    require.ensure(dependencies, callback)
    ```
    `require.ensure` 方法可以确保当调用回调函数的时候，所有在 `dependencies` 中的依赖都能够被同步调用。`callback` 函数再被调用的时候会将 `require` 函数当做参数传入。
    例子如下：
    ```JavaScript
    require.ensure(["module-a", "module-b"], function(require) {
        var a = require("module-a");
        // ...
    });
    ```
    注意：`require.ensure` 函数仅仅是加载模块，并不会执行它们。

- AMD： `require`
  AMD 规范中定义了一种异步的 `require` 方法，如下所示：
  `require(dependencies, callback)`
  当被调用时，所有的依赖都会被加载，而且加载的依赖的输出将会被传入到回调函数中：
```JavaScript
require(["module-a", "module-b"], function(a, b) {
    // ...
});
```
    注意： AMD 中 `require` 方法是会加载并执行模块的。在 webpack 中模块式从左到右执行的。
    注意：回调函数是可以省略的。

- ES6 模块
  webpack 不支持 ES6 模块，需要根据编译器支持哪种格式的模块格式来选择是使用 `require` 还是 `require.ensure`.
  webpack 1.xx（即将到来的2.0.0）版本本身并不支持 ES6 模块。但是可以利用编译器，比如 `Babel` 来将 ES6 中的 `import` 语法转换成 CommonJS 或者 AMD 模块，从而达到目的。这种方法很有效，但是动态加载的时候会产生一个警告。
  模块的语法（`import x from "foo" `）被故意设计成只能静态分析，所以不能够动态引入模块：
```
// INVALID!!!!!!!!!
[“lodash”, “backbone”].forEach(name => import name )
```
 不过幸运的是，在规范中提到可以利用一个 JavaScript API 中的 `loader` 来处理动态引入的情况：`System.load(or Sytem.import)`。这个 API 能起到和上面提到的 `require` 一样的作用。然而，大部分的编译器并不支持将 `System.load` 转化成 `require.ensure`，所以这时候如果想要动态的代码分割的话只能是直接去做了。
 ```JavaScript
     //static imports
    import _ from 'lodash'

    // dynamic imports
    require.ensure([], function(require) {
      let contacts = require('./contacts')
    })
 ```

- Chunk 内容
  在一个分割点内的所有依赖都会被包括在一个 Chunk 中，它们会被递归的加到这个 chunk 中。
  如果你将一个函数表达式作为回调函数传入（或者绑定）到一个分割点， Webpack 会自动的将这个函数表达式中所需要的依赖同时打包到这个 chunk 中。

- Chunk 优化
 - 如果两个 chunks 包含了同样的模块，那么这两个 chunk 将会合并成一个。这会造成 chunks 会有多重父级；
 - 如果一个模块在一个 chunk 的所有父级中都出现了，那么这个模块将会从这个 chunk 中移除；
 - 如果一个 chunk 包含了另一个 chunk 中的所有模块，那么将会形成多重 chunks。

- Chunk 加载
   基于一个叫做 `target` 的配置选项，关于 chunk 加载的运行环境会被加入到 `bundle` 文件中，例如：当 `target` 是 web 时， chunks 将会通过 jsonp 来加载。一个 chunk 只会加载一次， 并行的请求也会合并成一个请求。运行环境会检查已经加载的 chunk 是否形成复合 chunks。

- Chunk 类型
 - 入口 chunk
     入口代码块包含了运行环境以及一些模块。如果 chunk 中包含了模块 `Θ`， 那么将在运行环境中执行它。如果不包含这个模块，就会等到包含这个模块的 chunk 然后再执行（每一次遇到包含模块 `Θ` 的时候都会执行一次）。
 - 普通 chunk
     普通的 chunk 不包含运行环境，只包含一些模块。里面的结构由 chunk 加载算法来决定。例如，对于 jsonp 而言，模块将会被包含在 jsonp 的回调函数中。 chunk 里面也包含了一个由它来完成的 chunk id 的列表。
 - 初始 chunk（非入口）
     初始 chunk 是普通 chunk 的一种。它们之间唯一的区别是在优化的时候，初始 chunk 会更加被重视，因为它会影响到初始加载时间（就像入口 chunk 一样）。这种类型的 chunk 会在结合 `CommonChunkPlugin` 使用的时候产生。

- 拆解 app 以及分离代码
   为了将 app 拆解成两个文件，比如app.js 以及 vendor.js， 我们可以在 vendor.js 中利用 `require` 来引入 vendor 参数中的文件。然后将这个名字传入到 `CommonsChunkPlugin`中，如下所示：
 ```JavaScript
    var webpack = require("webpack");

    module.exports = {
      entry: {
        app: "./app.js",
        vendor: ["jquery", "underscore", ...],
      },
      output: {
        filename: "bundle.js"
      },
      plugins: [
        new webpack.optimize.CommonsChunkPlugin(/* chunkName= */"vendor", /* filename= */"vendor.bundle.js")
      ]
    };
 ```
 这会将 vendor chunk 中所包含的所有模块从 app chunk 中移除。 `bundle.js` 中将只会包含所有的 app 代码，不带有任何的依赖，所有的依赖代码都在 `vendor.bundle.js` 中。
 在 HTML 文件中，需要先加载 `vendor.bundle.js` 然后再加载 `bundle.js`，如下所示：
 ```JavaScript
 <script src="vendor.bundle.js"></script>
 <script src="bundle.js"></script>
 ```

- 多个入口 chunks
   通过[配置](http://webpack.github.io/docs/configuration.html)可以实现多个入口点，这同时会形成多个入口 chunks。入口 chunk 中包含了运行环境，而一个页面中只能包含一个运行环境（当然也会有例外）。

- 运行多个入口点
   通过插件 `CommonsChunkPlugin` 可以将运行环境转移到 commons chunk 中。入口点这时候在初始 chunk 中。虽然只有一个初始 chunk 可以被加载，但是多个入口 chunk 可以被加载。这就说明了在同一个页面中运行多个入口点是可能的。例子如下：
 ```JavaScript
    var webpack = require("webpack");
    module.exports = {
       entry: { a: "./a", b: "./b" },
       output: { filename: "[name].js" },
       plugins: [ new webpack.optimize.CommonsChunkPlugin("init.js") ]
}
 ```
 引入的时候，按如下顺序：
 ```JavaScript
    <script src="init.js"></script>
    <script src="a.js"></script>
    <script src="b.js"></script>
 ```

- Commons Chunk
   插件 `CommonsChunkPlugin` 可以将多个入口 chunks 的模块转移到一个新的入口文件（也就是 commons chunk）中。运行环境也被转移到了 commons chunk 中。这意味着原来的入口 chunk 现在变成了初始 chunk。了解更多[插件选项。](http://webpack.github.io/docs/list-of-plugins.html)

- 优化
   有一些用于优化的插件能够根据特别的标准将 chunk 合并起来，参考[插件列表](http://webpack.github.io/docs/list-of-plugins.html)

- 具名 chunks
   `require.ensure` 函数可以接收额外的第三个参数，这个参数必须是字符串类型。如果两个分割点传入了同样的字符串，那么它们将利用同样的 chunk。

- `require.include`
 ```JavaScript
 require.include(request)
 ```
 `require.include` 是 Webpack 中一个特殊的函数，它可以将模块加入到现在的 chunk 中，但是不会去执行它（打包的时候会将声明移除）。例子如下：
 ```JavaScript
    require.ensure(["./file"], function(require) {
      require("./file2");
    });

    // is equal to

    require.ensure([], function(require) {
      require.include("./file");
      require("./file2");
    });
 ```
 如果模块是在复合子代码块中，那么这个函数将非常有用。在父级代码块中运用这个函数引入模块将会使得这个子代码块中的模块实例都消失。

---

### 样式表

**内嵌样式表**
通过利用 `style-loader` 以及 `css-loader` 使得将样式表内嵌在 JavaScript 打包文件中变得可能。这种方式下你可以将你的样式表和其他模块一起模块化。引用方式非常简单： `require("./stylesheet.css")`。使用步骤如下：

- 安装
  首先从 `npm` 上下载 `loaders`
  `npm install style-loader css-loader --save-dev`

- 配置
  下面是一个配置参考：
```JavaScript
{
    // ...
    module: {
        loaders:[
            { test: /\.css$/, loader: "style-loader!css-loader" }
        ]
    }
}
```
 > 注意：对于一些需要编译的 css 样式，可以参考相对应的 loader 的配置例子，然后链式调用它们。

 需要记住的是我们很难管理模块的执行顺序，所以最好设计好样式表使得顺序无关紧要。（在一个 css 文件中，顺序还是可靠的。）

- 使用
  使用非常简单：
```JavaScript
// in your modules just require the stylesheet
// This has the side effect that a <style>-tag is added to the DOM.
require("./stylesheet.css");
```

**独立的样式打包**
结合使用 [extract-text-webpack-plugin](https://github.com/webpack/extract-text-webpack-plugin) 这个插件，可以产生一个本地的 css 输出文件。
结合代码分割，我们可以使用两种不同的模式：
 - 针对每一个初始 chunk 都创建一个 css 文件， 将样式表内嵌至附加的 chunk 中。（推荐做法）
 - 针对每一个初始 chunk 都创建一个 css 文件，并且这个文件中包含了附加 chunk 的样式。  

从初始加载速度优化的角度考虑，推荐使用第一种模式。因为缓存和 http 请求头的原因，在一些具有多个入口点的小型应用中，第二种模式可能会更好一些。

步骤如下：
- 安装插件
   `npm install extract-text-webpack-plugin --save`

- 处理初始 chunk 中的样式生成分离的 css 文件输出
   下面展示的虽然是多个入口点的例子，但是这种方式也适合单个入口点。
 ```JavaScript
    // webpack.config.js
    var ExtractTextPlugin = require("extract-text-webpack-plugin");
    module.exports = {
        // The standard entry point and output config
        entry: {
            posts: "./posts",
            post: "./post",
            about: "./about"
        },
        output: {
            filename: "[name].js",
            chunkFilename: "[id].js"
        },
        module: {
            loaders: [
                // Extract css files
                {
                    test: /\.css$/,
                    loader: ExtractTextPlugin.extract("style-loader", "css-loader")
                },
                // Optionally extract less files
                // or any other compile-to-css language
                {
                    test: /\.less$/,
                    loader: ExtractTextPlugin.extract("style-loader", "css-loader!less-loader")
                }
                // You could also use other loaders the same way. I. e. the autoprefixer-loader
            ]
        },
        // Use the plugin to specify the resulting filename (and add needed behavior to the compiler)
        plugins: [
            new ExtractTextPlugin("[name].css")
        ]
    }
 ```
 然后你会得到如下文件：
 - `posts.js  posts.css`
 - `post.js  post.css`
 - `about.js  about.css`
 - `1.js  2.js`（包含内嵌样式）

- 所有样式都具有各自的 css 输出文件
  利用第二种模式，只需要将 `allChunks` 选项设置成 `true` 即可：
```JavaScript
    // ...
    module.exports = {
        // ...
        plugins: [
            new ExtractTextPlugin("style.css", {
                allChunks: true
            })
        ]
    }
```
 然后将得到如下文件：
 - `posts.js  posts.css`
 - `post.js  post.css`
 - `about.js  about.css`
 - `1.js  2.js`（不包含内嵌样式）

- 在 commons chunk 中的样式
  可以结合利用 `CommonsChunkPlugin` 及分离的样式文件来为 commons chunk 生成样式文件：
```JavaScript
    // ...
    module.exports = {
        // ...
        plugins: [
            new webpack.optimize.CommonsChunkPlugin("commons", "commons.js"),
            new ExtractTextPlugin("[name].css")
        ]
    }
```
然后将得到如下输出文件：
 - `commons.js  commons.css`
 - `posts.js  posts.css`
 - `post.js  post.css`
 - `about.js  about.css`
 - `1.js  2.js`（包含内嵌样式）
     或者设置 `allChunks: true`，得到
 - `1.js 2.js`（不包含内嵌样式）

---

### 优化

**压缩**
为了压缩文件中的 JavaScript（如果用了 css-loader，css 文件也可以），webpack 提供了一个简单的选项：
`--optimize-minimize` 对应于：`new webpack.optimize.UglifyJsPlugin()`
这是一个简单而有效的优化网页应用的方法。
你应该知道（如果你看过之前的文档）在 webpack 中是通过给 chunk 和模块赋予 id 的方式来辨别它们的。通过一个选项， webpack 可以分辨 id 的分布，并将具有较小长度的 id 分配给这些模块或者 chunk：
`--optimize-occurrence-order` 对应于：`new webpack.optimize.OccurrenceOrderPlugin()`
在对文件体积的影响程度上，入口 chunk 具有更高的优先级。

**去重**
如果你使用了一些拥有不错的依赖关系的库，那么在打包的过程中就可能会产生一些完全相同的文件。webpack 可以识别这些文件，然后删除重复的。在运行环境下通过利用函数替代重复代码的方式，从而避免打包文件中包含重复代码文件。这对语义化不会有什么影响。可以通过下面的方式来实现这个功能：
`--optimize-dedupe` 对应于：`new webpack.optimize.DedupePlugin()`
利用这种特性的时候会在入口 chunk 中引入一些额外的代码。

**Chunks**
在编写代码的时候，为了达到按需加载的目的，你可能已经设定好了一些代码分割点。但是在编译之后，你可能会发现产生了非常多的很小的 chunk，这会导致 HTTP 请求头数据量非常大。不过不用担心，通过以下两项设置，我们可以在 webpack 中利用合并的方式来处理这些 chunks：
- 限制允许存在的 chunk 的数量（比如15个）： `--optimize-max-chunks 15  new webpack.optimize.LimitChunkPlugin({maxChunks: 15})`
- 限制允许存在的 chunk 的最小体积（比如 10000）：`--optimize-min-chunk-size 10000 new webpack.optimize.MinChunkSizePlugin({minChunkSize: 10000})`
  webpack 会通过合并的方式来处理这些 chunk（会优先处理具有重复模块的 chunk）。任何 chunk 都不会被合并到入口 chunk 中，这主要是为了避免影响到初始页面加载的时间。

**单页应用**
&nbsp;&nbsp;&nbsp;&nbsp;单页应用是一种网页应用，webpack 的设计和优化就是为了这种应用。
&nbsp;&nbsp;&nbsp;&nbsp;你可能会将应用分解成很多 chunks， 这些 chunks 会在路由中加载。入口 chunk 中包含了路由和一些库，但是没有其他内容。当用户只通过导航来使用应用的时候，这种方式非常好，但是对于初始页面的加载，你需要两个完整的数据来回：一个是路由数据，一个是当前的页面数据。
&nbsp;&nbsp;&nbsp;&nbsp;如果你利用 HTML5 History API 来识别 URL 中的当前页面信息，那么服务器可以根据客户端的代码来判断被请求的页面。为了将往返数据保存起来在服务器中，你可以将内容代码包含在响应中：这可以通过增加 `script` 标签来达到。浏览器将并行加载所有的 chunks。
```JavaScript
<script src="entry-chunk.js" type="text/javascript" charset="utf-8"></script>
<script src="3.chunk.js" type="text/javascript" charset="utf-8"></script>
```
&nbsp;&nbsp;&nbsp;&nbsp;可以从数据中提取 chunk 的文件名（利用 [stats-webpack-plugin ](https://www.npmjs.com/package/stats-webpack-plugin)插件可以输出创建的数据）

**多页应用**
当你在编译一个（真正的）多页应用时，你会希望不能的页面能共享公用代码。实际上利用 webpack 是非常容易实现的：只需要在编译的时候提供多个入口点：
`webpack p1=./page1 p2=./page2 p3=./page3 [name].entry-chunk.js`
```javascript
module.exports = {
    entry: {
        p1: "./page1",
        p2: "./page2",
        p3: "./page3"
    },
    output: {
        filename: "[name].entry.chunk.js"
    }
}
```
这会产生多个入口 chunk：`p1.entry.chunk.js`, `p2.entry.chunk.js` 以及 `p3.entry.chunk.js`。额外的 chunk 将会被共享。
如果你的入口 chunks 中有一些模块是一样的，那么可以使用一个很好的插件：`CommonsChunkPlugin`，它可以识别这些模块然后将它们生成一个 commons chunk。这时候就需要引用两个 `script` 标签了，一个用于引入 commons chunk，一个用于引入入口 chunk。
```javascript
var CommonsChunkPlugin = require("webpack/lib/optimize/CommonsChunkPlugin");
module.exports = {
    entry: {
        p1: "./page1",
        p2: "./page2",
        p3: "./page3"
    },
    output: {
        filename: "[name].entry.chunk.js"
    },
    plugins: [
        new CommonsChunkPlugin("commons.chunk.js")
    ]
}
```
这会产生多个入口文件：`p1.entry.chunk.js`, `p2.entry.chunk.js` 以及 `p3.entry.chunk.js`，同时还有 `commons.chunk.js`。加载的时候先加载 `commons.chunk.js` 然后再加载任一入口 chunk。
你可以通过选择不同的入口 chunk 来生成多个 commons chunk，而且也可以将这些 commons chunk 嵌套。
```javascript
var CommonsChunkPlugin = require("webpack/lib/optimize/CommonsChunkPlugin");
module.exports = {
    entry: {
        p1: "./page1",
        p2: "./page2",
        p3: "./page3",
        ap1: "./admin/page1",
        ap2: "./admin/page2"
    },
    output: {
        filename: "[name].js"
    },
    plugins: [
        new CommonsChunkPlugin("admin-commons.js", ["ap1", "ap2"]),
        new CommonsChunkPlugin("commons.js", ["p1", "p2", "admin-commons.js"])
    ]
};
// <script>s required:
// page1.html: commons.js, p1.js
// page2.html: commons.js, p2.js
// page3.html: p3.js
// admin-page1.html: commons.js, admin-commons.js, ap1.js
// admin-page2.html: commons.js, admin-commons.js, ap2.js
```
高级用法：可以在 commons chunk 内部运行代码：
```javascript
var CommonsChunkPlugin = require("webpack/lib/optimize/CommonsChunkPlugin");
module.exports = {
    entry: {
        p1: "./page1",
        p2: "./page2",
        commons: "./entry-for-the-commons-chunk"
    },
    plugins: [
        new CommonsChunkPlugin("commons", "commons.js")
    ]
};
```
更多阅读： [multiple-entry-points example](https://github.com/webpack/webpack/tree/master/examples/multiple-entry-points) 以及 [advanced multiple-commons-chunks example](https://github.com/webpack/webpack/tree/master/examples/multiple-commons-chunks)。

---

### 长期缓存
为了有效的缓存你的文件，它们应该在 URL 上有一个哈希值或者版本号。当然了，你可以手动的创建或者移动这些输出文件到一个版本号为 `v1.3` 的文件夹中。但是这么做有一些缺点：给开发者来带额外的工作，而且未更改的文件不会从缓存加载。
webpack 可以为文件的文件名加上哈希值。 那些能够产生输出文件的 Loaders（比如 worker-loader， file-loader）已经在这么做了。对于 chunk 而言，我们必须使它具有这种功能。有两种选择：
 - 为所有的 chunks 计算出一个哈希值并标记上
 - 为每一个 chunk 计算一个哈希值并标记上

下面针对这两种情况说明：
- 选择一：一次打包一个哈希值
   只需要将 `[hash]` 增加到文件名配置选项：
    `webpack ./entry output.[hash].bundle.js`
 ```javascript
 {
     output: {
         path: path.join( __dirname, "assets", "[hash]"),
         publicPath: "assets/[hash]",
         filename: "output.[hash].bundle.js",
         chunkFilename: "[id].[hash].bundle.js"
     }
 }
 ```

- 选择二：每个 chunk 一个哈希值
  只需要将 `[chunkhash]` 增加到 chunk 文件名配置选项中：
  `--output-chunk-file [chunkhash].js`
  `output: { chunkFilename: "[chunkhash].bundle.js" }`
  需要注意的是，在 HTML 文件中引用入口 chunk 的时候也需要带有哈希值。你应该会希望从数据中直接提取哈希值或者是文件名。如果你结合使用 `Hot Code Replacement`，你就只能使用第一种方式，并且不包括 `publicPath` 配置选项。

- 从数据中获取文件名
  你可能会想获取文件的最终文件名用于插入到 HTML 文件中。通过 webpack 这是可以做到的。如果你在使用 `CLI`，你可以在运行它的时候加上 `--json`，从而会输出标准的 JSON 文件。
  你也可以通过在配置表中增加一个插件，比如 [ assets-webpack-plugin](https://www.npmjs.com/package/assets-webpack-plugin) 来访问数据对象。下面是将具体的写法：
```javascript
plugins: [
  function() {
    this.plugin("done", function(stats) {
      require("fs").writeFileSync(
        path.join(__dirname, "..", "stats.json"),
        JSON.stringify(stats.toJson()));
    });
  }
]
```
 这个 JSON 数据包含了一个非常有用的特性：`assetsByChunkName`， 这是一个对象，这个对像里面的键为 chunk 的名字，键值为文件的名字。
 > 注意：如果每个 chunk 生成的是多个文件，比如一个 JavaScript 文件 一个 SourceMap， 那么这个特性就是个数组。数组中的第一个对应于 JavaScript。

---

### 编写 loader
&nbsp;&nbsp;&nbsp;&nbsp;Loader 就是输出一个函数的 node 模块。
&nbsp;&nbsp;&nbsp;&nbsp;当有资源需要被这个 loader 转化的时候，这个函数就会被调用了。
&nbsp;&nbsp;&nbsp;&nbsp;在简单的例子中，当只有一个 loader 作用在待处理资源上的时候，调用 loader 时就只有一个参数：字符串形式的资源文件的内容。
&nbsp;&nbsp;&nbsp;&nbsp;loader 可以通过在函数中的 this 格式来访问 [loader API](http://webpack.github.io/docs/loaders.html)。
&nbsp;&nbsp;&nbsp;&nbsp;一个同步的 loader 如果只想得到一个数值，那么直接用 return 返回就行了。除此之外，loader 可以通过 `this.callback(err. values...)` 函数来返回任意多的数值。错误会被传入到 `this.callback` 函数中或者被传入到同步的 loader 中。
&nbsp;&nbsp;&nbsp;&nbsp;一般来说我们都希望 loader 能够返回一到两个数据。第一个是缓存或者字符串形式的 JavaScript 代码，第二个数据是 JavaScript 对象格式的 SourceMap。
&nbsp;&nbsp;&nbsp;&nbsp;在比较附在的情况下，会组合使用到多个 loader，这时候只有最后的 loader 能够接触到源文件，同时也只有最开始的 loader 能够返回一到两个数据（JavaScript 代码及 SourceMap）（注：因为链式调用的时候是从右到左调用的）。其他的 loader 返回的数据都是传入到前一个 loader 中。

**例子**
```JavaScript
// Identity loader
module.exports = function(source) {
  return source;
};
```
```JavaScript
// Identity loader with SourceMap support
module.exports = function(source, map) {
  this.callback(null, source, map);
};
```


**提示**
    loaders 应该（按照优先级排序，第一个应该享有最高的优先级）
- 只完成单一任务
    loaders 是可以链式调用的，应该每一步都使用一个 loader 而不是让一个 loader 完成所有的事情。
    这也意味着如果不是必须的话就不应该转化成 JavaScript。
    例如：通过应用查询参数的方式从模板中渲染出 HTML：
    我们可以写一个 loader， 它可以从原文件中编译模板，然后执行它并返回一个能够输出带有 HTML 代码的字符串的模块。但这种做法不推荐。
    我们应该为每一个任务写一个 loader，然后链式调用它们：
    - jade-loader：将模板转化成一个能返回函数的模块
    - apply-loader：接收一个函数并通过应用查询参数返回原生结果
    - html-loader： 接收 HTML 并且输出字符串


- 生成的模块应该是模块化的
    通过 loader 生产的模块应该遵循和普通模块一样的设计原则。
    例如：这是一个不好的设计：（没有模块化，全局声明……）
    ```javascript
        require("any-template-language-loader!./xyz.atl");
        var html = anyTemplateLanguage.render("xyz");
    ```


- 尽量标明是可缓存的
    大部分的 loader 都是可缓存的，所以它们应该也标明是可缓存的。
    只需要在 loader 中调用 `cacheable`：
    ```javascript
        // Cacheable identity loader
        module.exports = function(source) {
            this.cacheable();
            return source;
        };
    ```


- 注明依赖
    如果 loader 需要利用外部资源（比如需要读取文档系统），那么就 **必须** 要注明。这个信息可以用来使可缓存的 loader 无效，也会使得在监控模式下重编译。
    ```javascript
        // Loader adding a header
        var path = require("path");
        module.exports = function(source) {
            this.cacheable();
            var callback = this.async();
            var headerPath = path.resolve("header.js");
            this.addDependency(headerPath);
            fs.readFile(headerPath, "utf-8", function(err, header) {
                if(err) return callback(err);
                callback(null, header + "\n" + source);
            });
        };
    ```

- 分解依赖
    在很多语言中都有规范依赖的方法，比如在 css 中有 `@import` 以及 `url(...)` 的方式。模块系统应该能够分解这些依赖。
    有两种选择可达到这种目的：
     - 将它们转化成 `require`
     - 利用 `this.resolve()` 函数来分解路径
         举例一：css-loader。 css-loader 将依赖转化成 `require`，具体方式是利用 `require` 样式（也会被 css-loader 处理）来替代 `@import`，同时也利用 `require` 相关文件来替代 `url(...)` 引用。
           如果这个语言只接受相对路径（比如在 css 中： `url(file)` 一般表示 `./file`），那么就可以通过 `~` 符号来将特定的引用传送给模块，如下所示：
    ```javascript
        url(file) -> require("./file")
        url(~module) -> require("module")
    ```

- 提取公用代码
    不要在利用同一个 loader 处理的每个模块中提取太多公用代码。在 loader 中创建一个（运行环境下的）文件，并利用一个 `require` 来引用公用代码。

- 不要内嵌绝对路径
    不要将绝对路径写入到模块代码中，因为如果项目移动位置的话会破坏路径的哈希值。在[loader-utils](https://github.com/webpack/loader-utils#stringifyrequest) 中有一个 `stringifyRequest` 方法，可以将绝对路径转化为相对路径。
    ```javascript
        var loaderUtils = require("loader-utils");
        return "var runtime = require(" +
        loaderUtils.stringifyRequest(this, "!" + require.resolve("module/runtime")) +
        ");";
    ```

- 使用库作为 `peerDependencies`
    当使用库作为同级依赖的时候，如果需要，应用的开发者可以在配置文件 `package.json` 中明确的指出所依赖库的版本。这种依赖应该在不需要重新发布新版本号的 loader 的情况下能升级。
    ```javascript
        "peerDependencies": {
            "libraay": "^1.3.5"
        }
    ```

- 更多关于 [loaders](http://webpack.github.io/docs/loaders.html).

---

## 总结
&nbsp;&nbsp;&nbsp;&nbsp;webpack 文档也看了好几天了，上面翻译的也只是其中一部分内容，看到后面有点不知所云，翻译起来很吃力，有种以其昏昏使人昭昭的感觉。为了不误人子弟，所以决定暂时不再翻译，日后有了更多的理解了再来继续。
&nbsp;&nbsp;&nbsp;&nbsp;如果在阅读的过程中发现翻译不妥，欢迎在下方留言或者给我发邮件。
