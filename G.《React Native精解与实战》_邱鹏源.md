## 《React Native精解与实战》精读笔记

### 写在前面
- 书籍介绍：本书由架构师撰写，包含ReactNative框架底层原理，以及与iOS、Android混合开发案例，精选了大量实例代码，方便读者快速学习。主要内容分为两大部分，第1部分“入门”包括第1~9章，介绍ReactNative框架的基本原理与使用方法；第2部分“进阶”包括第10~15章，介绍ReactNative框架的高阶开发与App部署相关知识。附录部分剖析了ReactNative的源码，可帮助读者研究ReactNative底层本质，还分享了一些ReactNative框架学习的相关资源。
- 我的简评：我是去年年底才开始学习使用React和React Native进行开发的，之前用的都是Vue的技术栈。这本书给我的感受就是逻辑清晰，通俗易懂，从基础入门到原理进阶，一一道来。但我想如果作者能再附带一个完整的项目实战可能效果更好，不过作者ParryQiu本人也写过很多技术教程以及录制了几套视频教程，有兴趣的可以去他个人的技术博客看看。
- ！！福利：文末有pdf书籍、笔记思维导图、随书代码打包下载地址哦

### 1.React Native简介

#### React简介
- 最早孵化于Facebook内部
- Jordan Walke是框架的创始人
- 底层核心是Virtual DOM

#### React Native简介
- 在React框架的基础之上
- 底层通过对IOS平台和Android平台原生代码的封装与调用
- JavaScript Core底层

#### React Native学前知识
- HTML5的基础知识
- CSS布局的基本知识
- JavaScript的基础知识
- Ios和Android两个平台的App打包、部署与上线
- Node.js以及npm包管理的知识

### 2.开发环境配置
- 安装nodejs
- 安装React Native
- 编辑器Vscode

#### 推荐插件
- React Native Tools
- react-beautify

### 3.React Native工作原理与生命周期

#### 3.1.框架工作原理
- JSX源码通过React Native框架编译后，通过对应平台的Bridge实现了与原生框架的通信
- UI层变更就映射为虚拟DOM后调用diff算法计算出变动后的JSON映射文件，最终由Native层将此JSON文件映射渲染到原生App的页面元素上，实现了项目中只需控制state以及props的变更来引起IOS与Android平台的UI变更

#### 3.2.与原生平台通信
- 与原生框架通信中，采用了JavaScriptCore作为JS VM，中间通过JSON文件与Bridge进行通信
- Chrome浏览器进行调试，那么所有的JavaScript代码都将运行在Chrome的V8引擎中，与原生代码通过WebSocket进行通信

#### 3.3.组件间通信
- 父子组件通信：props
- 子父组件通信：传入函数
- 多级组件之间的通信：context对象或global等方式
- 无直接关系组件间通信：AsyncStorage或JSON文件，EventEmitter/EventTarget/EventDispatcher继承或实现的接口，Signals模式，Publish/Suubscribe广播形式

#### 3.4.React Native生命周期
- 初始化阶段：constructor
- 加载阶段：componentWillMount、render、componentDidMount
- 更新阶段：componentWillReceiveProps、shouldComponentUpdate、componentWillUpdate、componentDidUpdate
- 卸载阶段：componentWillUnmount

### 4.React Native页面布局

#### 4.1.CSS3
- 选择器、2D/3D转换、盒子模型、动画、背景和边框、多列布局、文字特效、用户界面
- 引入新的模块：Flex布局，通俗称为弹性盒模型。为了更加有效的去布局、对其元素

#### 4.2.Flex弹性盒模型
- 元素以两个坐标方向进行布局，分别称为主轴和交叉轴
- 元素都存在于Flex容器中
- 以Flex Container的起始与结束作为坐标的起始与结束点
- 可以自动伸缩，默认可以填充剩余的空间

