{{#template name="react-step07"}}

# 在组件状态中存储临时的UI数据

在这一步，我们给我们的APP添加一个客户端数据过滤功能，以便用户可以检查的时候只看到未完成的任务。我们将会学习如何使用React的组件状态去存储仅在客户端上使用的临时信息。

首先，我们需要给我们的`App`组件添加一个checkbox：

{{> DiffBox step="7.1" tutorialName="simple-todos-react"}}

你可以看到它读取 `this.state.hideCompleted`。React组件有一个特殊的字段叫做`state`，你可以通过他存储封装的组件数据。在组件的构造函数中，我们需要去初始化`this.state.hideCompleted`的值。

{{> DiffBox step="7.2" tutorialName="simple-todos-react"}}

我们可以通过调用`this.setState`来更新`this.state`， 它将异步更新数据然后让组件重新渲染：

{{> DiffBox step="7.3" tutorialName="simple-todos-react"}}

现在，当`this.state.hideCompleted`是true的时候我们需要更新我们的`renderTasks`函数去过滤我们完成的任务：

{{> DiffBox step="7.4" tutorialName="simple-todos-react"}}

现在如果你点击方框，任务列表将显示给你尚未完成的任务。

### 加一个功能：显示未完成任务数量

现在我们已经写了一个过滤出已完成的任务的查询，我们可以使用相同的查询方式显示未完成的任务数量。为了实现这个我们需要在我们的数据容器里抓取这个数值并且在`rander`方法中添加一行。因为我们在客户端的Minimongo当中拥有了数据，所以扩展这个计数不需要与服务端通信。

{{> DiffBox step="7.5" tutorialName="simple-todos-react"}}

{{> DiffBox step="7.6" tutorialName="simple-todos-react"}}

{{/template}}
