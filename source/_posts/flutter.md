---
title: flutter介绍
date: 2021-12-14 16:11:27
tags: ""
image: "./image/flutter-mobile-web-desktop.jpg"
---


## 原生开发

原生应用程序是指某一个移动平台（比如iOS或安卓）所特有的应用，使用相应平台支持的开发工具和语言，并直接调用系统提供的SDK API。比如Android原生应用就是指使用Java或Kotlin语言直接调用Android SDK开发的应用程序；而iOS原生应用就是指通过Objective-C或Swift语言直接调用iOS SDK开发的应用程序。原生开发有以下
主要优势：

- 可访问平台全部功能（GPS、摄像头）
- 速度快、性能高、可以实现复杂动画及绘制，整体用户体验好

<br/>

主要缺点：
- 平台特定，开发成本高；不同平台必须维护不同代码，人力成本随之变大
- 内容固定，动态化弱，大多数情况下，有新功能更新时只能发版

## 跨平台技术简介

针对原生开发面临问题，业界一直都在努力寻找好的解决方案，而时至今日，已经有很多跨平台框架

- H5 + 原生（Cordova、Ionic、微信小程序）
- JavaScript 开发 + 原生渲染 （React Native、Weex）
- 自绘UI + 原生 (Qt for mobile、Flutter)

 ### Flutter 简介

 Flutter 是 Google 推出并开源的移动应用开发框架，主打跨平台、高保真、高性能。开发者可以通过 Dart 语言开发 App，一套代码同时运行在 iOS 和 Android平台。 Flutter 提供了丰富的组件、接口，开发者可以很快地为 Flutter 添加 Native 扩展

 - ### 是什么

 Flutter是由原 Google Chrome 团队成员，利用 Chrome 2D 渲染引擎，然后精简 CSS 布局演变而来

 ![](/image/whatisflutter.awebp)

 - ### 跨平台自绘引擎

 Flutter 与用于构建移动应用程序的其它大多数框架不同，因为 Flutter 既不使用 WebView，也不使用操作系统的原生控件。 相反，Flutter 使用自己的高性能渲染引擎来绘制 Widget（组件）。这样不仅可以保证在 Android 和iOS 上 UI 的一致性，也可以避免对原生控件依赖而带来的限制及高昂的维护成本。

Flutter 底层使用 Skia 作为其 2D 渲染引擎，Skia 是 Google的一个 2D 图形处理函数库，包含字型、坐标转换，以及点阵图，它们都有高效能且简洁的表现。Skia 是跨平台的，并提供了非常友好的 API，目前 Google Chrome浏览器和 Android 均采用 Skia 作为其 2D 绘图引擎。

目前 Flutter 已经支持 iOS、Android、Web、Windows、macOS、Linux、Fuchsia（Google新的自研操作系统）等众多平台，但本书的示例和介绍主要是基于 iOS 和 Android 平台的，其它平台读者可以自行了解。

 - ### 高性能

Flutter 高性能主要靠两点来保证：

第一：Flutter APP 采用 Dart 语言开发。Dart 在 JIT（即时编译）模式下，执行速度与 JavaScript 基本持平。但是 Dart 支持 AOT，当以 AOT模式运行时，JavaScript 便远远追不上了。执行速度的提升对高帧率下的视图数据计算很有帮助。

第二：Flutter 使用自己的渲染引擎来绘制 UI ，布局数据等由 Dart 语言直接控制，所以在布局过程中不需要像 RN 那样要在 JavaScript 和 Native 之间通信，这在一些滑动和拖动的场景下具有明显优势，因为在滑动和拖动过程往往都会引起布局发生变化，所以 JavaScript 需要和 Native 之间不停的同步布局信息，这和在浏览器中JavaScript 频繁操作 DOM 所带来的问题是类似的，都会导致比较可观的性能开销

 - ### 采用Dart语言开发

这个是一个很有意思但也很有争议的问题，在了解 Flutter 为什么选择了 Dart 而不是 JavaScript 之前我们先来介绍一下之前提到过的两个概念：JIT 和 AOT。

程序主要有两种运行方式：静态编译与动态解释。静态编译的程序在执行前程序会被提前编译为机器码（或中间字节码），通常将这种类型称为AOT （Ahead of time）即 “提前编译”。而解释执行则是在运行时将源码实时翻译为机器码来执行，通常将这种类型称为JIT（Just-in-time）即“即时编译”。

