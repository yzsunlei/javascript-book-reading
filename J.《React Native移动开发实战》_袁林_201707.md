## 《React Native移动开发实战》精读笔记

### 写在前面
- 书籍介绍：《React Native移动开发实战》全面涵盖React Native组件、API、布局、第三方组件及原生接口开发等内容；详解React Native的开发工具、命令行工具及各种调试工具的使用；详细讲解一个电商App项目案例的开发过程，提高读者的实战开发水平；涉及软件开发流程、应用架构设计、代码重构，以及原生平台与跨平台开发等。
- 我的简评：《React Native移动开发实战》作为学习RN开发的入门书还是挺不错的，讲解的比较基础、比较全面，读完就能开发出一个完整的电商App项目。
- ！！福利：文末有pdf书籍、笔记思维导图、随书代码打包下载地址哦

### 第一章 为什么要学习React Native

#### 1.1.看透React Native
- 所谓的原生应用是指：使用原生开发语言、工具和平台开发的应用
- 原生应用开发的优势在于拥有较高的平台成熟度，包括平台的稳定性、运行时的性能及完善的生态
- 原生应用开发的缺点，那就是开发成本较高，导致开发效率相对较低
- 为了解决产品满足多个平台的需求，就有了所谓的跨平台应用开发
- 几种常见的跨平台解决方案：1、混合应用开发：在移动浏览器中嵌入 HTML 页面来开发移动应用，代表的有 Apache
Cordova、以及基于 Apache Cordova 衍生的lnoic等；2、跨平台的语言：例如，基于 .NET 和 C＃的 Xamarin，以及基于 Ruby 的 RubyMotion ；3、React Native：使用的是 Web 开发语言 （JavaScript ）和环境（ Node.js ）。类似的技术方案还有 NativeScript、Weex等
- 不同平台的适配就交由React Native平台去处理，而开发者只需要专注于React Native平台应用开发本身，体现出的优势如下：1、应用层的开发变得简单、高效和跨平台；2、应用稳定性、运行时的性能和原生平台接近；3、在理解 React Native 原理之后，开发者也可以根据实际的产品需求开发自己的 React Native 组件，以复用己有原生平台的大量优秀组件

#### 1.2.React Native的特点
- React Native 相比其他跨平台技术到底有哪些优势呢：1、其一： Learn Once, Write Anywhere；2、其二：简单易学的开发语言；3、其三：接近原生应用的性能和体验；4、其四：完善的生态系统

#### 1.3.搭建React Native开发环境
- 搭建 React Native 开发环境有以下几个主要步骤：1、原生开发工具：iOS开发使用Xcode, Android开发使用 Android Studio and SDK Tools；2、Node.js：React Native 是借助 Node.js，即 JavaScript 运行时来创建 JavaScript 代码的；3、React Native：安装 React Native 命令行工具；4、其他辅助工具 ：代码编辑器 Nuclide、Chrome浏览器等

#### 1.4.第一个React Native应用
- React Native目录和文件的说明：tests： React Native工程单元测试文件夹；android：原生Android工程文件夹；ios：原生 iOS工程文件夹；node_modules：React Native工程依赖的第三方库；index.android.is：React Native工程Android App入口文件；index.ios.js：React Native工程iOS App入口文件；package.json：React Native工程配置文件，描述了工程的所有信息以及第三方库的依赖关系；
- 运行项目：`react-native run-ios --simulator “iPhone 7”`，`react-native run-android emulator-5 554`
- 调试项目：真机调试时晃动设备就可以打开调试选项；iOS 模拟器快捷键：`command + D`；Android 模拟器快捷键：`command + M` 

### 第二章 全局解析React Native开发的基础

#### 2.2.Git版本控制工具
- 版本控制工具提供完备的版本管理功能，用于存储、追踪目录（文件夹）和文件的修改历史

