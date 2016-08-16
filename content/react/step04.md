{{#template name="react-step04"}}

# 使用表单添加数据

在本章节，我们将添加一个输入框让用户将任务添加到列表当中。

首先，让我们我们为我们的`App`组件添加一个表单：

{{> DiffBox step="4.1" tutorialName="simple-todos-react"}}

> Tip: 你可通过`{/* ... */}`符号向你的JSX代码里添加注释。

你可以看到`form`元素有一个`onSubmit`属性提供了一个方法在组件当中叫做`handleSubmit`。In React, this is how you listen to browser events, like the submit event on the form. `input` 元素有一个 `ref` 属性在后面它会让我们更容易的区访问这个元素。

让我们添加一个 `handleSubmit` 方法到我们的 `App` 组件当中：

{{> DiffBox step="4.2" tutorialName="simple-todos-react"}}

现在你的APP已经有了一个新的输入框。 只需要在输入框输入文字并点击回车就可以添加任务。如果你打开了一个新的浏览器窗口，你需要重新打开APP， 你将会看到列表在所有的客户端之间同步更新了。

### 在React中监听事件

如你所见, 在React当中你通过直接引用组件上的方法操作DOM事件。在事件处理程序当中,你可以通过给它们一个`ref`属性和使用`ReactDOM.findDOMNode`来从组件中引用元素。 如果想了解更多React支持的事件和如何让事件系统的工作，请在这个文档当中查看 [React docs](https://facebook.github.io/react/docs/events.html)。

### 插入一个集合

在事件处理程序当中, 我们通过调用`Tasks.insert()`来向`tasks`集合插入一个任务。我们可以指派任何一个属性到任务对象上,比如创建时间，这样我们甚至都不需要定义集合的架构。

可以从客户端插入任何数据到数据库是非常不安全的，但是目前还可以。在第十节里我们将学习如何让我们的的APP更安全和如何约束限制数据插入到数据库当中。 

### 任务分类

目前，我们的代码将所有的新任务显示在了列表的底端。作为任务列表那不是非常好，因为我们想第一时间看到最新的任务。 

我们可以通过使用`createdAt`分类结果来解决这个问题，它是由我们的新代码自动添加的。仅仅添加一个分类选项给`find`去调用数据容器内部封装的`App`组件：

{{> DiffBox step="4.3" tutorialName="simple-todos-react"}}

让我们回到浏览器查看确保它工作了：任何你添加的新任务都应该显示在列表的顶部而不是在底部。

在下一节，我们将会添加一些非常重要的todo列表的功能：完成任务和删除任务。
{{/template}}
