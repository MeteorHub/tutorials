{{#template name="react-step09"}}

# 安全使用方法

在本节开始之前，APP的用户可以随意操作数据库。对于小范围内部使用或者一个demos来说无所谓，但是任何一款真正的应用都需要去控制数据权限。在Meteor当中，控制数据权限最好的方式是声明 _methods_。代替客户端的代码直接调用 `insert`， `update`， 和 `remove`，这将调用一个方法，检查用户是否有权限来完成操作，然后再执行用户对数据库的操作。

### 移除 `insecure`

创建每一个新的meteor项目的时候都会被默认创建一个`insecure`包。这个包允许我们在客户端上编辑数据库。在原型阶段它是非常有用的，但是现在我们要关掉这个辅助功能。为了移除这个包，需要进入APP根目录然后执行：

```bash
meteor remove insecure
```

如果你在移除这个包之后尝试使用APP，你会发现任何输入操作和按钮都不可用了。这是因为，所有的客户端操作数据库的权限都被取消了。现在我们需要重写APP的一些部分。

### 定义方法

首先，我们需要去定义一些方法。我们需要一个可以在客户端上执行每个数据库操作的方法。这些方法应该在客户端和服务端执行的代码当中定义，我们将会在后面的章节——_Optimistic UI_ 当中讨论这一点。

{{> DiffBox step="9.2" tutorialName="simple-todos-react"}}

现在我们已经定义了我们的方法，我们需要Now that we have defined our methods, 我们需要更新我们在操作集合的地方使用的方法：

{{> DiffBox step="9.3" tutorialName="simple-todos-react"}}

{{> DiffBox step="9.4" tutorialName="simple-todos-react"}}

现在，我们所有的输入操作和按钮都将再次可以使用了。Now all of our inputs and buttons will start working again. 刚才所有的工作当中我们都添加了什么？

1. 当我们向数据库插入数据的时候，我们可以验证用户登陆， `createdAt` 字段是否正确`owner` and `username` 是否正确，确保用户不是其他人。

2. 当用户可以创建私有任务的时候我们可以在后面给`setChecked` and `deleteTask`添加额外的确认逻辑。

3. 现在我们的客户端代码逐渐的与数据库逻辑分离。而不再是使用我们的事件处理程序去操作，现在我们拥有这套方法可以在任何地方调用数据库。

{{> step09OptimisticUI}}

{{/template}}
