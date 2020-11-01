《Koa和Node.js开发实战》
1.	第一章 Node.js入门	1
1.1.	1.1.Node.js介绍	1
1.1.1.	官方描述：Node.js 是一个基于 Chrome v8 引擎的 JavaScript 运行环境 。 Node.js 使用了一个事件驱动、非阻塞式 I/0 的模型，使其轻量又高效。Node.js 的包管理器 NPM，是全球最大的开源库系统。	1
1.1.2.	Node.js 是一个基于 Chrome v8 引擎的 JavaScript 运行时环境	1
1.1.3.	运行时是一个平台，它把运行在底层的操作系统和体系结构的特点抽象出来，承担了解释与编译、堆管理（ Heap Management ）、垃圾回收机制（ Garbage Co llection ）、内存分配 C Memory Allocation ）、安全机制 (Security)等功能 。	1
1.1.4.	解决问题的关键是非阻塞和异步 I/O 。	1
1.1.5.	Node.js使用了事件驱动、非阻塞式 I/O 模型，轻量又高效。	1
1.1.6.	事件驱动的异步 I/O 模型使得 Node.js 非常适合用来处理 I/O 密集型应用	1
1.1.7.	例如 Web 聊天室（ Socket.io ）、 Web 博客（ Hexo ） 、 Web 论坛（ Node Club ）、前端模块管理平台（ Bower.js ）、浏览器环境工具（ Browserif沪、命令行工具（ Commander)等。	1
1.2.	1.2.NPM	1
1.2.1.	NPM 是一个 JavaScript 的模块管理工具，遵循 CommonJS 标准，由 Isaac Z . Schlueter 开发	1
1.2.2.	Facebook 、 Google 、 Exponent 和 Tilda 于 2016 年开发了一款新的模块管理工 具 Yam ，在速度和可靠性上较 NPM 更加优秀	1
1.2.3.	package.json文件包含了模块所有的依赖关系，也可以定义依赖项的元数据（如名称、版本、许可证等）	2
1.2.4.	NVM ( Node Version Manager, Node 版本管理器）	2
1.2.5.	NProxy 是一个跨平台，支持单文件、多文件及目录替换，支持 HTTP 和 HTTPS 协议的 Web 代理工具，在文件替换功能上尤其出色。	2
1.3.	1.3.Visual Studio Code编辑器	2
1.3.1.	Visual Studio Code 是微软在 2015 年发布的一款能够运行在 Windows 、macOS 和 Linux 上的跨平台编辑器	2
2.	第二章 遇见Koa	2
2.1.	2.1.Koa介绍	2
2.1.1.	Koa 是基于 Node.js 的 Web 框架，其特点是轻量、健壮、富有表现力，由 Express 的原班人马打造，目前有 Koal 和 Koa2 两种版本。	2
2.1.2.	Express 4 之前的版本主要基于 Connect，封装了大量便利的功能，如路由、视图处理、错误处理等 。Express 4 之后不再依赖 Connect，除 express.static外的内置中间件也全部作为单独模块安装 。	2
2.1.3.	Koa 采用 Generator 函数+yield 语句处理异步函数，解决了“回调金字塔”的问题 。 但是 Generator 的设计初衷不是为了解决异步编程的问题，而是为了实现“协程”的功能 。	2
2.2.	2.2.Context对象	2
2.2.1.	Koa 中有一个非常重要的概念叫上下文	2
2.2.2.	Koa 将 Node.js 的 Request （请求〉和 Response （响应）对象封装到 Context 对象中，所以也可以把 Context 对象称为一次对话的上下文，通过加工 Context 对象，就可以控制返回给用户的内容。	2
2.2.3.	Koa 应用程序中的每个请求都将创建一个 Context，并在中间件中被作为参数引用	3
2.2.4.	Koa 没有封装获取 POST 请求参数的方法，因此需要解析 Context 中的原生 Node .js 请求对象 req	3
2.2.5.	可以通过 koa-bodyparser 等中 间件来获取 POST 请求的参数， 而且更加方便。	3
2.3.	2.3.Koa的中间件	3
2.3.1.	Koa 应用程序其实就是一个包含一组中间件函数的对象	3
2.3.2.	中间件函数是一个带有 ctx 和 next 两个参数的简单函数。	3
2.3.3.	ctx 就是之前介绍的上下文，封装了 Request 和 Response 等对象；next 用于把中间件的执行权交给下游的中间件。	3
2.3.4.	“洋葱模型”来解释中间件的执行顺序。先进后出的堆栈结构	3
2.3.5.	如果一个中间件没有调用 await next(),后面的中间件将不会被执行	3
2.3.6.	常用 Koa 中间件介绍：koa-bodyparser、koa-router、koa-static、koa-views	3
2.3.7.	koa-static 是专门用于加载静态资源的中间件，通过它可以为页面请求加载 css 、 JavaScript 等静态资源，而 koa-views用于加载 HTML 模板文件 。	3
3.	第三章 路由	3
3.1.	3.1.路由介绍	3
3.1.1.	Python官网的描述：路由（请求路由或 URL 分发）是匹配 URL 到相应处理程序的活 动）。	4
3.1.2.	通俗地说，路由是根据 URL 的变更重新渲染页面布局和内容的过程 。	4
3.1.3.	前端路由主要解决了两个问题：在页面不刷新的前提下实现 URL 的变化， 以及捕捉 U虹的变化并执行相应的页面逻辑。	4
3.2.	3.2.koa-router路由中间件	4
3.2.1.	koa-router 具有丰富的 API ，可以实现命名参数、命名路由 、多路由中间件 、多路由、嵌套路由等功能。	4
3.2.2.	koa-router 从 5.2.0 版本开始支持 ECMAScript 2016 的 async/await 语法糖。	4
3.2.3.	REST 设计一般符合以下条件：1、程序或应用的事物都应该被抽象为资源；2、每个资源对应唯一的 URL；3、使用统一的接口对资源进行操作；4、对资源的各种操作不会改变资源标识；5、所有的操作都是无状态的 。	4
3.2.4.	在 HTTP 中，会被经常使用的方法有 POST 、 DELETE 、 PUT 、 GET，对应于增、删、改、查，即常说的 CRUD(Create 、 Retrieve、 Update 、 Delete ）操作。	4
3.2.5.	不得不提的是 GitHub v4 的 API 使用了全新的设计风格 GraphQL	4
3.2.6.	与嵌套路由不同的是，路由前缀是一个固定的字符串，不能添加动态参数	4
3.2.7.	常见鉴别用户权限的方式有两种， 一种是广泛使用的 Cookie-Based Authentication （基于 Cookie 的认证模式），另一种是 Token-Based Authentication （基于 Token 的认证模式） 。	5
3.2.8.	Token 方式最大的优点在于采用了无状态机制 ，在此基础上，可以实现天然的跨域支持、前后端分离等，同时降低了服务端开发和维护的成本 。Token 方式的缺点在于服务器每次都需要对 Token 进行校验，这一步骤会对服务器产生运算压力 。	5
4.	第四章 HTTP	5
4.1.	4.1.HTTP介绍	5
4.1.1.	HTTP 全称为 HyperText Transfer Protocol ，即超文本传输协议，是当今互联网使用最广泛的网络基础协议。	5
4.1.2.	HTTP/ I.0 在 HTTP/0.9 的基础上做出了大量的改进，增加了访问不同对象类型的功能，不仅可以传输文本，还可以传输图像、视频、二进制文件等。同时，在 GET 请求命令的基础上，增加了 POST 、 PUT、 HEAD 、 DELETE 、LINK 等命令 。另外，还增加了头部信息，如 User-Agent 、 Accept 、 Last-Modified 、 Content-Type 等至今仍在使用的请求头字段。	5
4.1.3.	HTTP/ 1.1 目前依旧被广泛地使用在互联网领域，其在 HTTP/1.0 的基础上又做了大量的改进	5
4.1.4.	2009 年， Goolge 公开了自己研发的 SPDY （单词 speedy 的缩写〉 协议，通过多路复用、压缩、优先级、安全等新技术方案，缩短了网页的加载时间，井提高了安全性 。IETF( The Internet Engineering Task Force,国际互联网工程任务组〉随后对 SPDY 进行了标准化， 并作为制定 HTTP/2 标准的起点 。	5
4.1.5.	URI: Uniform Resource Identifier （统一资源标识符）；URL: Uniform Resource Locator （ 统一资源定位符〉	5
4.1.6.	一个完整的URL一般由 7 个部分组成：scheme: [//[user[:password]@]host[:port]][/path][?query][#fragment]	6
4.1.7.	HTTP 状态码表示服务器响应状态的 3 位数字。 HTTP 状态码主要包括 1** （消息）、 2**（成功）、 3**（重定向）、 4**（请求错误〉、 5**和 6** （服务器错误）等 6 种不同类型。	6
4.1.8.	目前常用的 9 种 HTTP 请求：GET、POST、HEAD、PUT、DELETE、CONNECT、OPTIONS、TRACE、PATCH	6
4.1.9.	首部字段是构成 HTTP 的重要元素之一 ，用以提供 HTTP 传输过程中额外 的重要信息 。常见的首部字段：User-Agent、Last-Modified、Content-Length、Content-Encoding、Content-Type、Expires、Set-Cookies、Cookie、Cache-Control、ETag、Vary、Server	6
4.2.	4.2.HTTP/2	6
4.2.1.	HTTP/2 在 HTTP/1.1 的基础上保持原有语义和功能不变，但极大地 提升了性能。	6
4.2.2.	采用二进制格式传输数据：之前的 HTTP/1.* 均采用文本格式传输数据，而 HTTP/2 则选择了使用二进制格式传输数据。	6
4.2.3.	在 HTTP/2 中，基本的协议单位是帧，每个数据流均以消息形式发送，消息由一个或 多个帧组合而成。帧的内容包括：长度（ Length ）、类型（ Type ）、标记（ Flags ）、保留字段 CR）、流标识符（ Stream Identifier）和帧主体（ Frame Payload ） 。	6
4.2.4.	多路复用：HTTP/2 重新定义了底层的 HTTP 语义映射，允许在同一个连接上使用请求和响应双向数据流	6
4.2.5.	流的优先级：在 HTTP/2 中可以为每个流（ Stream ）设置优先级，高优先级的流会被服务优先处理井返回给客户端	7
4.2.6.	首部压缩：HTTP/2 引入了 HPACK 压缩首部数据。 由于 HPACK 压缩引入了索引表概念，包含静态表和动态表 。	7
4.2.7.	服务端推送：例如，可以在请求该HTML 文档的同时， 一并推送与之关联的静态资源文件，达到性能优化的目的。	7
4.3.	4.3.Node.js的querystring模块	7
4.3.1.	querystring 模块由 Node .js 原生提供，包含相关解析和格式化工具，共有 4 种方法：escape、unescape、parse、stringify	7
4.3.2.	通过 query 或 querystring 可以直接获取 GET 请求的数据，唯一不同的是 query 返回的是对象，而querystring 返回的 是查询字符串。	7
4.4.	4.4.koa-bodyparser中间件	7
4.4.1.	通过 POST 请求传递表单数据、上传数据文件、传递 JSON 格式的数据等。	7
4.4.2.	koa-bodyparser 中间件用于解析请求的 Body，支持 JSON 、 Form 和 Text 类型 。	7
4.4.3.	解析后的数据会被存储在 ctx.request.body 中，如果没有数据则为空对象	7
5.	第五章 构建Koa Web应用	7
5.1.	5.1.MVC	7
5.1.1.	MVC 模式的目的是实现动态的程序设计，简化程序后续 的修改和扩展过程，并且使模 块能够被重复利用。	7
5.1.2.	需要注意的是： MVC 不是一种技术，而是一种设计理念 。	8
5.1.3.	MVC 模式主要采用分层的思想来降低耦合度，从而使系统更 加灵活， 扩展性更强 。	8
5.1.4.	MVC 模式在概念上强调 Model、View 和 Controller 的分离，模块间也遵循着由 Controller进行消息处理、 Model 进行数据源处理、View 进行数据显示的职责分离原则。	8
5.1.5.	3个部分分离实现：Model负责数据访问、Controller负责处理消息、View负责显示数据	8
5.1.6.	通常意义上的三层架构是将整个业务应用 划分为界面层（ User Interface Layer ）、业务逻辑层（ Business Logic Layer ）、数据访问层（ Data Access Layer ） 。微软推荐的分层式结构一般也分为三层，从下至上分别为数据访问层、业务逻辑层（又称领域层〉和表示层 。	8
5.1.7.	不管是 MVC 还是三层架构，其实设计理念都是一致的： 分层，解耦	8
5.2.	5.2.模板引擎	8
5.2.1.	模板引擎是 Web 应用中用来生成动态 HTML 的工具，负责将数据模型与 HTML 模板 结合（模板渲染），生成最终的 HTML 。	8
5.2.2.	模板引擎不属于特定技术领域，是为了使用户界面与业务数据（内容）分离而产生的，是跨领域跨平台的概念。	8
5.2.3.	几种类型：“置换型”、“解释型”、“编译型”	8
5.2.4.	可以在 Node.js 中应用且比较成熟的模板引擎有很多 ，例如 EJS 、 Jade （现己改 名为 Pug ） 、 Handlebars 、 Nunjucks 、 Swig 等。	8
5.2.5.	一般情况下，模板引 擎都需要具备这些功能：变量、逻辑表达式、循环、 layout、 include 、宏和扩展等。	9
5.2.6.	宏 ： 定义可复用的内容，类似于编程语言中的函数	9
5.3.	5.3.静态资源	9
5.3.1.	koa-static 是官方提供的文件服务器中间件，依赖于另一款官方中间件 koa-send	9
5.3.2.	动态资源需要使用的系统开销大于静态资源 。	9
5.3.3.	MIME Type 通常是通过 HTTP，由 Web 服务器告知浏览器的， 被定义在 Content-Type header 中 。	9
5.4.	5.4.其他常用开发技巧	9
5.4.1.	HTTP 请求的整个过程中所传输的数据，本身没有任何特定的格式或形态，但客户端在接收数据时，会按照 MIME Type 指定的方式去处理 。	9
5.4.2.	koa-multer 源于 Multer，并以中间件的形式对 Multer 进行包装，而 Multer 是一个基于 Busboy 模块（专门用于处理表单数据 的模块〕的 Node.js 中间件， 主要用于上传文件，处理 multipart/form-data 类型的表单数据。	9
5.4.3.	永远不要将 Multer 作为全局中间件使用，因为恶意用户可以上传文件到一个预料之外的路由 。 开发者应该只在自己需要处理上传文件的路由上使用 Multer。	9
6.	第六章 数据库	9
6.1.	6.1.数据库介绍	9
6.1.1.	数据库主要具备以下特点 ：数据共享；减少数据冗余度；数据独立；数据一致性和可维护性；故障恢复	9
6.1.2.	数据库一般采用索引来提升查询效率	10
6.1.3.	通过事务，也就是一组有序的数据库操作指令，进行“捆绑”执行，要么全部执行，要么全部不执行，从而保证了数据的一致性和完整性 。	10
6.1.4.	关系型数据库一般通过 SQL (Structured Query Language ，结构化查询语言〉来操作数据库。代表：Oracle、SQL Server、MySql、MariaDB	10
6.1.5.	非关系型数据库一般不采用 SQL 作为查询语言，也经常避免使用类似 SQL 中的 JOIN 操作来关联多张数据表。代表：MongoDB、Memcached、Redis	10
6.2.	6.2.在Koa中应用MySQL数据库	10
6.2.1.	ORM 的字面意思为对象关系映射，它提供了概念性的、易于理解的模型化数据的方法。	10
6.2.2.	在Node.js 中， 一般采用 Sequelize 这个 ORM 类库来操作数据库。	10
6.2.3.	可以直接定义数据模型来创建数据表，而不必去数据库中使用 SQL 脚本创建。	10
6.2.4.	Sequelize 通过 define 方法定义数据模型，通过访问模型提供的接口来查询和更新数据，避免开发者直接访问数据库	10
6.3.	6.3.在Koa中应用MongoDB数据库	10
6.3.1.	MongoDB 是由 C＋＋编写的基于分布式文件存储的开源数据库	10
6.3.2.	开发Node.js应用时， 一般借助 Mongoose 类库来访问数据库	10
6.4.	6.4.在Koa中应用Redis数据库	11
6.4.1.	Redis 可用作数据库、高速缓存和消息队列代理 。 Redis非常适合处理那些短时间内被高频访问但又不需要长期访问的简单数据存储	11
6.4.2.	Redis 是一个开源、使用 ANSIC 语言编写 、 遵守 BSD ( Berkeley Software Distribution, 伯克利软件套件）协议、支持网络、可基于内存亦可持久化的日志型 Key-Value 数据库，并提供多种语言的 API。	11
6.4.3.	在 Redis 中，集合是通过哈希表实现的，所以添加、删除、查找的复杂度都 是 o(1)	11
6.4.4.	GitHub 上开源的 Redis库有很多 ， 其中使用最广、最成熟的是 node_redis 库	11
6.4.5.	Session 中的数据一般都是短时间内高频访问的，需要保证性能，所以比 较好的方式是内存配合 Redis 做一个持久化。	11
6.4.6.	在 Koa 应用中可以使用 koa-session 中间件来操作 Session。	11
7.	第七章 单元测试	11
7.1.	所谓单元是指应用的最小可测试部件，通常是单个函数、过程或方法 。	11
7.2.	单元测试通常拥有如下优势：尽早发现问题并进行更正； 简化集成测试的复杂度；生成文档。	11
7.3.	两个概念：TDD是测试驱动开发、BDD是行为驱动开发	11
7.4.	7.1.Chai断言库	11
7.4.1.	所谓断言是一种放在程序中的逻辑判断，目的是检 测结果是否与开发者的预想一致。	12
7.4.2.	Node.js 内置了断言库 Assert，但并不是一个真正的测试运行器	12
7.4.3.	单元测试的测试用例中推荐使用Chai	12
7.4.4.	Chai 包含 3 个断言库，其中有 BDD 风格的 Expect/Should 和 TDD 风格的 Assert 。	12
7.4.5.	可以直接使用 assert(expression, message) PEI数来对应所有断言的情况	12
7.5.	7.2.Mocha框架	12
7.5.1.	Mocha 是一个功能丰富且流行的 JavaScript 测试框架，支持回调函数、Promise 、 Async等。	12
7.5.2.	Mocha 的关键词只有 describe 和 it 两个	12
7.6.	7.3.SuperTest测试RESTful API	12
7.6.1.	SuperTest 就是一个用来实现 Web 请求的库，是可以用来测试 HTTP 服务的工具。	12
7.6.2.	SuperTest 也是对 SuperAgent 工具 的扩展，在支持所有 SuperAgent 的 API 基础上，提供了对请求结果的断言处理 。	12
7.7.	7.4.其他常用工具	12
7.7.1.	Nock 提供给开发者一个模拟请求服务器响应的情况，而 Nye 则可以检查代码的测试覆盖情况。	12
7.7.2.	单元测试过程中， 一方面不一定能够调用这些 API 服务， 另一方面单元测试并不需要承担对第三方服务的测试。	12
7.7.3.	Nock 就是一个模拟服务器响应的工具。Nock 会覆盖 Node.js 的 http.request 方法 ， 来伪造一个结果	13
7.7.4.	完成所有单元测试后，也可能存在测试用例不够完整或不能测试到所有的应测试代码的情况 。另一种情况是被测试的代码中存在一些“死”代码，即逻辑上不能被执行到的代码 。	13
7.7.5.	4 个种类：语句覆盖率（ Stmts ）、分支覆盖率 （Branch）、函数覆盖率（ Funes ）、行覆盖率（ Lines ）	13
8.	第八章 优化与部署	13
8.1.	8.1.服务优化	13
8.1.1.	通过完整的日志记录，能够快速地定位、还原问题现场。	13
8.1.2.	根据日志的用途， 一般可以将日志分为访问日志和应用日志。	13
8.1.3.	log4js 中的日志输出可以分为 7 个级别，日志级别由低到高：trace跟踪信息、debug调试信息、info非调试和跟踪信息、warn警告信息、error错误信息、fatal严重错误信息	13
8.1.4.	在项目开发中，一般会分为开发、测试、验证、线上等环境。	13
8.1.5.	除 try/catch 之外，也可以用另外一种方法解决： 使用 uncaughtException 。	13
8.1.6.	传递异常情况，常见的方式有 3 种，包括 throw 抛出、 callback 回调传递和通过 EventEmitter 触发 error 。	13
8.2.	8.2.部署	13
8.2.1.	进程管理器用于对应用状态进行管理，可以启动、暂停、重启或删 除应用进程，也可 以对进程进行监控，包括对进程错误的记录。	13
8.2.2.	Docker 是一个开源的应用容器引擎，能够让应用程序部署在软件容器下，这个容器是 在 Linux 操作系统上的一个软件抽象层。	14
8.2.3.	Travis CI 是一个免费的持续集成服务。持续集成是指在代码开发过程中经常性地集成 （ 通常在某个特定分支修改后 就触发〉。	14
8.2.4.	在持续集成环境中有两种自动部署方法： 一种是使用脚本登录对应的线上服务器，在己经设置好 Git 环境的服务器上获取代码，然后启动；另一种是在构建服务器上生成代码压缩包，利用 scp 传输到线上服务器，解压后启动	14
8.3.	8.3.服务监控	14
8.3.1.	一般来说，服务的性能分为两部分：服务的吞吐量和服务对资源的占用量。	14
8.3.2.	Node.js 是基于 v8 引擎的 ， 在 JavaScript 中，内存采用堆的方式来分配，因 此 ， 可以根据堆的统计信息查看 Node. 月民务的内存使用情况。	14
8.3.3.	一般情况下， HTTP 服务采用 QPS（查询量/秒）和 TPS（事务/秒） 来衡量服务的性能	14
8.3.4.	一般数据通过 Kafka （消息队列）上报到 Influxdb （分布式时序数据库〉中存储，最后通过 Grafana （可视化图表〉展示出来。	14
8.3.5.	一个强大的开源日志管理系统 ELK （即 Elasticsearch Logstash Kibana ） 。	14
8.3.6.	PM2 官方也提供了 一个服务--Keymetrics 来进行性能数据的分析和展示 。	14

1. 第一章 Node.js入门
1.1. 1.1.Node.js介绍
1.1.1. 官方描述：Node.js 是一个基于 Chrome v8 引擎的 JavaScript 运行环境 。 Node.js 使用了一个事件驱动、非阻塞式 I/0 的模型，使其轻量又高效。Node.js 的包管理器 NPM，是全球最大的开源库系统。
1.1.2. Node.js 是一个基于 Chrome v8 引擎的 JavaScript 运行时环境
1.1.3. 运行时是一个平台，它把运行在底层的操作系统和体系结构的特点抽象出来，承担了解释与编译、堆管理（ Heap Management ）、垃圾回收机制（ Garbage Co llection ）、内存分配 C Memory Allocation ）、安全机制 (Security)等功能 。
1.1.4. 解决问题的关键是非阻塞和异步 I/O 。
1.1.5. Node.js使用了事件驱动、非阻塞式 I/O 模型，轻量又高效。
1.1.6. 事件驱动的异步 I/O 模型使得 Node.js 非常适合用来处理 I/O 密集型应用
1.1.7. 例如 Web 聊天室（ Socket.io ）、 Web 博客（ Hexo ） 、 Web 论坛（ Node Club ）、前端模块管理平台（ Bower.js ）、浏览器环境工具（ Browserif沪、命令行工具（ Commander)等。
1.2. 1.2.NPM
1.2.1. NPM 是一个 JavaScript 的模块管理工具，遵循 CommonJS 标准，由 Isaac Z . Schlueter 开发
1.2.2. Facebook 、 Google 、 Exponent 和 Tilda 于 2016 年开发了一款新的模块管理工 具 Yam ，在速度和可靠性上较 NPM 更加优秀
1.2.3. package.json文件包含了模块所有的依赖关系，也可以定义依赖项的元数据（如名称、版本、许可证等） 
1.2.4. NVM ( Node Version Manager, Node 版本管理器）
1.2.5. NProxy 是一个跨平台，支持单文件、多文件及目录替换，支持 HTTP 和 HTTPS 协议的 Web 代理工具，在文件替换功能上尤其出色。
1.3. 1.3.Visual Studio Code编辑器
1.3.1. Visual Studio Code 是微软在 2015 年发布的一款能够运行在 Windows 、macOS 和 Linux 上的跨平台编辑器
2. 第二章 遇见Koa
2.1. 2.1.Koa介绍
2.1.1. Koa 是基于 Node.js 的 Web 框架，其特点是轻量、健壮、富有表现力，由 Express 的原班人马打造，目前有 Koal 和 Koa2 两种版本。
2.1.2. Express 4 之前的版本主要基于 Connect，封装了大量便利的功能，如路由、视图处理、错误处理等 。Express 4 之后不再依赖 Connect，除 express.static外的内置中间件也全部作为单独模块安装 。
2.1.3. Koa 采用 Generator 函数+yield 语句处理异步函数，解决了“回调金字塔”的问题 。 但是 Generator 的设计初衷不是为了解决异步编程的问题，而是为了实现“协程”的功能 。 
2.2. 2.2.Context对象
2.2.1. Koa 中有一个非常重要的概念叫上下文 
2.2.2. Koa 将 Node.js 的 Request （请求〉和 Response （响应）对象封装到 Context 对象中，所以也可以把 Context 对象称为一次对话的上下文，通过加工 Context 对象，就可以控制返回给用户的内容。
2.2.3. Koa 应用程序中的每个请求都将创建一个 Context，并在中间件中被作为参数引用
2.2.4. Koa 没有封装获取 POST 请求参数的方法，因此需要解析 Context 中的原生 Node .js 请求对象 req
2.2.5. 可以通过 koa-bodyparser 等中 间件来获取 POST 请求的参数， 而且更加方便。
2.3. 2.3.Koa的中间件
2.3.1. Koa 应用程序其实就是一个包含一组中间件函数的对象
2.3.2. 中间件函数是一个带有 ctx 和 next 两个参数的简单函数。
2.3.3. ctx 就是之前介绍的上下文，封装了 Request 和 Response 等对象；next 用于把中间件的执行权交给下游的中间件。
2.3.4. “洋葱模型”来解释中间件的执行顺序。先进后出的堆栈结构
2.3.5. 如果一个中间件没有调用 await next(),后面的中间件将不会被执行
2.3.6. 常用 Koa 中间件介绍：koa-bodyparser、koa-router、koa-static、koa-views
2.3.7. koa-static 是专门用于加载静态资源的中间件，通过它可以为页面请求加载 css 、 JavaScript 等静态资源，而 koa-views用于加载 HTML 模板文件 。
3. 第三章 路由
3.1. 3.1.路由介绍
3.1.1. Python官网的描述：路由（请求路由或 URL 分发）是匹配 URL 到相应处理程序的活 动）。
3.1.2. 通俗地说，路由是根据 URL 的变更重新渲染页面布局和内容的过程 。
3.1.3. 前端路由主要解决了两个问题：在页面不刷新的前提下实现 URL 的变化， 以及捕捉 U虹的变化并执行相应的页面逻辑。
3.2. 3.2.koa-router路由中间件
3.2.1. koa-router 具有丰富的 API ，可以实现命名参数、命名路由 、多路由中间件 、多路由、嵌套路由等功能。
3.2.2. koa-router 从 5.2.0 版本开始支持 ECMAScript 2016 的 async/await 语法糖。
3.2.3. REST 设计一般符合以下条件：1、程序或应用的事物都应该被抽象为资源；2、每个资源对应唯一的 URL；3、使用统一的接口对资源进行操作；4、对资源的各种操作不会改变资源标识；5、所有的操作都是无状态的 。
3.2.4. 在 HTTP 中，会被经常使用的方法有 POST 、 DELETE 、 PUT 、 GET，对应于增、删、改、查，即常说的 CRUD(Create 、 Retrieve、 Update 、 Delete ）操作。
3.2.5. 不得不提的是 GitHub v4 的 API 使用了全新的设计风格 GraphQL
3.2.6. 与嵌套路由不同的是，路由前缀是一个固定的字符串，不能添加动态参数
3.2.7. 常见鉴别用户权限的方式有两种， 一种是广泛使用的 Cookie-Based Authentication （基于 Cookie 的认证模式），另一种是 Token-Based Authentication （基于 Token 的认证模式） 。 
3.2.8.  Token 方式最大的优点在于采用了无状态机制 ，在此基础上，可以实现天然的跨域支持、前后端分离等，同时降低了服务端开发和维护的成本 。Token 方式的缺点在于服务器每次都需要对 Token 进行校验，这一步骤会对服务器产生运算压力 。
4. 第四章 HTTP
4.1. 4.1.HTTP介绍
4.1.1. HTTP 全称为 HyperText Transfer Protocol ，即超文本传输协议，是当今互联网使用最广泛的网络基础协议。
4.1.2. HTTP/ I.0 在 HTTP/0.9 的基础上做出了大量的改进，增加了访问不同对象类型的功能，不仅可以传输文本，还可以传输图像、视频、二进制文件等。同时，在 GET 请求命令的基础上，增加了 POST 、 PUT、 HEAD 、 DELETE 、LINK 等命令 。另外，还增加了头部信息，如 User-Agent 、 Accept 、 Last-Modified 、 Content-Type 等至今仍在使用的请求头字段。
4.1.3. HTTP/ 1.1 目前依旧被广泛地使用在互联网领域，其在 HTTP/1.0 的基础上又做了大量的改进
4.1.4. 2009 年， Goolge 公开了自己研发的 SPDY （单词 speedy 的缩写〉 协议，通过多路复用、压缩、优先级、安全等新技术方案，缩短了网页的加载时间，井提高了安全性 。IETF( The Internet Engineering Task Force,国际互联网工程任务组〉随后对 SPDY 进行了标准化， 并作为制定 HTTP/2 标准的起点 。
4.1.5. URI: Uniform Resource Identifier （统一资源标识符）；URL: Uniform Resource Locator （ 统一资源定位符〉
4.1.6. 一个完整的URL一般由 7 个部分组成：scheme: [//[user[:password]@]host[:port]][/path][?query][#fragment]
4.1.7. HTTP 状态码表示服务器响应状态的 3 位数字。 HTTP 状态码主要包括 1** （消息）、 2**（成功）、 3**（重定向）、 4**（请求错误〉、 5**和 6** （服务器错误）等 6 种不同类型。
4.1.8. 目前常用的 9 种 HTTP 请求：GET、POST、HEAD、PUT、DELETE、CONNECT、OPTIONS、TRACE、PATCH
4.1.9. 首部字段是构成 HTTP 的重要元素之一 ，用以提供 HTTP 传输过程中额外 的重要信息 。常见的首部字段：User-Agent、Last-Modified、Content-Length、Content-Encoding、Content-Type、Expires、Set-Cookies、Cookie、Cache-Control、ETag、Vary、Server
4.2. 4.2.HTTP/2
4.2.1. HTTP/2 在 HTTP/1.1 的基础上保持原有语义和功能不变，但极大地 提升了性能。
4.2.2. 采用二进制格式传输数据：之前的 HTTP/1.* 均采用文本格式传输数据，而 HTTP/2 则选择了使用二进制格式传输数据。
4.2.3. 在 HTTP/2 中，基本的协议单位是帧，每个数据流均以消息形式发送，消息由一个或 多个帧组合而成。帧的内容包括：长度（ Length ）、类型（ Type ）、标记（ Flags ）、保留字段 CR）、流标识符（ Stream Identifier）和帧主体（ Frame Payload ） 。
4.2.4. 多路复用：HTTP/2 重新定义了底层的 HTTP 语义映射，允许在同一个连接上使用请求和响应双向数据流
4.2.5. 流的优先级：在 HTTP/2 中可以为每个流（ Stream ）设置优先级，高优先级的流会被服务优先处理井返回给客户端
4.2.6. 首部压缩：HTTP/2 引入了 HPACK 压缩首部数据。 由于 HPACK 压缩引入了索引表概念，包含静态表和动态表 。
4.2.7. 服务端推送：例如，可以在请求该HTML 文档的同时， 一并推送与之关联的静态资源文件，达到性能优化的目的。
4.3. 4.3.Node.js的querystring模块
4.3.1. querystring 模块由 Node .js 原生提供，包含相关解析和格式化工具，共有 4 种方法：escape、unescape、parse、stringify
4.3.2. 通过 query 或 querystring 可以直接获取 GET 请求的数据，唯一不同的是 query 返回的是对象，而querystring 返回的 是查询字符串。
4.4. 4.4.koa-bodyparser中间件
4.4.1. 通过 POST 请求传递表单数据、上传数据文件、传递 JSON 格式的数据等。
4.4.2. koa-bodyparser 中间件用于解析请求的 Body，支持 JSON 、 Form 和 Text 类型 。
4.4.3. 解析后的数据会被存储在 ctx.request.body 中，如果没有数据则为空对象
5. 第五章 构建Koa Web应用
5.1. 5.1.MVC
5.1.1. MVC 模式的目的是实现动态的程序设计，简化程序后续 的修改和扩展过程，并且使模 块能够被重复利用。
5.1.2. 需要注意的是： MVC 不是一种技术，而是一种设计理念 。 
5.1.3. MVC 模式主要采用分层的思想来降低耦合度，从而使系统更 加灵活， 扩展性更强 。
5.1.4. MVC 模式在概念上强调 Model、View 和 Controller 的分离，模块间也遵循着由 Controller进行消息处理、 Model 进行数据源处理、View 进行数据显示的职责分离原则。
5.1.5. 3个部分分离实现：Model负责数据访问、Controller负责处理消息、View负责显示数据
5.1.6. 通常意义上的三层架构是将整个业务应用 划分为界面层（ User Interface Layer ）、业务逻辑层（ Business Logic Layer ）、数据访问层（ Data Access Layer ） 。微软推荐的分层式结构一般也分为三层，从下至上分别为数据访问层、业务逻辑层（又称领域层〉和表示层 。
5.1.7. 不管是 MVC 还是三层架构，其实设计理念都是一致的： 分层，解耦
5.2. 5.2.模板引擎
5.2.1. 模板引擎是 Web 应用中用来生成动态 HTML 的工具，负责将数据模型与 HTML 模板 结合（模板渲染），生成最终的 HTML 。
5.2.2. 模板引擎不属于特定技术领域，是为了使用户界面与业务数据（内容）分离而产生的，是跨领域跨平台的概念。
5.2.3. 几种类型：“置换型”、“解释型”、“编译型”
5.2.4. 可以在 Node.js 中应用且比较成熟的模板引擎有很多 ，例如 EJS 、 Jade （现己改 名为 Pug ） 、 Handlebars 、 Nunjucks 、 Swig 等。
5.2.5. 一般情况下，模板引 擎都需要具备这些功能：变量、逻辑表达式、循环、 layout、 include 、宏和扩展等。
5.2.6. 宏 ： 定义可复用的内容，类似于编程语言中的函数
5.3. 5.3.静态资源
5.3.1. koa-static 是官方提供的文件服务器中间件，依赖于另一款官方中间件 koa-send
5.3.2. 动态资源需要使用的系统开销大于静态资源 。
5.3.3. MIME Type 通常是通过 HTTP，由 Web 服务器告知浏览器的， 被定义在 Content-Type header 中 。 
5.4. 5.4.其他常用开发技巧
5.4.1.  HTTP 请求的整个过程中所传输的数据，本身没有任何特定的格式或形态，但客户端在接收数据时，会按照 MIME Type 指定的方式去处理 。
5.4.2. koa-multer 源于 Multer，并以中间件的形式对 Multer 进行包装，而 Multer 是一个基于 Busboy 模块（专门用于处理表单数据 的模块〕的 Node.js 中间件， 主要用于上传文件，处理 multipart/form-data 类型的表单数据。
5.4.3. 永远不要将 Multer 作为全局中间件使用，因为恶意用户可以上传文件到一个预料之外的路由 。 开发者应该只在自己需要处理上传文件的路由上使用 Multer。
6. 第六章 数据库
6.1. 6.1.数据库介绍
6.1.1. 数据库主要具备以下特点 ：数据共享；减少数据冗余度；数据独立；数据一致性和可维护性；故障恢复
6.1.2. 数据库一般采用索引来提升查询效率
6.1.3. 通过事务，也就是一组有序的数据库操作指令，进行“捆绑”执行，要么全部执行，要么全部不执行，从而保证了数据的一致性和完整性 。 
6.1.4. 关系型数据库一般通过 SQL (Structured Query Language ，结构化查询语言〉来操作数据库。代表：Oracle、SQL Server、MySql、MariaDB
6.1.5. 非关系型数据库一般不采用 SQL 作为查询语言，也经常避免使用类似 SQL 中的 JOIN 操作来关联多张数据表。代表：MongoDB、Memcached、Redis
6.2. 6.2.在Koa中应用MySQL数据库
6.2.1. ORM 的字面意思为对象关系映射，它提供了概念性的、易于理解的模型化数据的方法。
6.2.2. 在Node.js 中， 一般采用 Sequelize 这个 ORM 类库来操作数据库。
6.2.3. 可以直接定义数据模型来创建数据表，而不必去数据库中使用 SQL 脚本创建。
6.2.4.  Sequelize 通过 define 方法定义数据模型，通过访问模型提供的接口来查询和更新数据，避免开发者直接访问数据库
6.3. 6.3.在Koa中应用MongoDB数据库
6.3.1. MongoDB 是由 C＋＋编写的基于分布式文件存储的开源数据库
6.3.2. 开发Node.js应用时， 一般借助 Mongoose 类库来访问数据库
6.4. 6.4.在Koa中应用Redis数据库
6.4.1. Redis 可用作数据库、高速缓存和消息队列代理 。 Redis非常适合处理那些短时间内被高频访问但又不需要长期访问的简单数据存储
6.4.2. Redis 是一个开源、使用 ANSIC 语言编写 、 遵守 BSD ( Berkeley Software Distribution, 伯克利软件套件）协议、支持网络、可基于内存亦可持久化的日志型 Key-Value 数据库，并提供多种语言的 API。
6.4.3. 在 Redis 中，集合是通过哈希表实现的，所以添加、删除、查找的复杂度都 是 o(1)
6.4.4. GitHub 上开源的 Redis库有很多 ， 其中使用最广、最成熟的是 node_redis 库
6.4.5.  Session 中的数据一般都是短时间内高频访问的，需要保证性能，所以比 较好的方式是内存配合 Redis 做一个持久化。
6.4.6. 在 Koa 应用中可以使用 koa-session 中间件来操作 Session。
7. 第七章 单元测试
7.1. 所谓单元是指应用的最小可测试部件，通常是单个函数、过程或方法 。
7.2. 单元测试通常拥有如下优势：尽早发现问题并进行更正； 简化集成测试的复杂度；生成文档。
7.3. 两个概念：TDD是测试驱动开发、BDD是行为驱动开发
7.4. 7.1.Chai断言库
7.4.1. 所谓断言是一种放在程序中的逻辑判断，目的是检 测结果是否与开发者的预想一致。
7.4.2. Node.js 内置了断言库 Assert，但并不是一个真正的测试运行器
7.4.3. 单元测试的测试用例中推荐使用Chai
7.4.4. Chai 包含 3 个断言库，其中有 BDD 风格的 Expect/Should 和 TDD 风格的 Assert 。
7.4.5. 可以直接使用 assert(expression, message) PEI数来对应所有断言的情况
7.5. 7.2.Mocha框架
7.5.1. Mocha 是一个功能丰富且流行的 JavaScript 测试框架，支持回调函数、Promise 、 Async等。
7.5.2. Mocha 的关键词只有 describe 和 it 两个 
7.6. 7.3.SuperTest测试RESTful API
7.6.1. SuperTest 就是一个用来实现 Web 请求的库，是可以用来测试 HTTP 服务的工具。
7.6.2. SuperTest 也是对 SuperAgent 工具 的扩展，在支持所有 SuperAgent 的 API 基础上，提供了对请求结果的断言处理 。
7.7. 7.4.其他常用工具
7.7.1. Nock 提供给开发者一个模拟请求服务器响应的情况，而 Nye 则可以检查代码的测试覆盖情况。
7.7.2. 单元测试过程中， 一方面不一定能够调用这些 API 服务， 另一方面单元测试并不需要承担对第三方服务的测试。
7.7.3. Nock 就是一个模拟服务器响应的工具。Nock 会覆盖 Node.js 的 http.request 方法 ， 来伪造一个结果
7.7.4. 完成所有单元测试后，也可能存在测试用例不够完整或不能测试到所有的应测试代码的情况 。另一种情况是被测试的代码中存在一些“死”代码，即逻辑上不能被执行到的代码 。 
7.7.5.  4 个种类：语句覆盖率（ Stmts ）、分支覆盖率 （Branch）、函数覆盖率（ Funes ）、行覆盖率（ Lines ）
8. 第八章 优化与部署
8.1. 8.1.服务优化
8.1.1. 通过完整的日志记录，能够快速地定位、还原问题现场。
8.1.2. 根据日志的用途， 一般可以将日志分为访问日志和应用日志。
8.1.3. log4js 中的日志输出可以分为 7 个级别，日志级别由低到高：trace跟踪信息、debug调试信息、info非调试和跟踪信息、warn警告信息、error错误信息、fatal严重错误信息
8.1.4. 在项目开发中，一般会分为开发、测试、验证、线上等环境。
8.1.5. 除 try/catch 之外，也可以用另外一种方法解决： 使用 uncaughtException 。
8.1.6. 传递异常情况，常见的方式有 3 种，包括 throw 抛出、 callback 回调传递和通过 EventEmitter 触发 error 。
8.2. 8.2.部署
8.2.1. 进程管理器用于对应用状态进行管理，可以启动、暂停、重启或删 除应用进程，也可 以对进程进行监控，包括对进程错误的记录。
8.2.2. Docker 是一个开源的应用容器引擎，能够让应用程序部署在软件容器下，这个容器是 在 Linux 操作系统上的一个软件抽象层。
8.2.3. Travis CI 是一个免费的持续集成服务。持续集成是指在代码开发过程中经常性地集成 （ 通常在某个特定分支修改后 就触发〉。
8.2.4. 在持续集成环境中有两种自动部署方法： 一种是使用脚本登录对应的线上服务器，在己经设置好 Git 环境的服务器上获取代码，然后启动；另一种是在构建服务器上生成代码压缩包，利用 scp 传输到线上服务器，解压后启动
8.3. 8.3.服务监控
8.3.1. 一般来说，服务的性能分为两部分：服务的吞吐量和服务对资源的占用量。
8.3.2. Node.js 是基于 v8 引擎的 ， 在 JavaScript 中，内存采用堆的方式来分配，因 此 ， 可以根据堆的统计信息查看 Node. 月民务的内存使用情况。
8.3.3. 一般情况下， HTTP 服务采用 QPS（查询量/秒）和 TPS（事务/秒） 来衡量服务的性能
8.3.4.  一般数据通过 Kafka （消息队列）上报到 Influxdb （分布式时序数据库〉中存储，最后通过 Grafana （可视化图表〉展示出来。
8.3.5. 一个强大的开源日志管理系统 ELK （即 Elasticsearch Logstash Kibana ） 。
8.3.6. PM2 官方也提供了 一个服务--Keymetrics 来进行性能数据的分析和展示 。