#### 2.3.React Native的JSX解决方案
- JSXTransformer帮我们把代码中XML-Like语法编译转换成真实可用的JavaScript代码，它不仅仅创建View对象、设置， View 样式和布局，同时更加贴心的是，还构建了 View 之间的树形结构

#### 2.4.React Native的Flexbox布局
- React Native中Flexbox布局的工作原理和Web开发基本一致，只有少许差异。例如，默认值不同，React Native中flexDirection属性的默认值是column而不是row, alignltems的默认值是stretch而不是flex-start，另外，flex只能指定一个数 字值

#### 2.5.如何调试React Native项目
- 另一个非常重要的调试选项Debug JS Remotely选项

#### 2.6.实战-设计一个电商App
- 完整的软件开发流程还包括需求分析与设计、软件概要与详细设计、编写代码、测试、发布与更新等一系列的流程
- 分享给读者的经验是，先搭好架子是一个良好的开发习惯

### 第三章 React Native 的组件（1）

#### 3.1.创建新的电商App
- AppRegistry是所有React Native应用的入口，应用的根组件通过 AppRegistry － registerComponent方法注册自己，然后原生系统才可以加载React Native应用的代码井运行React Native应用

#### 3.8.实现页面间的数据传递
- props通常是在父组件中指定的，而且一经指定，在被指定的组件的生命周期中则不再改变
- state通常是用于存储需要改变的数据，并且当state数据发生更新时，React Native会刷新界面

### 第四章 React Native的组件（2）

#### 4.1.只支持特定平台的组件
- 只支持iOS的组件：DatePickerIOS、DatePickerIOS、PickerIOS、ProgressViewIOS、SegmentedControlIOS以及TabBarIOS 等
- 只支持Android的组件：DrawerLayoutAndroid、ProgressBarAndroid、Tool barAndroid以及ViewPagerAndroid等

#### 4.2.第三方组件
- React Native推荐使用react-native-maps来代替原生组件MapView
- 使用第三方组件也是有一定风险的，例如，作者停止维护、发现的问题修复不及时、组件的兼容性不好等

### 第五章 原生平台的适配和调试

#### 5.1.iOS平台的适配
- 所有iPhone屏幕的详细尺寸和分辨率，可以参考该网站的汇总The Ultimate GuideToiPhonResolutions
- iOS适配的技术基于自动布局（Auto Layout）系统，自动布局描述的是视图或组件之间的相对位置关系，它可以在应用运行时根据设备的屏幕尺寸动态改变各个试图或组件的尺寸
- 在React Native开发中，想要实现类似iOS平台自动布局的方式，可以使用Flexbox布局，而iOS平台实现自动布局的方法是约束。约束既可以定义布局属性的具体值，也可以定位布局属性之间的关系

#### 5.2.iOS开发的调试技巧
- 关于iOS平台的UI调试，还有一些优秀的第三方工具，例如，FaceBook 出品开源免费的chisel

#### 5.3.Android平台的适配
- Android适配是基于文件夹的，不同分辨率和尺寸的屏幕会自动适配相应文件夹下的布局或资源文件
- 一些基本概念：1、屏幕尺寸：屏幕尺寸是指手机屏幕对角线的英寸数；2、屏幕分辨率：屏幕分辨率是指屏幕宽、高像素数；3、屏幕像素密度：屏幕像素密度是指手机屏幕对角线上单位英寸内的像素数
- 常用的适配属性：1、wrap_content方式：wrap_content 布局元素将根据内容更改大小；2、match_parent方式：match_parent 自动填满整个父元素的空间；3、Constraintlayout方式：简单来说，这种布局方式和上面介绍的 iOS 自动布局（ Auto Layout ）有相似之处，即描述的都是视图或组件之间的关系

