{{#template name="react-step03"}}

# 将任务存储到集合当中

{{> step03CollectionsIntro tutorialName="simple-todos-react"}}

### 在React组件当中使用集合的数据

在React组件当中使用Meteor集合的数据, 我们可以使用一个 Atmosphere 包 `react-meteor-data` 它允许我们创建一个“数据容器”让Meteor的相应数据填充到React组件层当中。

我们需要利用NPM安装它，`react-addons-pure-render-mixin`：

```bash
meteor npm install --save react-addons-pure-render-mixin
meteor add react-meteor-data
```

为了使用`react-meteor-data`,我们需要将我们的组件包含在更高级别的`createContainer`容器当中：

{{> DiffBox step="3.4" tutorialName="simple-todos-react"}}

包含`App`组件的容器从`Tasks`集合里面读取任务数据并且将数据提供给下层`App`组件作为任务'传递'。这就是为什么当数据库发生变化，`App`马上就可以渲染变化。

当你改变这些代码的时候，你将注意到任务列表没有显示任何内容，因为我们的数据库是空的；我们需要插入一些任务！

{{> step03InsertingTasksFromConsole}}

{{/template}}