#### 4.3.Flex详解
- justify-content
- align-items
- align-self
- flex-direction
- flex-basis
- flex-wrap
- align-content
- flex-grow
- flex-shrink
- order
- flex-flow
- flex

#### 4.4.React Native中Flex
- 因为在React Native框架中直接使用JavaScript来实现属性的定义，所以所有属性都按照React Native中定义的写法来写，只是属性名称部分有连接符的，在React Native中变成了驼峰拼写的形式，并且某些属性的默认值进行了变更，但是本质的原理与作用是不变的

### 5.React Native开发调试技巧与工具

#### 5.2.常用调试属性（开发者菜单）
- 重新加载刷新应用
- 启动实时重新加载刷新
- 启用调试跟踪
- 启用热加载
- 显示审查元素工具
- 显示性能监控工具

#### 5.3.Chrome中远程调试
- 在 React Native 开发调试时，打开模拟器或真机设备上的开发者菜单，选择“ Debug JS Remotely ”后，本地的 Chrome 浏览器会自动打开一个 tab，URL 地址
  为 http://localhost:8081/debugger-ui 

#### 5.4.React Developer Tools工具
- 树形结构查看
- 源码搜索
- 边栏工具

### 6.React Native组件详解

#### 6.1.组件简介
- 提供一系列的内置组件供开发者使用
- 依托开源社区强大的生态系统，更有无穷无尽的开发组件可供使用

#### 6.2.视图组件View
- 用于布局的基础组件是View组件，其他所有的组件都可以布局在View组件中，类似网页布局中的div
- 支持Flex CSS属性，还支持React Native中的样式、一些触摸事件以及一些可访问性的属性设置
- View组件对应iOS平台的UIView，Android平台的Android.view以及HTML中的div

#### 6.3.底部导航组件TabBar
- iOS平台下的TabBarIOS
- Android平台没有官方提供的TabBar组件，推荐使用开源组件react-native-tab-navigator

#### 6.4.页面跳转组件
- iOS平台下的NavigatorIOS
- Android没有官方的页面导航组件，推荐使用react-native-navigation

#### 6.5.图片组件Image
- 提供多种方式加载图片资源，如加载网络图片、静态资源、本地图片、或读取用户相册中的图片
- Android平台下还可以支持GIF和WebP图片格式，iOS平台上支持psd
- 在iOS平台下，加载的资源必须是HTTPS协议资源

#### 6.6.文本组件Text
- React Native中不可以直接将文字放置在View组件之下
- 可以进行文字的嵌套处理
- React Native没有直接定义元素级别样式的能力，所以不能让所有的Text等组件直接通过继承的方式获取到统一的样式定义

#### 6.7.输入框组件TextInput
- 提供了接受用户通过键盘输入字符的功能，并可以通过后期的配置实现如自动纠错、自动大写、提示文字以及显示不同的键盘类型如邮件、数字等功能

#### 6.8.触摸处理类组件TouchableHighlight
- 在组件被点击时使用自定义的背景颜色进行高亮显示，以便在某些使用场景下让用户更能明确地感应到对应的操作
- 但只能包裹在一个层级的子元素上，如果有多个，那么就需要使用一个View组件将所有的元素包裹起来，再放置在TouchableHighlight组件下

#### 6.9.网页WebView组件
- App中有些页面组件是经常变动的，如用户帮助等，或者加载一个别人提供的页面

#### 6.10.滚动视图组件ScrollView
- ScrollView在指定了固定的高度之后即可以工作，用于生成一个可滚动的视图
- 但它会一次将所有的子元素渲染出来，数据量多的时候渲染效率肯定比较低下
- React Native提供另一个组件FlatList用于改进这个组件的性能问题，会进行延迟渲染

### 7.React Native API详解

#### 7.1.API简介
- React Native不仅为开发人员提供了大量用于App开发布局的组件，还提供了用于供开发人员调用的更加接近原生组件与功能的模块

