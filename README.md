# 官方Meteor教程

这个repo当中包含了离线的Meteor教程的内容和视图代码[meteor.com](https://www.meteor.com/tutorials/blaze/creating-an-app)。

请随意提交pull request来提升我们的内容！

### 教程内容

1. [Blaze tutorial](https://www.meteor.com/tutorials/blaze/creating-an-app): [`/content/blaze`](https://github.com/meteor/tutorials/tree/master/content/blaze)
2. [Angular tutorial](https://www.meteor.com/tutorials/angular/creating-an-app): [`/content/angular`](https://github.com/meteor/tutorials/tree/master/content/angular)
3. [React tutorial](https://www.meteor.com/tutorials/react/creating-an-app): [`/content/react`](https://github.com/meteor/tutorials/tree/master/content/react)

### 一步一步跟我学教程repos

我们也在这里维护所有的一步一步跟我学的教程

1. [Blaze](https://github.com/meteor/simple-todos)
2. [Angular](https://github.com/meteor/simple-todos-angular)
3. [React](https://github.com/meteor/simple-todos-react)

### 教程查看器

如果你正在编辑这些教程，使用这个简单的应用去查看他们：https://github.com/meteor/tutorial-viewer

## 教程工作流程

### 编辑文字

只在`/content/`当中编辑markdown文件。

### 编辑代码片段

代码片段是从一步一步跟我学的git repos当中的`/repos`生成的。每一个代码片段都是自己提交的。提交的信息遵循以下的形式：

```
Step 3.1: Add some feature
```

你可能还需要确保你的所有文件以换行符结尾，这样你就不会因为“文件末尾没换行”的差异而纠结。

使用 `git rebase -i --root` 去整合repo达到你期望的状态，运行脚本更新程序文件：

```sh
./scripts/process-repo.rb blaze
```

提交这个信息可以使用下面代码片段当中包含的内容：

```html
{{> DiffBox step="3.1" tutorialName="simple-todos"}}
```

你应该用正确的教程名字来替换 `simple-todos`  (通过调用 `DiffBox.registerTutorial`定义)。

你完成的时候要确保所有生成的文件都更改。

## repository 布局

这个 repository 是一个Meteor包；目前还没有公布，但是你可以clone它并在作为本地应用来使用它。

这个repository的不同部分有十分不同的作用，但是他们是紧耦合的，分成单独的包没有意义。

3. `/content/` 教程内容，markdown格式的。
4. `/generated/` (不要手动编辑)这个目录的内容是从一步一步跟我的repos当中生成的git补丁文件。
5. `/repos/` 这个目录包含所有三个一步一步跟我学的git子模块的repos。
7. `/scripts/` 这个包含一个用来从`/repos/`的源更新`/generated/`的脚本。