#### 5.4.Android平台的调试技巧
- 如果要调试原生项目的实现和逻辑，可以使用上述方法：如果要调试Android的布局，可以使用React Native的调试选项Toggle Inspector
- 晃动Android设备或者在Android模拟器上使用快捷键（command + M）打开调试选项，然后选择Toggle Inspector选项页，此时单击任意组件，即可查看该组件的布局信息

### 第六章 React Native的服务器端处理

#### 6.6.App数据的本地化存储
- React Native 开发中常见的本地数据存储的方法如下:
- AsyncStorage: React Native提供的键·值存储系统，接口和功能简单，只能存储字符串数据
- SQLite：原生应用开发中比较常见的数据存储方法
- Realm： 一种新兴的数据存储方法，使用简单但功能却很强大
- 其他：例如自定义API使用原生的存储方法、使用Redux生态圈的本地持久化实现redux-persist

### 第七章 常用React Native API

#### 7.2.动画API
- React Native 也提供了简洁、强大的动画 API
- requestAnimationFrame：最简单也是最“粗暴”的动画API，通过不断改变state的值，来实现组件的动画效果
- LayoutAnimated：体验和性能更好，适用于全局的动画配置，实现单个动画非常简洁方便
- animated：最强大的动画API，适用于实现灵活丰富的动画效果，例如多个动画的组合动画

