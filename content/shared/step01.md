{{#template name="sharedStep01"}}

# 创建你的第一个应用

在本教程当中, 我们将要创建一个简单的应用去管理“todo”列表并且可以和他人协作。

创建一个APP,打开你的terminal输入：

```bash
meteor create simple-todos
```

这将创建一个叫做“simple-todos”的文件夹包含所有meteor应用需要的文件：

```bash
client/main.js        # 客户端的JavaScript入口文件
client/main.html      # 定义视图模板的HTML文件
client/main.css       # 定义你的应用的css样式的CSS文件
server/main.js        # 服务端的JavaScript入口文件
package.json          # NPM安装包管理文件
.meteor               # Meteor内部文件
.gitignore            # 控制git的文件
```

运行刚刚创建的APP：

```bash
cd simple-todos
meteor npm install
meteor
```

打开你的浏览器然后访问`http://localhost:3000`查看运行的APP

在我们继续之前你可以游览一下这个默认的APP。举个例子，你可以用你最喜欢的编辑器尝试编辑`client/main.html`文件当中`<h1>`的文本。当你保存文件的时候，你的浏览器就会自动更新你更改的新内容。我们管这个叫“hot code push”（实时预览）。

### ES2015 JavaScript 特性

ES2015的新特性贯穿在最初的app代码和整个教程当中，如果你还没有尝试下一代javascript新特性，你将会对他们感到陌生。这是因为Meteor默认需要很多ES2015的特性支持。这些特性包括：


1. 数组函数: `(arg) => {return result;}`
2. 简写方法: `render() { ... }`
3. `const` 和 `let` 代替 `var`

在[ecmascript docs](http://example.net/) 中阅读关于Meteor支持的特性。获取更多关于ECMAScript2015的信息，可以看一下下面的文章：

* [Luke Hoban's "ES6 features"](http://git.io/es6features)

* [Kyle Simpson's "You don't know JS: ES6 and beyond"](https://github.com/getify/You-Dont-Know-JS/tree/master/es6%20%26%20beyond)

* [Nikolas C. Zakas "Understanding ECMAScript 6"](https://github.com/nzakas/understandinges6)

现在你已经体验了如何编辑你的Meteor app的文件，让我开始制作一个简单的todo list 应用。如果你在教程当中发现BUG或者错误，请提交到 [GitHub](https://github.com/meteor/tutorials).
{{/template}}
