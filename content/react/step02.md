{{#template name="react-step02"}}
# 使用React组件定义视图

在开始使用React作为我们的视图之前，让我们添加一些运行React的NPM包。

在你的运行当中的app的目录下，打开一个新的terminal，输入：

```sh
meteor npm install --save react react-dom
```

### 更换启动代码

开始之前，让我们替换默认的APP代码，然后我们将讨论它。

首先， 替换初始的HTML内容：

{{> DiffBox tutorialName="simple-todos-react" step="2.2"}}

然后， **删除 `client/main.js`**并且创建三个新文件：

{{> DiffBox tutorialName="simple-todos-react" step="2.3"}}

{{> DiffBox tutorialName="simple-todos-react" step="2.4"}}

{{> DiffBox tutorialName="simple-todos-react" step="2.5"}}

*==（代码报错注意模块导入路径问题）==*

我们刚刚添加了三个东西到我们的APP当中 ：

1. 一个 `App` React 组件
2. 一个 `Task` React 组件
3. 一些初始化代码 (在我们的 `client/main.js` JavaScript客户端入口文件),当页面载入被读取的时候通过`Meteor.startup`的调用，程序知道如何去调用代码。这个代码载入其他的组件并渲染将他们提交到`#render-target`html元素

你可以在Meteor引导中[Application Structure article](http://guide.meteor.com/structure.html)阅读更多关于如何导入工作组以及如何组织你的代码的内容。

在教程的最后，当你需要添加或者改变代码的时候我们将会提供这些组件。


### 检查结果

在我们的浏览器当中, APP看起来应该像下面这样：

> #### Todo List
> - This is task 1
> - This is task 2
> - This is task 3

如果你的APP看起来不是这样，查看每一段代码右上角的github链接去查看完整文件，并且确保你的代码和例子是一样的。

### HTML文件定义静态内容

Meteor 会解析所有的在APP文件夹当中的HTML文件并且识别三个顶级标签： **&lt;head>**, **&lt;body>**, and **&lt;template>**.

每一个包含在 &lt;head>中的标签会被添加到HTML的`head`区域发送到客户端，每一个在 &lt;body> 中的标签会被添加到`body`区域，就像常规的HTML文件一样。

每一个包含在 &lt;template> 中的标签会被编译到Meteor _模板_ 当中, 它可以使用HTML的 `{{dstache}}> templateName}}` 嵌入或者你可以参考JavaScript的 `Template.templateName`。 在本教程当中, 我们不会使用Meteor的视图模板功能因为我们将使用React去构建我们的视图组件。

### 使用React定义视图组件

在React当中, 视图组件是`React.Component`的子类 (通过`import { Component } from 'react';`导入的)。 你的组件可以有任何你喜欢的方法, 但是有一些方法比如`render`需要特殊的函数 。 组件也可以从他们的父级组件哪里接受数据，通过`props`属性。在本教程当中我们将浏览更多React的特性。你也可以查看他们在[Facebook's React tutorial](https://facebook.github.io/react/docs/tutorial.html)。

### 使用JSX返回标记和渲染方法

在每一个React component当中最重要的方法是`render()`，React用这个方法来描述如何渲染HTML组件以及他们应该如何显示。HTML内容被javascript的扩展来书写的方法叫做JSX，它类似于一种将html写在javascript当中的感觉。你可以在其中看到一些明显的不同；在JSX你使用`className`属性代替`class`。关于JSX很重要的事情是，它不是像Spacebars或者 Angular一样是模板语言-它实际上是直接编译成了常规的javascript。
阅读更多关于JSX [in the React docs.](https://facebook.github.io/react/docs/jsx-in-depth.html)。

JSX被`ecmascript`支持的范围广泛的包，它包含在所有新的Meteor的默认应用当中。

{{> DiffBox tutorialName="simple-todos-react" step="2.6"}}

在我们继续之前，让我们通过添加css使我们的app看起来比较好看。
虽然这个教程专注于html和javascript，所以仅仅复制下面的css到`main.css`当中。这是本教程需要的所有CSS代码。没有CSS，APP依然可以正常工作，不过如果你添加了它会看起来更好一些。

{{/template}}