#### 7.3.组件、React Native API、原生平台API
- API (Application Programming Interface）是指应用程序编程接口，在React Native平台上，API 是一些预先定义并实现好的函数，基于React native平台API，应用开发者通过调用这些接口就可以达到预期的目的，而无须了解 React Native 内部工作的细节
- 组件（Component）是对数据和方法的简单封装，可以理解为一个组件就是一个对象，它可以有自己的属性和方法。React Native 应用中，所有展示的界面都可以看做是一个组件，它们只是功能和逻辑上的复杂程度不同

#### 7.5.为应用添加更丰富的API
- AppState API能告诉开发者应用当前是在前台还是在后台，并且能在状态变化的时候发出通知
- 众所周知，iOS设备是没有物理返回按键的，而Android设备通常是有返回按键的。React Native提供的BackAndroid API就是用来处理返回按键的
- PermissionsAndroid API可以使用Android M（即 Android 7.0）开始提供的权限模型：有一些权限写在AndroidManifest.xml 文件中就可以在安装时自动获得，但有一些“危险”的权限则需要弹出提示框供用户选择

### 第八章 React Native与原生平台混合编程（1）
- 但是在使用React Native进行实际开发时，难免会遇到以下这些情况：1、需要使用React Native没有封装的原生功能；2、复用已有的原生组件或原生的第三方组件；3、多线程调用以及高性能要求的功能，如加密、图像处理等
- React Native 平台与原生平台的通信原理：React Native 平台调用原生平台基于NativeModules, 调用的方法是 `NativeModules.模块名称.接口名称`；原生平台返回数据到 React Native 平台基于回调，回调的原型定义是 `RCTRespon seSenderBlock（iOS 平台）`和 `com.facebook.react.bridge.Callback（Android 平台）`
- React Native应用的启动流程如下：1、首先还是启动原生平台的应用；2、然后原生平台再调用注册的根组件

### 第十章 电商App的复盘

#### 10.2.电商App的结构
- 通常应用（也包括这里的React Native应用）主要由以下3部分构成：页面显示和布局；数据和网络；逻辑控制
- 页面间的数据通信：上一级页面传递数据到下一级页面： 基于 props 属性；下一级页面返回数据到上一级页面： 基于 props 属性和回调函数

#### 10.3.优化和改进
- 从工程和结构来看：可以按照功能和模块划分工程结构。例如，图片都放到images文件夹下，自定义实现的JavaScript API可以放至相应的apis文件夹下
- 从页面和体验来看：应用的整体配色需要统一起来，样式和设计可以向成熟的第三方库组件靠拢
- 从文件和组件来看：公用的组件和逻辑尽量封装和复用。例如index.android.js和index.ios.js中的大部分组件、样式以及逻辑都是相同的，因此可以考虑复用这部分实现
- 从网络和数据来看：所有与服务器交互的接口可以单独封装成一个network的模块，所有与数据库交互的逻辑可以单独封装成一个db的模块
- 从整体的架构来看：页面间的数据通信和流程可以使用基于redux的设计
- 使用redux架构有如下3个原则：redux 己经不仅仅是一个第三方库或React应用架构方案，已经形成了一个基于redux的完成生态系统，包括组件、异步处理、存储、调试、国际化等一系列功能

#### 10.4.用到的组件
- 一些本书没有涉及。对于这些组件，大致可以分为以下3类：
- 平台特定组件：DataPickerIOS、DrawerLayoutAndroid、NavigatorIOS、PickerIOS、ProgressBarAndroid、ProgressViewIOS、SegmentedControllOS、Tool barAndroid
- 细节和体验优化组件：KeyboardAvoidingView
- 可以使用第三方代替组件：Modal

### 第十一章 App的发布

#### 11.1.App Store苹果应用商店
- 和普通的iOS应用一样，发布React Native应用生成的iOS安装包也有以下几个步骤：1、加入开发者计划；2、生成证书文件（包括生成发布证书、注册App ID、生成描述文件）；3、打包应用；4、发布到App Store上

#### 11.2.Andriod应用商店
- Android 要求所有应用都有一个数字签名才会被允许安装在用户手机上
- 酷传最大的作用是支持一键发布30多个应用市场，从而大大节省了Android应用发布的时间和精力

### 第十二章 App的热部署

#### 12.1.什么是热部署
- 热部署是指不需要重新审核和安装新版本的应用，通过服务器的动态更新来更新应用的功能
- 原生开发平台通过第三方的解决方案也可以具有热更新的能力，例如，iOS平台下的JSPatch, Android平台下的Bugly。但是这些都不是官方的解决方案，而且苹果公司己对此发出了警告

#### 12.2.解析React Native应用的工作原理
- 当执行 react-native run-ios 或者 react-native run-android 命令时：
- 首先，将 JavaScript 相关资源打包，例如，iOS应用的JavaScript资源打包为index.ios.bundle
- 然后，启动一个基于Node.js的 React Native 服务，这个服务运行在本地，监听的默认端口号是8081，最后当应用请求该地址的 index.ios.bundle 资源时，就会从React Native服务实时获取最新的JavaScript资源
- 最后，当应用请求该地址的index.ios.bundle资源时，就会从React Native服务实时获取最新的JavaScript资源。另外，当修改 index.ios.js文件时，React Native会重新打包JavaScript资源，这样就实现了应用的热更新

12.4.微软的热部署方案CodePush
- 自己实现的热更新服务虽然简单有效，但是也存在一些问题：1、首次使用有一定延时，因为需要下载JavaScript包；2、网络劫持等问题
- 实际开发中使用的热更新通常基于本地文件，即将更新包下载到本地后使用。基于上述原理，可以使用第三方的实现方案， 即微软推出的CodePush
- CodePush是微软提供的一套用于热更新 React Native 和 Apache Cordova应用的服务，提供 React Native 和 Apache Cordova 开发者直接部署移动应用更新给用户的云服务
- CodePush作为一个中央仓库，开发者可以推送更新，然后应用从客户端查询更新
- CodePush主要的功能和优势有：开源免费，CodePush源码托管在 GitHub；直接对用户部署代码更新；管理 Alpha 、Beta以及生产环境应用；支持 JavaScript 文件和图片资源的更新；支持 React Native 和 Apache Cordova 应用；

### 写在后面
- pdf书籍、笔记思维导图、随书代码打包下载地址：[https://pan.baidu.com/s/1G-FfptnZAJkCTV6cEzn9Iw(提取码：v1j8)](https://pan.baidu.com/s/1G-FfptnZAJkCTV6cEzn9Iw)