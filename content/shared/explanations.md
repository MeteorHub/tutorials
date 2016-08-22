{{#template name="step03CollectionsIntro"}}

集合是Meteor坚持使用的数据存储方式。在meteor当中关于集合比较特别的一点是他们可以在服务端和客户端同时通信，这让编写视觉逻辑层变得更加容易不需要在服务端添加任何代码。他们也可以自动更新，因此视图组件会从集合当中自动更新最新的数据。

你可以阅读这篇文章了解更多关于集合的内容 [Collections article](http://guide.meteor.com/collections.html) 。

创建一个新的集合和使用javascript调用 `MyCollection = new Mongo.Collection("my-collection");`一样简单。在服务端，设置一个叫做的mongodb集合`my-collection`；在客户端，创建一个链接服务端集合的缓存。我们将在12节当中学习更多关于客户端/服务端分开的内容，但是现在我们可以嘉定进入数据库的端口在服务端来编写我们的代码。

创建一个集合，我们定义一个新的模块`tasks`用来创建mongo集合和导入它：

{{> DiffBox tutorialName=tutorialName step="3.1"}}

注意我们将这些文件放在了 `imports/api`新目录当中。 这是一个存储你的应用API非常好的地方，我们使用的集合API就放这里，然后存储从他们读取和写入Publications 以及写入他们的方法。 你可以阅读这篇文章了解如何组织你的代码 [Application Structure article](http://guide.meteor.com/structure.html) 。

我们需要导入服务端的模块（创建mongodb集合和设置钩子让数据到达客户端）：

{{> DiffBox tutorialName=tutorialName step="3.2"}}

{{/template}}

{{#template name="step03InsertingTasksFromConsole"}}

### 从服务端数据库控制台插入任务

集合中的项目叫做 _documents_. 让我们使用服务端数据库控制台插入一些文档。打开一个新的terminal，到你的APP根目录输入：

```bash
meteor mongo
```

这将为你APP的本地数据库开启一个控制台，在提示符的后面输入：

```js
db.tasks.insert({ text: "Hello world!", createdAt: new Date() });
```

在你的浏览器当中，你讲看到APP的UI发生了变化，更新显示出了新的任务。你可以看到我们不必在后台填写任何连接服务端数据库的代码 &mdash; 它自动就创建好了。

从数据库控制台插入更多不同内容的任务。在下一节，我们将看到如何不使用数据库控制台通过UI界面添加任务。

{{/template}}

{{#template name="step09OptimisticUI"}}

### optimistic UI

为什么我们想要在客户端和服务端定义方法？我们做这些事为了调用一个特性叫做  _optimistic UI_.

当你使用`Meteor.call`在客户端上调用一个方法的时候，有两件事情同时发生：

1. 客户端给服务端发送一个请求在安全的环境当中运行一个方法，就好像一个ajax请求一样工作。
2. 一个在客户端上运行的模拟的方法，试途使用可用的信息来预测服务端调用的结果。

这意味着，一个新创建的任务会在从服务端做出响应之前就显示出来。

如果结果从服务端放，并且在服务端仿真组合对比，确定的数据会保留下来。如果服务器结果和客户端结果不一样，UI就会使用服务端发来的信息。


你可以阅读更多关于方法和optimistic UI在这篇文章 [Methods article](http://guide.meteor.com/methods.html)和[blog post about optimistic UI](http://info.meteor.com/blog/optimistic-ui-with-meteor-latency-compensation).

{{/template}}