#### 7.2.提示框Alert
- 用于提示用户的信息弹出框
- 如果在弹出提示框的同时需要用户输入一些信息，那么在iOS平台下就需要调用AlertIOS API

#### 7.3.App运行状态AppState
- 通过AppState可以获取到当前App是在前台运行还是在后台运行
- AppState共有三种状态：active（正在前台运行），background（在后台运行），inactive（前后台切换的一个短暂状态）

#### 7.4.异步存储AsyncStorage
- 为开发者提供了一个异步的、未加密、持久的、全局的键值对（key-Value）存储模块，如同HTML5中的LocalStorage
- IOS平台会使用原生代码将AsyncStorage中的小数据存储于序列化的字典数据结构中，而将大数据存储在单独的文件中
- Android平台会将AsyncStorage存储于RocksDB或SQLite中，取决于哪一个模块是可用的
- AsyncStorage是明文存储的。所以在iOS系统下，推荐将用户敏感信息存储在iOS的Keychain中，而在Android下，需要将用户敏感信息存储在SharedPreferences
- iOS已有组件react-native-keychain，Android有react-native-sensitive-info组件

#### 7.5.相机与相册API
- React Native框架中，API提供了CameraRoll供用户访问本地相册的功能，而在iOS系统中使用此功能时，还需要先链接RCTCameraRoll库
- 在App的开发过程中，一般在为用户提供读取相册的功能时，还应该给用户提供一个直接相机拍照的功能。所以在开发过程中会直接使用集成了读取相册以及使用相机拍照二合一的功能组件
- 开源组件React Native Image Picker提供了使用原生UI从设备相册中选取图片或者视频的功能，或者直接使用相机进行拍摄读取

#### 7.6.地理位置信息Geolocation
- 为App提供获取定位坐标的功能

#### 7.7.设备网络信息NetInfo
- 获取App当前网络状态的功能API
- 使用场景：通过网络的不同状态加载不同的资源，以便提高用户加载资源的速度，或者保存网络状态以便判断用户使用场景的变化
- iOS系统设备状态：none、wifi、cell、unknown

### 8.React Native 网络请求详解

#### 8.1.Restful API简介
- REST指的是一组架构约束条件和原则

#### 8.2.React Native中的网络请求
- 提供了Fetch API作为网络请求之用
- 现在产生的Fetch框架就是为了提供更加强大、高效的网络请求而生额。在Chrome浏览器中已经支持了Fetch函数
- Fetch支持了大部分常用的HTTP的请求并和HTTP标准兼容

#### 8.3.ListView组件
- 在通过Fetch API获取数据后，一般会使用React Native中的ListView组件进行数据的绑定操作

### 9.常用React Native开源组件详解

#### 9.1.React Native热门资源列表
- github地址：awesome-react-native

#### 9.2.React Native接入微博、微信、QQ登录
- 使用的组件是react-native-open-share

#### 9.3.更加美观的组件库
- react-virgin

#### 9.4.React Native 图表
- react-native-pathjs-charts，基于react-native-svg与paths-js

#### 9.5.react-native-gifted-listview
- 提供了iOS平台下的下拉刷新与Android平台下的点击刷新，以及列表底部加载更多组件功能。还提供了加载进度条、列表无数据时的默认视图、列表页头标题等功能

#### 9.6.react-native-vector-icons
- 提供了几千个图标，而且这些图标都是开源的

###	10.React Native运行原理与部署调试

#### 10.1.React Native运行原理
- 框架运行起来所依赖的几大组成部分：硬件设备或者模拟器，用于运行原生代码；Node.js服务端，也就是React Native Packger，负责源码的打包工作；Google Chrome，可以提供中间态的调试工具；后台的React Native JavaScript代码；
- React Native Packger实现原理：当我们在启动iOS或Android项目时，React Native框架会自动启动React Native Packager控制台来进行监听和打包，而手动启动的方法为在项目文件夹下运行命令npm start即可

