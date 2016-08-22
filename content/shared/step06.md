{{#template name="sharedStep06"}}

# 在Android 或者 iOS 上运行你的APP

> 现在，Meteor不支持在windows上构建移动应用。如果你在windows上使用Meteor，你可以跳过这一节。

到目前为止，我们已经构建了我们的应用并且在浏览器当中测试了他，但是Meteor是跨平台的框架，只需要几行命令你的简单的todo列表网站可以变成一个iOS 和 Android 应用。

Meteor让构建移动应用变得非常简单，但是下载所有的程序需要一段时间——android大约要300MB以及IOS你需要安装xcode大概2GB。如果你不想等待下载可以自由跳过到下一步。

{{#if specialContent}}
  {{> Template.dynamic template=specialContent}}
{{/if}}

### 在iOS虚拟机上运行（仅限mac）

如果你有一台mac电脑，你可以在iOS虚拟机当中运行你的应用。

进入你的应用文件夹并且输入：

```bash
meteor install-sdk ios
```

这将安装一些用来构建iOS应用必要的文件。当你完成的时候，输入：

```bash
meteor add-platform ios
meteor run ios
```

你讲看到iOS虚拟机弹出并且你的应用就运行在里面。

### 在android虚拟机上运行

在terminal当中,进入到你的APP的文件夹并且输入：

```bash
meteor install-sdk android
```

这将帮助你安装构建android应用的必要工具。当你完成的时候，输入：

```bash
meteor add-platform android
```

然后同意许可项目，输入：

```bash
meteor run android
```

在初始化之后，你将看到android虚拟机弹出，并且你的应用运行在其中。这个虚拟机运行可能会慢一些，如果你想看到你的app到底怎么样，你应该让他运行在你的真实的设备上。

### 在android设备上运行

首先，在你的操作系统上完成所有设置android工具的步骤。然后确保你有 [USB Debugging enabled on your phone](http://developer.android.com/tools/device.html#developer-device-options) 并且你的手机通过usb插在电脑上。在你在设备上运行的时候你应该退出你的android虚拟机。

然后，运行下面的命令：

```bash
meteor run android-device
```

应用将在你的设备上安装。

### 在iPhone 或者 iPad 上运行 (仅限mac;需要苹果开发者账号)

如果你有一个苹果开发者账号，你也可以让你的app运行在iOS设备上。执行下面的命令：

```bash
meteor run ios-device
```

这将启动Xcode并打开一个iOS应用项目。你可以使用Xcode然后将app发送到任何设备上或者Xcode支持的虚拟机上。

现在我们看到了构建一个移动应用是如此的简单，让我们来添加更多新特性。

{{/template}}
