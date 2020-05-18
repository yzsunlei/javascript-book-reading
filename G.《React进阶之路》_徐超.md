## 《React进阶之路》精读笔记

### 写在前面
- 书籍介绍：《React进阶之路》详细介绍了React技术栈涉及的主要技术。本书分为基础篇、进阶篇和实战篇三部分。基础篇主要介绍React的基本用法，包括React 16的新特性；进阶篇深入讲解组件state、虚拟DOM、高阶组件等React中的重要概念，同时对初学者容易困惑的知识点做了介绍；实战篇介绍React Router、Redux和MobX 3个React技术栈的重要成员，并通过实战项目讲解这些技术如何和React结合使用。
- 我的简评：这本书适合初级的React开发者，书名虽是进阶，实际上就是一本入门的书。书中对一些React用法总结的还挺不错，实践性比较强。
- ！！文末有pdf书籍、笔记思维导图、随书代码打包下载地址，需要请自取

### 1.初识React

#### 1.1.简介
- 一句话：通过引入虚拟DOM、状态、单项数据流等设计理念，形成以组件为核心，用组件搭建UI的开发模式，理顺了UI的开发过程，完美的将数据、组件状态和UI映射到一起，极大地提高了开发大型Web应用的效率

#### 1.2.特点
- 声明式的视图层、简单的更新流程、灵活的渲染实现、高效的DOM操作

### 2.React基础

#### 2.1.Jsx
- 简介：一种用于描述UI的JavaScript扩展语法
- Jsx语法：基本语法、标签类型、JavaScript表达式、标签属性、注释
- Jsx不是必需的

#### 2.2.组件
- 定义：组件将应用的UI拆分成独立的、可复用的模块
- props：用于把父组件中的数据或方法传递给子组件，供子组件使用
- state：组件内部的状态，state的变化最终将反映到组件UI的变化上
- props和state比较：props是组件对外的接口，组件通过props接收外部传入的数据(包括方法)；state是组件对内的接口，组件内部状态的变化通过state来反映。另外，props是只读的，state是可变的
- 有状态组件和无状态组件：用不到state就称为无状态组件
- 属性校验和默认属性：PropTypes和defaultProps
- 组件样式：外部和内联
- 组件和元素：React元素是一个普通的JavaScript对象，React组件是一个class或函数

#### 2.3.组件的生命周期
- 挂载阶段：constructor、componentWillMount、render、componentDidMount
- 更新阶段：componentWillReceiveProps(nextProps)、shouldComponentUpdate(nextProps, nextState)、componentWillUpdate(nextProps, nextState)、render、componentDidUpdate(prevProps, prevState)
- 卸载阶段：componentWillUnmount

#### 2.4.列表和Keys
- 使用key属性来标记列表中的每个元素，通过key知道哪些元素发生了变化，只渲染发生变化的元素，提高渲染效率

#### 2.5.事件处理
- 合成事件，并不是原生的DOM事件
- 1.使用箭头函数
- 2.使用组件方法
- 3.属性初始化语法

#### 2.6.表单
- 受控组件：表单元素的值是由React来管理的（input文本框、select列表、checkbox复选框和radiobox单选框）
- 非受控组件：表单元素的状态依然由表单元素自己管理

### 3.React16新特性
- 1.render新的返回类型：数组和字符串
- 2.错误处理：错误边界componentDidCatch
- 3.Portals：任意组件都可以将弹窗组件渲染到根节点上，以方便弹窗的显示
- 4.自定义DOM属性：之前会忽略不识别的HTML和SVG属性，现在React会把不识别的属性传递给DOM元素

### 4.深入理解组件

#### 4.1.组件state
- 设计合适的state
- 正确修改state：不能直接修改state；state的更新是异步的；state的更新是一个合并的过程；
- state与不可变对象：状态的类型是不可变类型；状态的类型是数组；状态的类型是普通对象(不包含字符串、数组)；

#### 4.2.组件与服务器通信
- 挂载阶段通信：componentDidMount是执行组件与服务器通信的最佳地方
- 更新阶段通信

#### 4.3.组件间通信
- 父子组件通信：父向子：通过父组件向子组件的props传递数据完成；子向父：通过父组件向子组件传递的回调方法；
- 兄弟组件通信：通过状态提升的方式实现；即把组件之间需要共享的状态保存到距离他们最近的共同父组件内，任意一个兄弟组件都可以通过父组件传递的回调函数来修改共享状态，父组件中共享状态的变化也会通过props向下传递给所有兄弟组件，从而完成兄弟组件之间的通信；
- 组件层级太深时使用Context：创建context的方式是：在提供context的组件内新增一个getChildContext方法，返回context对象，然后在组件的childContextTypes属性上定义context对象的属性的类型信息
- 延伸：使用消息队列实现组件通信：改变数据的组件发起一个消息，使用数据的组件监听这个消息，并在响应函数中触发setState来改变组件状态

#### 4.4.特殊的ref
- 在DOM元素上使用ref：ref接收一个回调函数作为值，在组件被挂载或卸载时，回调函数会被调用。在组件被挂载时，回调函数会接收当前dom元素作为参数，在组件被卸载时，回调函数会接收null作为参数
- 在组件上使用ref：此时ref的回调函数接收的参数是当前组件的实例，提供在组件外部操作组件的方式
- 父组件访问子组件的DOM节点：需要在父组件获取子组件的某个DOM元素

### 5.虚拟DOM和性能优化