#### 10.2.iOS平台部署于调试
- 运行App到模拟器上：react-native run-ios --simulator="iPhone X"
- 运行App到真机上：1、连接真机设备；2、配置代码签名；3、启用iOS应用的ATS（App Transport Security）；4、配置发布模式；5、将资源文件静态化打包；6、编译发布运行；

#### 10.3.Android平台部署与调试
- 连接Android设备
- Android离线JavaScript资源的打包
- 在真机上运行App
- Gradle：基于Apache Ant和Apache Maven概念的项目自动化工具。特点：自动处理包相依关系-取自Maven Repos的概念；自动处理部署问题-取自Ant的概念；条件判断写法直觉-使用Groovy语言；

#### 10.4.Android模拟器介绍
- Android Studio下自带Android模拟器
- 另一款模拟器Genymition可以模拟3000+的Android设备

### 11.IOS开发与React Native混合开发

#### 11.1.iOS平台混合开发简介
- 有时React Native框架还没有提供对应的JavaScript Api，就需要自己编写React Native框架与iOS平台结合的混合开发代码，使得React Native框架可以直接与iOS平台的原生代码进行通信

#### 11.2.iOS平台混合开发原理详解
- 实现过程：1.在iOS平台的原生代码中定义混合开发的入口，用于与React Native中的JavaScript代码进行通信；2.设置iOS平台下项目的编译必备设置；3.在React  Native项目中通过JavaScript代码调用混合开发实现的iOS平台原生功能；
- 开发特性：参数类型；回调函数；Promise；多线程；依赖注入；导出常量；枚举常量；发送事件到JavaScript；优化无监听处理的事件；Swift的实现方法；

### 12.Android平台与React Native混合开发

#### 12.1.Android平台混合开发简介
- 混合开发可以利用现有的Android原生平台的代码，并可以用于开发一些需求高性能、多线程的应用场景

#### 12.2.Android平台混合开发原理详解
- 开发步骤：1.在Android项目中通过原生代码实现提供给React Native调用的原生功能；2.在Android项目中将编写好的功能模块进行注册；3.定义功能模块的Android包；4.在React Native项目中通过JavaScript代码调用混合开发实现的Android平台原生功能；
- 开发特性：回调；Promise；发送事件到JavaScript；从StartActivityForResult中获取结果；监听生命周期事件；

### 13.React Native消息推送

#### 13.1.iOS平台消息推送机制
- 所有的iOS设备的消息推送都会经过Apple的消息推送服务器Apple Push Notification service（APNs），所有的推送消息由此服务器进行消息的下发
- 向APNs发送请求的服务器需要配置Apple开发者账号下的证书
- APNs发现目标设备离线后，会先将请求的消息存储起来，等设备上线后再进行消息的推送
- iOS平台的原生消息推送设置非常复杂，需要手动设置消息推送的开发者账号证书、推送消息请求的服务器证书、环境、编写以及APNs交互的代码
- iOS平台第三方消息推送框架会将开发的流程简单化，我们只需要与极光平台通过JPush API进行通信，JPush API提供了APNs Sender与Apple APNs Server进行通信，后续APNs与设备的通信与原生消息推送通信的过程一致，由APNs负责即可，前部分由极光平台代理
- JPush还提供了应用内消息推送部分，即App启动时，内嵌的JPush SDK会开启长连接到JPush Server，从而JPush Server 可以推送消息到App里

#### 13.2.Android平台消息推送机制
- Android环境下的消息推送方案：轮询（Pull）方式；长连接（Push）方式；使用XMPP、MQTT实现消息推送；
- 综合考虑，使用长连接（Push）方式在实现简易度以及资源损耗方面可以找到一个比较好的平衡点
- Android平台第三方通过开发者集成JPush Android SDK到其应用中，JPush Android SDK创建到JPush Cloud的长连接，为App提供永远在线的能力，当推送消息到达App时，只需要调用JPush API推送即可	