AOT 程序的典型代表是用 C/C++ 开发的应用，它们必须在执行前编译成机器码；而JIT的代表则非常多，如JavaScript、python等，事实上，所有脚本语言都支持 JIT 模式。但需要注意的是 JIT 和 AOT 指的是程序运行方式，和编程语言并非强关联的，有些语言既可以以 JIT 方式运行也可以以 AOT 方式运行，如Python，它可以在第一次执行时编译成中间字节码，然后在之后执行时再将字节码实施转为机器码执行。也许有人会说，中间字节码并非机器码，在程序执行时仍然需要动态将字节码转为机器码，这不应该是 JIT 吗 ? 是这样，但通常我们区分是否为AOT 的标准就是看代码在执行之前是否需要编译，只要需要编译，无论其编译产物是字节码还是机器码，都属于AOT。在此，读者不必纠结于概念，概念就是为了传达精神而发明的，只要读者能够理解其原理即可，得其神忘其形。


 ## 一个简单的应用: 计数器应用示例

 通过 Android Studio 或 VS Code 创建一个新的 Flutter 工程，命名为 "first_flutter_app"。创建好后，就会得到一个计数器应用的 Demo。
 > 注意，默认 Demo 示例可能随着编辑器 Flutter 插件的版本变化而变化，本例中会介绍计数器示例的全部代码，所以不会对本示例产生影响

 我们先运行创建的工程，效果如图2-1所示：
 ![](/image/flutter_demo.png)

 该计数器示例中，每点击一次右下角带“+”号的悬浮按钮，屏幕中央的数字就会加1。

在这个示例中，主要Dart代码是在 lib/main.dart 文件中，下面是它的源码：

```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key? key, required this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('You have pushed the button this many times:'),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```

## Flutter 怎么写

到这里终于到正题了，如果熟悉 web 前端，熟悉 React 的话，你会对下面要讲的异常的熟悉

### 开始
Flutter App 的一切从 lib/main.dart文件的 main 函数开始：
```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Welcome to Flutter',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

Dart 类 build 方法返回的便是 Widget，在 Flutter 中一切都是 Widget，包括但不限于
- 结构性元素，menu，button 等
- 样式类元素，font，color 等
- 布局类元素，padding，margin 等
- 导航
- 手势

Widget 是 Dart 中特殊的类，通过实例化(Dart 中new 是可选的)相互嵌套，你的这个 App 就是形如下图的一颗组件树(Dart 入口函数的概念， main.dart->main())

![Flutter Widget Tree](/image/flutter_widger_tree.png)

### Widget 布局
上说过 Flutter 布局思路来自 CSS，而 Flutter 中一切皆 Widget，因此整体布局也很简单：
- 容器组件 Container
- decoration(装饰属性，设置背景色，背景图，边框，圆角，阴影和渐变等)、margin、padding、alignment、width、height
- Padding，Center
- Row,Column,Flex
- Wrap, Flow 流式布局
- stack， z 轴布局
- ...

### Widget组件
Flutter 中 Widget 可以分为三类，形如 React 中“展示组件”、“容器组件”，“context”

- ##### StatelessWidget
这个就是 Flutter 中的“展示组件”，自身不保存状态，外部参数变化就销毁重新创建。Flutter 建议尽量使用无状态的组件
- ##### StatefulWidget
状态组件就是类似于 React 中的“容器组件”了，Flutter 中状态组件写法会稍微不一样
```
class Counter extends StatefulWidget {
  // This class is the configuration for the state. It holds the
  // values (in this case nothing) provided by the parent and used by the build
  // method of the State. Fields in a Widget subclass are always marked "final".

  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _counter = 0;

  void _increment() {
    setState(() {
      // This call to setState tells the Flutter framework that
      // something has changed in this State, which causes it to rerun
      // the build method below so that the display can reflect the
      // updated values. If you change _counter without calling
      // setState(), then the build method won't be called again,
      // and so nothing would appear to happen.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // This method is rerun every time setState is called, for instance
    // as done by the _increment method above.
    // The Flutter framework has been optimized to make rerunning
    // build methods fast, so that you can just rebuild anything that
    // needs updating rather than having to individually change
    // instances of widgets.
    return Row(
      children: <Widget>[
        RaisedButton(
          onPressed: _increment,
          child: Text('Increment'),
        ),
        Text('Count: $_counter'),
      ],
    );
  }
}

```

可以看到 Flutter 中直接使用了和 React 中同名的 setState方法，不过不会有变量合并的东西，当然也有生命周期
![Flutter生命周期](/image/flutter_live_circle.jfif)

## Flutter 一些例子

 - [flutter官方教程及demo](https://github.com/iampawan/FlutterExampleApps) https://github.com/iampawan/FlutterExampleApps
 - [网易云](https://github.com/boyan01/flutter-netease-music) https://github.com/boyan01/flutter-netease-music
 - [豆瓣](https://github.com/kaina404/FlutterDouBan) https://github.com/kaina404/FlutterDouBan

 > 学习资源 [flutter中文网](https://book.flutterchina.club/) 