#### 5.1.虚拟DOM
- 虚拟DOM使用普通的JavaScript对象描述DOM元素

#### 5.2.Diff算法
- 原理：通过比较两次虚拟DOM结构的变化找出差异部分，更新到真实DOM上，从而减少对真实DOM上执行的操作，提高程序执行效率
- 几种情况：1.当根节点是不同类型时；2.当根节点是相同的DOM元素类型时；3.当根节点是相同的组件类型时；

#### 5.3.性能优化
- 1.使用生产环境版本的库
- 2.避免不必要的组件渲染
- 3.使用key

#### 5.4.性能检测工具
- React Developer Tools for Chrome
- Chrome Performance Tab

### 6.高阶组件

#### 6.1.基本概念
- 接收React组件作为参数，并且返回一个新的React组件。实现方式本质上是装饰者模式

#### 6.2.使用场景
- 1.操作props
- 2.通过ref访问组件实例
- 3.组件状态提升
- 4.用其他元素包装组件

#### 6.4.继承实现高阶组件
- 属性代理实现高阶组件：由高阶组件处理通用逻辑，然后将相关属性传递给被包装组件
- 还可以通过继承方式实现高阶组件，通过继承被包装组件实现逻辑的复用

#### 6.5.注意事项
- 1.为更好地区别包装了不同组件的高阶组件，需要对高阶组件的显示名称做自定义处理
- 2.不要在组件的render方法中使用高阶组件，尽量也不要在组件的其他生命周期方法中使用高阶组件
- 3.如果需要使用被包装组件的静态方法，必须手动复制这些静态方法
- 4.refs不会被传递给被包装组件
- 5.与父组件的区别

### 7.路由：用React Router开发单页面应用
- 7.1.前端路由的实现方式
- 7.2.Router对象
- 7.3.Route是React Router中用于配置路由信息的组件
- 7.4.Link链接组件

### 8.Redux：可预测的状态管理机

#### 8.1.三大原则
- 1.唯一数据源
- 2.保持应用状态只读
- 3.应用状态的改变通过纯函数完成

#### 8.2.主要组成
- 1.action：信息的载体
- 2.reducer：描述应用发生了什么操作
- 3.store：是action和reducer之间的桥梁

#### 8.3.store负责的工作
- 1.保存应用状态
- 2.通过方法getState()访问应用状态
- 3.通过方法dispatch(action)发送更新状态的意图
- 4.通过方法subscribe(listener)注册监听函数、监听应用状态的改变

### 9.Redux实战

#### 9.1.组织项目结构
- 目前主流的方案有三种：按照类型、按照页面功能和Ducks
- 按照类型：就是将充当component、container、action、reducer等不同角色的文件分别放在不同的文件夹下。问题：项目规模较大时，非常不方便
- 按照页面功能：就是将一个页面功能使用到的组件、状态和行为都在同一个文件夹下。优点：方便开发、易于功能的扩展。问题：需要频繁在reducer、action、action type等不同文件间切换
- Ducks：提倡将相关联的reducer、action types和action creators写到一个文件里。本质上是以应用的状态作为划分模块的依据，而不是以界面功能作为划分模块的依据。

#### 9.2.设计state
- 错误1：以API作为设计的state的依据
- 错误2：以页面UI作为设计state的依据
- 合理设计state：最重要的是记住一句话：像设计数据库一样设计state；类似设计数据库总结的三个原则（1.把整个应用的状态按照领域分为若干个子状态，子状态之间不能保存重复的数据；2.state以键值对的结构存储数据，以记录的key或ID作为记录的索引，记录中的其他字段都依赖于索引；3.state中不能保存可以通过state中的已有字段计算而来的数据，即state中的字段不互相依赖；）

#### 9.3.设计模块
- app模块、auth模块、posts模块、comments模块、users模块、ui模块、index模块

#### 9.4.连接Redux
- 注入state
- 注入action creators
- connecte连接PostList和Redux

#### 9.5.Redux调试工具
- Redux DevTools
- 一款用于调试Redux应用的浏览器插件，可以实时的显示当前应用的state信息、action触发的记录以及state的变化

#### 9.6.性能优化
- React Router引起的组件重复渲染问题
- Immutable.js：Redux的state必须是不可变对象，reducer中每次返回的state都是一个新对象；Immutable.js的作用在于以更高效的方式创建不可变对象；主要3个优点（保证数据的不可变、丰富的API、优异的性能）
- Reselect：Redux state的任意改变都会导致所有容器组件的mapStateToProps的重新调用，进而导致使用到的selectors重新计算；Reselect可以创建具有记忆功能的selectors，当selectors计算使用的参数未发生变化时，不会再次计算，而是直接使用上次缓存的计算结果；

### 写在后面
- pdf书籍、笔记思维导图、随书代码打包下载地址：[https://pan.baidu.com/s/15g8dwBHcPJBVEmO7mlh52g(提取码：zfjg)](https://pan.baidu.com/s/15g8dwBHcPJBVEmO7mlh52g)
- 纸质书京东购买地址：[https://u.jd.com/wnGjvI](https://u.jd.com/wnGjvI)（推荐购买纸质书来学习）
- 为了方便在手机上查看，后面我会把这些笔记陆续发布到公众号“派三派四”，可以扫码关注一下，欢迎关注。
  ![扫码关注公众号](http://cdn.yzsunlei.com/pai_study/qrcode_for_gh_ef1e79fe4f71_258.jpg)