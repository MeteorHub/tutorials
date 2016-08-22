{{#template name="react-step10"}}

# 发布和订阅的数据过滤

现在，我们已经移除了我们应用当中所有的敏感代码，我们需要学习其他关于meteor安全的事情。直到现在，我们假设客户端可以操作整个数据库，这意味着如果我们调用 `Tasks.find()` 我们将会得到集合当中的所有任务。如果用户想要存储自己的私人数据这样就行不通了。我们需要一个方法控制数据库有选择性的给客户端传输数据。

就好像上一节使用`insecure`一样，所有的新的Meteor应用创建的时候都会有`autopublish` 包,它会给客户端自动同步所有的数据。让我们移除它看看会发生什么：

```bash
meteor remove autopublish
```

当应用刷新的时候，任务列表就空了。没有了 `autopublish` 包，我们必须明确的制定服务端那些内容发送给客户端。在Meteor当中`Meteor.publish` 和 `Meteor.subscribe`可以实现这项功能。
 
首先让我们为所有的任务添加publication：

{{> DiffBox step="10.2" tutorialName="simple-todos-react"}}

然后当`App`组件被创建的时候让我们订阅他们：

{{> DiffBox step="10.3" tutorialName="simple-todos-react"}}

只要你添加上这些代码，所有的任务都会重新显示出来。

在服务器上调用 `Meteor.publish` 注册一个名字叫做`task`的 _publication_ 。当`Meteor.subscribe` 在客户端上被publication的名字调用的时候，客户端会 _subscribes_ 所有的 publication，它会显示出这个例子数据库当中所有的任务。想了解 publish/subscribe 模块的真正功能， 让我们添加一个功能，允许用户将任务标记成私人任务，这样其他用户就无法看到他的私人任务了。

### 添加一个任务私有化按钮

让我们添加任务添加另外一个功能叫“私有化”可以让用户将任务私有化。这个按钮仅仅显示在拥有者拥有的任务前。我们希望表单可以显示正确的状态：共有的或者是私有的。

首先我们需要添加一个新的方法让我们可以设置任务的私有化状态：

{{> DiffBox step="10.4" tutorialName="simple-todos-react"}} 

现在我们需要给任务添加一个新的属性去决定我们是否想要显示私有化按钮；按钮应该仅仅显示在登录的用户的任务的旁边：

{{> DiffBox step="10.5" tutorialName="simple-todos-react"}}

{{> DiffBox step="10.6" tutorialName="simple-todos-react"}}

让我们添加一个按钮，使用这个新属性去决定是否应该被显示：

{{> DiffBox step="10.7" tutorialName="simple-todos-react"}}

我们需要定义一个按钮触发事件：

{{> DiffBox step="10.8" tutorialName="simple-todos-react"}}

最后一件事情，让我们更新<li>元素当中的`Task` 组件去响应私有化状态。我们将会使用 `classnames` NPM包 :

```bash
meteor npm install --save classnames
```

然后我们会使用这个包去选择一个基于任务的类渲染：

{{> DiffBox step="10.10" tutorialName="simple-todos-react"}}

### 基于私有化状态有选择的发布任务

现在我们有了一个设置任务私有化的方法，我们应该修改我们的共有函数仅仅任务发送给有权限的用户去看：

{{> DiffBox step="10.11" tutorialName="simple-todos-react"}}

为了测试功能是否正常，你可以使用浏览器的隐秘浏览模式用不同的用户登录。将两个窗口并列排放，并且将任务标记私有化，通过这种方法来确认其他用户无法看见。现在再把任务公开，任务就会再次显示！

### 额外的安全方法

为了完善我们的私有化任务的功能，我们需要给`deleteTask` 和 `setChecked` 方法检查机制确保只有任务拥有者菜可以删除或者完成一个私有化任务：

{{> DiffBox step="10.12" tutorialName="simple-todos-react"}}

> 注意以上的代码可以让任何人删除公有的任务。添加一些小的修改，你应该可以只能由任务拥有者删除任务。

我们完成了我们的私有化任务功能！现在我们的APP是安全的了，攻击者不可以修改和删除其他人私有化的任务了。

{{/template}}
