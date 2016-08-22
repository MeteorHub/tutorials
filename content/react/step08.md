{{#template name="react-step08"}}

# 添加用户账户

Meteor自带一个用户系统和一个常规的用户登录界面让你可以在短时间内给APP添加多用户功能。

> 现在,这个UI组件使用Blaze，是Meteor的默认的UI引擎。未来，这里也许也会是React组件。

为了应用这个用户系统和UI，我们需要添加一个关联的包。在你的APP根目录下，运行下面的命令：

```bash
meteor add accounts-ui accounts-password
```

### 在React中封装一个Blaze组件

引用`accounts-ui`包中的Blaze UI组件，我们需要把它分装到React组件当中。让我创建一个名字为`AccountsUIWrapper`的新组件：

{{> DiffBox step="8.2" tutorialName="simple-todos-react"}}

我们只需要在APP中定义它就可以引用组件：

{{> DiffBox step="8.3" tutorialName="simple-todos-react"}}

然后，添加下列代码去配置用户UI，让用户名代替email地址：

{{> DiffBox step="8.4" tutorialName="simple-todos-react"}}

我们也需要将配置代码引入到我们的客户端：

{{> DiffBox step="8.5" tutorialName="simple-todos-react"}}

### 添加和用户相关的功能

现在用户可以创建账号以及登录你的APP！这是非常棒的，但是登入和登出还不是很好用，让我们添加两个功能：

1. 只给登录用户显示创建任务的输入框
2. 显示任务是由谁创建的

为了实现这些功能，我们需要给`tasks`集合添加两个字段：

1. `owner` - the `_id` of the user that created the task.
2. `username` - the `username` of the user that created the task. We will save the username directly in the task object so that we don't have to look up the user every time we display the task.

首选，让我添加一些代码用来将这些字段内容保存到`handleSubmit`事件：

{{> DiffBox step="8.6" tutorialName="simple-todos-react"}}

修改数据容器获得当前登录用户的信息：

{{> DiffBox step="8.7" tutorialName="simple-todos-react"}}

然后，在我们的渲染方法当中，添加一个条件约束，当用户登录的时候只显示表格：

{{> DiffBox step="8.8" tutorialName="simple-todos-react"}}

最后，添加一个功能，在每一个任务文本之前显示`username`：

{{> DiffBox step="8.9" tutorialName="simple-todos-react"}}

在你的浏览器当中，添加一些任务，注意你的用户名会显示出来，我们之前添加的任务不会显示用户名；你可以把他们都删除了。

现在，用户可以登录并且我们可以追踪每一个任务属于那个用户。现在让我看一下这些概念中的细节。

### 自动用户界面

如果我们的APP有 `accounts-ui` 包， 我们必须添加一个登陆下拉框，渲染内部UI组件。这个下拉登陆检测登陆方法已经被添加到APP当中并会显示一些控制。在我们的案例当中，我们用到的登录方法是 `accounts-password` ，因此下拉框显示一个密码输入框。如果你想探索一下，你可以添加一个`accounts-facebook` 包，这可以让你的APP支持facebook登录。facebook的登录按钮会自动显示在下拉框里。

### 获得关于登录用户的信息

在你的数据容器当中，你可以使用`Meteor.user()` 去检查用户是否登录，并且获得他们的信息。举个例子，`Meteor.user().username` 包含了用户的用户名。你也可以使用`Meteor.userId()`获得当前用户的ID。

在下一节当中，我们将学习如何让我们的APP通过在服务器上进行数据验证，让数据更安全。
{{/template}}
