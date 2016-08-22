{{#template name="sharedStep11"}}

# 测试

现在我们已经为我们的应用添加了一些功能，让我们添加一个测试确保我们不用推到重来并且应用可以像我们所期望的那样运行。

我们将写一个测试执行我们的一个方法（这个方法是我们的APP的API当中的）并且验证它可以正常运行。

为了实现这个，我们将添加一个 [test driver](http://guide.meteor.com/testing.html#test-driver) 作为 [Mocha](https://mochajs.org) JavaScript的测试框架：

```bash
meteor add practicalmeteor:mocha
```

我们现在可以在“测试模型”当中通过调用特殊的命令运行我们的app并且指定使用驱动(你将需要停止正常运行的应用，否则使用 `--port XYZ` 命令指定一个新的端口。

```bash
meteor test --driver-package practicalmeteor:mocha
```

如果你这么做，在你的浏览器窗口当中你应该可以看到一个空白的测试结果。

让我们添加一些简单的测试（这里还什么也没做）：

{{> DiffBox tutorialName="simple-todos" step="11.2"}}

在任何测试当中我们都应该确保数据如我们期望的那样在一个稳定的状态当中。我们会使用Mocha's `beforeEach` 架构去测试：

{{> DiffBox tutorialName="simple-todos" step="11.3"}}

这里我们创建了一个单独的任务，它关联到的是一个随机的，和之前测试都不同的 `userId`。

现在我们写一个测试区调用`task.remove`方法验证用户删除操作：

{{> DiffBox tutorialName="simple-todos" step="11.4"}}

如果你想在Meteor测试当中做更多事！你可以阅读这篇文章了解更多。 [article on testing](http://guide.meteor.com/testing.html).

{{/template}}