#### 13.3.React Native极光推送实战
- jpush-react-native
- 需要注意Android的应用包名与iOS App的Bundle ID最好保持一致

### 14.IOS、Android平台发布与热更新

#### 14.2.快速生成平台App图标与启动图的方法
- Ape Tools
- makeappicon.com

#### 14.3.iOS打包上架
- 需要使用XCode进行打包，打包后的App可以直接通过XCode提交到App Store供Apple审核

#### 14.4.Android打包上架
- App打包开放得多，通过Android Studio工具打包后可以直接生成单独的、可任意复制分发的Apk文件，用户只需要下载apk文件即可在自己的真机上安装

#### 14.5.ReactNative热更新
- 用户可以在不更新App的情况下进行App的热更新，甚至支持增量热更新，服务器只需要给用户下发新增的代码与资源文件，React Native框架会自动进行JS Bundle文件的合并，App在重新加载了JS Bundle后，App的功能和内容也进行了更新	16
- React Native框架会将我们开发的所有JavaScript代码，包括React Native框架代码、第三方组件代码、业务逻辑代码、图片等资源都打包在一个JS Bundle文件中，React Native App运行时会加载这个JS Bundle文件
- CodePush是微软推出的用于Cordova框架与React Native框架App热更新的框架，我们可以直接通过调用CodePush的SDK来快速、稳定的实现App的热更新功能
- 我们通过CodePush的CLI将更新的代码包以及相关资源文件按照CodePush的格式打包后提交到CodePush云平台，用户的设备会请求CodePush的服务器询问是否有文件更新

### 15.React Native 性能调试方法与技巧

#### 15.1.性能调优基准参数
- RAM 内存占用
- JSC JavaScript堆内存占用
- Views 当前屏幕中所有的view数量
- UI FPS(帧率)
- JS JavaScript帧率

#### 15.2.常见造成App性能低下的原因
- 1.console.log语句
- 2.Navigator性能问题
- 3.Touchable类组件使用问题
- 4.改变图片大小导致掉帧问题
- 5.改变视图时导致丢帧问题
- 6.ListView组件性能问题
- 7.在重绘一个没有改变的视图JS的FPS突然下降
- 8.JavaScript线程繁忙时导致JS线程掉帧

#### 15.3.查找性能问题以及调优方法
- XCode的性能测试工具Instruments
- Android原生的性能统计工具systrace

#### 15.4.性能优化方法与组件
- 1.性能优化原则：最核心就是尽量减少通过bridge的通信内容
- 2.使用特定平台组件：使用特定平台的组件开发特定平台的功能，如NavigatorIOS、TabBarIOS等
- 3.高性能第三方组件：react-native-fast-image；react-native-largelist；react-native-display；react-native-swipeview；react-native-interactable；
- 4.资源优化：React Native最终会将所有的资源文件打包成一个Bundle文件；控制Bundle的尺寸大小；除tab图标外其他的图片资源文件可以通过网络加载的方式进行加载，或者从图片CDN上加载；Bundle文件还可以进行拆分，让资源文件按需加载；

### 写在后面
- pdf书籍、笔记思维导图、随书代码打包下载地址：[https://pan.baidu.com/s/1ZJz711DrCfGRkqdlkx_HZg(提取码：b4yg)](https://pan.baidu.com/s/1ZJz711DrCfGRkqdlkx_HZg)
- 纸质书京东购买地址：[https://u.jd.com/OuBeOf](https://u.jd.com/OuBeOf)（推荐使用纸质书来学习）
- 为了方便在手机上查看，后面我会把这些笔记陆续发布到公众号“派三派四”，可以扫码关注一下，欢迎关注。
  ![扫码关注公众号](http://cdn.yzsunlei.com/pai_study/qrcode_for_gh_ef1e79fe4f71_258.jpg)