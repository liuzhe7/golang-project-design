
非编码类规范
开源规范
1. 选择开源协议
2. 开元规范特点
  a. 开源项目，应该有一个高的单元覆盖率。这样，一方面可以确保第三方开发者在开发完代码之后，能够很方便地对整个项目做详细的单元测试，另一方面也能保证提交代码的质量。
  b. 要确保整个代码库和提交记录中，不能出现内部 IP、内部域名、密码、密钥这类信息。否则，就会造成敏感信息外漏，可能会对我们的内部业务造成安全隐患。
  c. 当我们的开源项目被别的开发者提交 pull request、issue、评论时，要及时处理，一方面可以确保项目不断被更新，另一方面也可以激发其他开发者贡献代码的积极性。
  d. 好的开源项目，应该能够持续地更新功能，修复 Bug。对于一些已经结项、不维护的开源项目，需要及时地对项目进行归档，并在项目描述中加以说明。



文档规范
1. readme 规范

# 项目名称

<!-- 写一段简短的话描述项目 -->

## 功能特性

<!-- 描述该项目的核心功能点 -->

## 软件架构(可选)

<!-- 可以描述下项目的架构 -->

## 快速开始

### 依赖检查

<!-- 描述该项目的依赖，比如依赖的包、工具或者其他任何依赖项 -->

### 构建

<!-- 描述如何构建该项目 -->

### 运行

<!-- 描述如何运行该项目 -->

## 使用指南

<!-- 描述如何使用该项目 -->

## 如何贡献

<!-- 告诉其他开发者如果给该项目贡献源码 -->

## 社区(可选)

<!-- 如果有需要可以介绍一些社区相关的内容 -->

## 关于作者

<!-- 这里写上项目作者 -->

## 谁在用(可选)

<!-- 可以列出使用本项目的其他有影响力的项目，算是给项目打个广告吧 -->

## 许可证

<!-- 这里链接上该项目的开源许可证 -->
2. 项目文档

docs
├── devel                            # 开发文档，可以提前规划好，英文版文档和中文版文档
│   ├── en-US/                       # 英文版文档，可以根据需要组织文件结构
│   └── zh-CN                        # 中文版文档，可以根据需要组织文件结构
│       └── development.md           # 开发手册，可以说明如何编译、构建、运行项目
├── guide                            # 用户文档
│   ├── en-US/                       # 英文版文档，可以根据需要组织文件结构
│   └── zh-CN                        # 中文版文档，可以根据需要组织文件结构
│       ├── api/                     # API文档
│       ├── best-practice            # 最佳实践，存放一些比较重要的实践文章
│       │   └── authorization.md
│       ├── faq                      # 常见问题
│       │   ├── iam-apiserver
│       │   └── installation
│       ├── installation             # 安装文档
│       │   └── installation.md
│       ├── introduction/            # 产品介绍文档
│       ├── operation-guide          # 操作指南，里面可以根据RESTful资源再划分为更细的子目录，用来存放系统核心/全部功能的操作手册
│       │   ├── policy.md
│       │   ├── secret.md
│       │   └── user.md
│       ├── quickstart               # 快速入门
│       │   └── quickstart.md
│       ├── README.md                # 用户文档入口文件
│       └── sdk                      # SDK文档
│           └── golang.md
└── images                           # 图片存放目录
    └── 部署架构v1.png
3. API接口文档
  a. 接口文档拆分为以下几个 Markdown 文件，并存放在目录 docs/guide/zh-CN/api 中
    ⅰ. README.md ：API 接口介绍文档，会分类介绍 IAM 支持的 API 接口，并会存放相关 API 接口文档的链接，方便开发者查看。
    ⅱ. CHANGELOG.md ：API 接口文档变更历史，方便进行历史回溯，也可以使调用者决定是否进行功能更新和版本更新。
    ⅲ. generic.md ：用来说明通用的请求参数、返回参数、认证方法和请求方法等。
    ⅳ. struct.md ：用来列出接口文档中使用的数据结构。这些数据结构可能被多个 API 接口使用，会在 user.md、secret.md、policy.md 文件中被引用。
    ⅴ. user.md 、 secret.md 、 policy.md ：API 接口文档，相同 REST 资源的接口会存放在一个文件中，以 REST 资源名命名文档名。
    ⅵ. error_code.md ：错误码描述，通过程序自动生成。

版本规范
1. 语意化版本规范先行版本号和编译版本号只能是字母、数字，且不可以有空格。

2. 语意化版本控制规范
  a. 标记版本号的软件发行后，禁止改变该版本软件的内容，任何修改都必须以新版本发行。
  b. 主版本号为零（0.y.z）的软件处于开发初始阶段，一切都可能随时被改变，这样的公共 API 不应该被视为稳定版。1.0.0 的版本号被界定为第一个稳定版本，之后的所有版本号更新都基于该版本进行修改。
  c. 修订号 Z（x.y.Z | x > 0）必须在只做了向下兼容的修正时才递增，这里的修正其实就是 Bug 修复。
  d. 次版本号 Y（x.Y.z | x > 0）必须在有向下兼容的新功能出现时递增，在任何公共 API 的功能被标记为弃用时也必须递增，当有改进时也可以递增。其中可以包括修订级别的改变。每当次版本号递增时，修订号必须归零。
  e. 主版本号 X（X.y.z | X > 0）必须在有任何不兼容的修改被加入公共 API 时递增。其中可以包括次版本号及修订级别的改变。每当主版本号递增时，次版本号和修订号必须归零。

3. 如何确定版本号
  a. 第一，在实际开发的时候，我建议你使用 0.1.0 作为第一个开发版本号，并在后续的每次发行时递增次版本号。
  b. 第二，当我们的版本是一个稳定的版本，并且第一次对外发布时，版本号可以定为 1.0.0。
  c. 第三，当我们严格按照 Angular commit message 规范提交代码时，版本号可以这么来确定：
    ⅰ. fix 类型的 commit 可以将修订号 +1。
    ⅱ. feat 类型的 commit 可以将次版本号 +1。
    ⅲ. 带有 BREAKING CHANGE 的 commit 可以将主版本号 +1。

commit规范
1. Angular规范
  a. 在 Angular 规范中，Commit Message 包含三个部分，分别是 Header、Body 和 Footer，格式如下：

<type>[optional scope]: <description>
// 空行
[optional body]
// 空行
[optional footer(s)]

Header 是必需的，Body 和 Footer 可以省略。在以上规范中，必须用括号 () 括起来， <type>[<scope>] 后必
须紧跟冒号 ，冒号后必须紧跟空格，2 个空行也是必需的。
  b. Header
    ⅰ. Header 部分只有一行，包括三个字段：type（必选）、scope（可选）和 subject（必选）
      1. type
        a. 它用来说明 commit 的类型。为了方便记忆，我把这些类型做了归纳，它们主要可以归为 Development 和 Production 共两类。它们的含义是
          ⅰ. Development：这类修改一般是项目管理类的变更，不会影响最终用户和生产环境的代码，比如 CI 流程、构建方式等的修改。遇到这类修改，通常也意味着可以免测发布。
          ⅱ. Production：这类修改会影响最终的用户和生产环境的代码。所以对于这种改动，我们一定要慎重，并在提交前做好充分的测试。
          ⅲ. 
          ⅳ. 确定type的方式
      2. scope
        a. scope 是用来说明 commit 的影响范围的，它必须是名词。显然，不同项目会有不同的 scope。在项目初期，我们可以设置一些粒度比较大的 scope，比如可以按组件名或者功能来设置 scope；后续，如果项目有变动或者有新功能，我们可以再用追加的方式添加新的 scope。
      3. subject
        a. subject 是 commit 的简短描述，必须以动词开头、使用现在时。比如，我们可以用 change，却不能用 changed 或 changes，而且这个动词的第一个字母必须是小写。通过这个动词，我们可以明确地知道 commit 所执行的操作。此外我们还要注意，subject 的结尾不能加英文句号。
  c. Body
    ⅰ. Header 对 commit 做了高度概括，可以方便我们查看 Commit Message，是可选的。
    ⅱ. Body 部分可以分成多行，而且格式也比较自由。不过，和 Header 里的一样，它也要以动词开头，使用现在时。此外，它还必须要包括修改的动机，以及和跟上一版本相比的改动点。
  d. Footer
    ⅰ. Footer 部分不是必选的，可以根据需要来选择，主要用来说明本次 commit 导致的后果。在实际应用中，Footer 通常用来说明不兼容的改动和关闭的 Issue 列表，格式如下
      1. 不兼容的改动：如果当前代码跟上一个版本不兼容，需要在 Footer 部分，以 BREAKING CHANG: 开头，后面跟上不兼容改动的摘要。Footer 的其他部分需要说明变动的描述、变动的理由和迁移方法，例如

BREAKING CHANGE: isolate scope bindings definition has changed and
    the inject option for the directive controller injection was removed.

    To migrate the code follow the example below:

    Before:

    scope: {
      myAttr: 'attribute',
    }

    After:

    scope: {
      myAttr: '@',
    }
    The removed `inject` wasn't generaly useful for directives so there should be no code using it.
      2. 关闭的 Issue 列表：关闭的 Bug 需要在 Footer 部分新建一行，并以 Closes 开头列出，例如：Closes #123。如果关闭了多个 Issue，可以这样列出：Closes #123, #432, #886。例如
Closes #1137
2. 提交频率
  a. 只要我对项目进行了修改，一通过测试就立即 commit。比如修复完一个 bug、开发完一个小功能，或者开发完一个完整的功能，测试通过后就提交
  b. 代码下班前固定提交一次，并且要确保本地未提交的代码，延期不超过 1 天。
3. 合并提交
  a. 新的 commit 合并到主干时，只保留 2~3 个 commit 记录。可以利用git rebase
4. 规范自动化
  a. commitizen-go：使你进入交互模式，并根据提示生成 Commit Message，然后提交。


发布规范

编码类规范
目录规范
1. 设计原则
  a. 命名清晰：目录命名要清晰、简洁，不要太长，也不要太短，目录名要能清晰地表达出该目录实现的功能，并且目录名最好用单数。一方面是因为单数足以说明这个目录的功能，另一方面可以统一规范，避免单复混用的情况。
  b. 功能明确：一个目录所要实现的功能应该是明确的、并且在整个项目目录中具有很高的辨识度。也就是说，当需要新增一个功能时，我们能够非常清楚地知道把这个功能放在哪个目录下。
  c. 全面性：目录结构应该尽可能全面地包含研发过程中需要的功能，例如文档、脚本、源码管理、API 实现、工具、第三方包、测试、编译产物等。
  d. 可预测性：项目规模一定是从小到大的，所以一个好的目录结构应该能够在项目变大时，仍然保持之前的目录结构。
  e. 可扩展性：每个目录下存放了同类的功能，在项目变大时，这些目录应该可以存放更多同类功能。
2. 平铺目录：适用于go包
  a. 平铺方式就是在项目的根目录下存放项目的代码，整个目录结构看起来更像是一层的，这种方式在很多框架 / 库中存在，使用这种方式的好处是引用路径长度明显减少，比如github.com/golang/glog 

$ ls glog/
glog_file.go  glog.go  glog_test.go  LICENSE  README
3. 结构化目录结构：适用于go项目，分为三个部分 go应用，项目管理，文档。
  a. go应用：主要存放前后端代码
    ⅰ. /web：前端代码存放目录，主要用来存放 Web 静态资源，服务端模板和单页应用（SPAs）。
    ⅱ. /cmd：一个项目有很多组件，可以把组件 main 函数所在的文件夹统一放在/cmd 目录下。每个组件的目录名应该跟你期望的可执行文件名是一致的。这里要保证 /cmd/<组件名> 目录下不要存放太多的代码，如果你认为代码可以导入并在其他项目中使用，那么它应该位于 /pkg 目录中。如果代码不是可重用的，或者你不希望其他人重用它，请将该代码放到 /internal 目录中。
    ⅲ. /internal：存放私有应用和库代码。如果一些代码，你不希望在其他应用和库中被导入，可以将这部分代码放在/internal 目录下。在引入其它项目 internal 下的包时，Go 语言会在编译时报错
      1. /internal/apiserver：该目录中存放真实的应用代码。这些应用的共享代码存放在/internal/pkg 目录下。
        a. /internal/apiserver/api/v1：HTTP API 接口的具体实现，主要用来做 HTTP 请求的解包、参数校验、业务逻辑处理、返回。注意这里的业务逻辑处理应该是轻量级的，如果业务逻辑比较复杂，代码量比较多，建议放到 /internal/apiserver/service 目录下。该源码文件主要用来串流程。
        b. /internal/apiserver/options：应用的 command flag。
        c. /internal/apiserver/config：根据命令行参数创建应用配置
        d. /internal/apiserver/service：存放应用复杂业务处理代码。
        e. /internal/apiserver/store/mysql：一个应用可能要持久化的存储一些数据，这里主要存放跟数据库交互的代码，比如 Create、Update、Delete、Get、List 等。
      2. /internal/pkg：存放项目内可共享，项目外不共享的包。这些包提供了比较基础、通用的功能，例如工具、错误码、用户验证等功能。
        a. /internal/pkg/code：项目业务 Code 码。
        b. /internal/pkg/validation：一些通用的验证函数。
        c. /internal/pkg/middleware：HTTP 处理链。
      3. /internal/iamctl：对于一些大型项目，可能还会需要一个客户端工具。
    ⅳ. /pkg： 该目录中存放可以被外部应用使用的代码库，其他项目可以直接通过 import 导入这里的代码
    ⅴ. /vendor： 需要注意的是，如果是一个 Go 库，不要提交 vendor 依赖包。
    ⅵ. /third_party： 外部帮助工具，分支代码或其他第三方应用（例如 Swagger UI）。比如我们 fork 了一个第三方 go 包，并做了一些小的改动，我们可以放在目录 /third_party/forked 下。一方面可以很清楚的知道该包是 fork 第三方的，另一方面又能够方便地和 upstream 同步

    ⅶ. /test：用于存放其他外部测试应用和测试数据。
    ⅷ. /configs：这个目录用来配置文件模板或默认配置。例如，可以在这里存放 confd 或 consul-template 模板文件。这里有一点要注意，配置中不能携带敏感信息，这些敏感信息，我们可以用占位符来替代，例如username: ${CONFIG_USER_USERNAME}
    ⅸ. /deployments： 用来存放 Iaas、PaaS 系统和容器编排部署配置和模板（Docker-Compose，Kubernetes/Helm，Mesos，Terraform，Bosh）。在一些项目，特别是用 Kubernetes 部署的项目中，这个目录可能命名为 deploy。
    X. /init：存放初始化系统（systemd，upstart，sysv）和进程管理配置文件（runit，supervisord）。比如 sysemd 的 unit 文件。这类文件，在非容器化部署的项目中会用到。
    Xⅰ. /Makefile：一个 Go 项目在其根目录下应该有一个 Makefile 工具，用来对项目进行管理，Makefile 通常用来执行静态代码检查、单元测试、编译等功能。
    Xⅱ. /scripts：该目录主要用来存放脚本文件，实现构建、安装、分析等不同功能。不同项目，里面可能存放不同的文件，但通常可以考虑包含以下 3 个目录：
      1. /scripts/make-rules：用来存放 makefile 文件，实现 /Makefile 文件中的各个功能。Makefile 有很多功能，为了保持它的简洁，我建议你将各个功能的具体实现放在/scripts/make-rules 文件夹下。
      2. /scripts/lib：shell 库，用来存放 shell 脚本。一个大型项目中有很多自动化任务，比如发布、更新文档、生成代码等，所以要写很多 shell 脚本，这些 shell 脚本会有一些通用功能，可以抽象成库，存放在/scripts/lib 目录下，比如 logging.sh，util.sh 等。
      3. /scripts/install：如果项目支持自动化部署，可以将自动化部署脚本放在此目录下。如果部署脚本简单，也可以直接放在 /scripts 目录下。
    Xⅲ. /build：这里存放安装包和持续集成相关的文件。这个目录下有 3 个大概率会使用到的目录，在设计目录结构时可以考虑进去。
      1. /build/package：存放容器（Docker）、系统（deb, rpm, pkg）的包配置和脚本。
      2. /build/ci：存放 CI（travis，circle，drone）的配置文件和脚本。
      3. /build/docker：存放子项目各个组件的 Dockerfile 文件。
    Xⅳ. /tools：存放这个项目的支持工具。这些工具可导入来自 /pkg 和 /internal 目录的代码。
    Xⅴ. /githooks：Git 钩子。比如，我们可以将 commit-msg 存放在该目录。
    Xⅵ. /assets：项目使用的其他资源 (图片、CSS、JavaScript 等)。
    Xⅶ. /website：如果你不使用 GitHub 页面，那么可以在这里放置项目网站相关的数据。
    Xⅷ. /README.md：项目的 README 文件一般包含了项目的介绍、功能、快速安装和使用指引、详细的文档链接以及开发指引等
    Xⅸ. /docs：详见非编码类规范.文档规范.项目文档
    XX. /CONTRIBUTING.md:如果是一个开源就绪的项目，最好还要有一个 CONTRIBUTING.md 文件，用来说明如何贡献代码，如何开源协同等等
    XXⅰ. /api:当前项目对外提供的各种不同类型的 API 接口定义文件，其中可能包含类似 /api/protobuf-spec、/api/thrift-spec、/api/http-spec、openapi、swagger 的目录，这些目录包含了当前项目对外提供和依赖的所有 API 文件
    XXⅱ. /LICENSE:版权文件
    XXⅲ. /CHANGELOG：当项目有更新时，为了方便了解当前版本的更新内容或者历史更新内容，需要将更新记录存放到 CHANGELOG 目录。编写 CHANGELOG 是一个复杂、繁琐的工作，我们可以结合 Angular 规范 和 git-chglog 来自动生成 CHANGELOG。
    XXⅳ. /examples：存放应用程序或者公共包的示例代码


4. 不建议的目录：
  a. /src：在默认情况下，Go 语言的项目都会被放置到$GOPATH/src 目录下。这个目录中存放着所有代码，如果我们在自己的项目中使用/src 目录，这个包的导入路径中就会出现两个 src
  b. /model：在 Go 项目里，不建议将类型定义统一存放在 model 目录中，这样做一方面不符合 Go 按功能拆分的设计哲学。另一方面，别人在阅读代码时，可能不知道这些类型在哪里使用，修改了结构体，也不知道有多大影响。建议将类型定义放在它被使用的模块中
  c. xxs/：在 Go 项目中，要避免使用带复数的目录或者包。建议统一使用单数
5. 其他建议：
  a. 对于小型项目，可以考虑先包含 cmd、pkg、internal 3 个目录，其他目录后面按需创建
  b. 在设计目录结构时，一些空目录无法提交到 Git 仓库中，但我们又想将这个空目录上传到 Git 仓库中，以保留目录结构。这时候，可以在空目录下加一个 .keep 文件。

代码规范
1. 格式化：
  a. 使用go fmt进行格式化
  b. 运算符和操作数之间要留空格。
  c. 建议一行代码不超过 120 个字符，超过部分，请采用合适的换行方式换行。但也有些例外场景，例如 import 行、工具自动生成的代码、带 tag 的 struct 字段。
  d. 文件长度不能超过 800 行。
  e. 函数长度不能超过 80 行。
  f. 代码都必须用 goimports 进行格式化（建议将代码 Go 代码编辑器设置为：保存时运行 goimports）。
  g. 不要使用相对路径引入包，例如 import ../util/net 。
2. 注释：
  a. 每个包都应包含一段包注释，即放置在包子句前的一个块注释,即放置在包子句前的一个块注释。对于包含多个文件的包， 包注释只需出现在其中的任一文件中即可。包注释应在整体上对该包进行介绍，并提供包的相关信息。 它将出现在 godoc 页面中的最上面，并为紧随其后的内容建立详细的文档。
  b. 在包中，任何顶级声明前面的注释都将作为该声明的文档注释。 在程序中，每个可导出（首字母大写）的名称都应该有文档注释。
  c. 所有注释掉的代码在提交 code review 前都应该被删除，否则应该说明为什么不删除，并给出后续处理建议。
3. 初始化:
  a. 在初始化结构引用时，请使用 &T{}代替 new(T)，以使其与结构体初始化一致
4. 错误:
  a. 错误描述:
    ⅰ. 告诉用户他们可以做什么，而不是告诉他们不能做什么
    ⅱ. 当声明一个需求时，用 must 而不是 should。例如，must be greater than 0、must match regex '[a-z]+'。
    ⅲ. 当声明一个格式不对时，用 must not。例如，must not contain。
    ⅳ. 当声明一个动作时用 may not。例如，may not be specified when otherField is empty、only name may be specified。
    ⅴ. 引用文字字符串值时，请在单引号中指示文字。例如，ust not contain '..'。
    ⅵ. 当引用另一个字段名称时，请在反引号中指定该名称。例如，must be greater than request。
    ⅶ. 指定不等时，请使用单词而不是符号。例如，must be less than 256、must be greater than or equal to 0 (不要用 larger than、bigger than、more than、higher than)。
    ⅷ. 指定数字范围时，请尽可能使用包含范围。
    ⅸ. 建议 Go 1.13 以上，error 生成方式为 fmt.Errorf("module xxx: %w", err)。
    X. 错误描述用小写字母开头，结尾不要加标点符号，例如：
  b. error作为函数的值返回，必须对error进行处理，或将返回值赋值给明确忽略。对于defer xx.Close()可以不用显式处理。
  c. error作为函数的值返回且有多个返回值的时候，error必须是最后一个参数。
  d. 尽早进行错误处理，并尽早返回，减少嵌套。

// bad
if err != nil {
  // error code
} else {
  // normal code
}

// good
if err != nil {
  // error handling
  return err
}
// normal code
  e. 错误要单独判断，不与其他逻辑组合判断

// bad
v, err := foo()
if err != nil || v  == nil {
  // error handling
  return err
}

// good
v, err := foo()
if err != nil {
  // error handling
  return err
}

if v == nil {
  // error handling
  return errors.New("invalid value v")
}
5. panic:
  a. 在业务逻辑处理中禁止使用 panic
  b. 在 main 包中，只有当程序完全不可运行时使用 panic，例如无法打开文件、无法连接数据库导致程序无法正常运行。
  c. 在 main 包中，使用 log.Fatal 来记录错误，这样就可以由 log 来结束程序，或者将 panic 抛出的异常记录到日志文件中，方便排查问题。
  d. 可导出的接口一定不能有 panic。
6. 命名规则：
  a. 包名
    ⅰ. 包应当以小写的单个单词来命名，且不应使用下划线或驼峰记法，例如，bufio 包中的缓存读取器类型叫做 Reader 而非 BufReader。
    ⅱ. 用于创建 ring.Ring 的新实例的函数（这就是 Go 中的构造函数）一般会称之为 NewRing，但由于 Ring 是该包所导出的唯一类型，且该包也叫 ring，因此它可以只叫做 New，它跟在包的后面，就像 ring.New
    ⅲ. 避免在导入路径中包含 src/、pkg/ 部分。
    ⅳ. 重命名应遵循相同的规则。
    ⅴ. godoc 总是以“Package {pkgname}”开头，然后是描述。对于主包，文档应该解释二进制文件。
  b. 获取器：
    ⅰ. 获取器当中不应该用Get
    ⅱ. 设置器当中应该用Set
owner := obj.Owner()
if owner != user {
    obj.SetOwner(user)
}
  c. 接口命名：
    ⅰ. 只包含一个方法的接口应当以该方法的名称加上 - er 后缀来命名，如 Reader、Writer、 Formatter、CloseNotifier 等。
    ⅱ. 若你的类型实现了的方法， 与一个众所周知的类型的方法拥有相同的含义，那就使用相同的命名。 请将字符串转换方法命名为 String 而非 ToString
  d. 驼峰命名
    ⅰ. Go 中的约定是使用 MixedCaps 或 mixedCaps 而不是下划线来编写多个单词组成的命名。
  e. 结构体
    ⅰ. 结构体名不应该是动词，应该是名词，比如 Node、NodeSpec。
    ⅱ. 避免使用 Data、Info 这类无意义的结构体名。
  f. error
    ⅰ. Error 类型应该写成 FooError 的形式。
    ⅱ. Error 变量写成 ErrFoo 的形式。
7. 函数：
  a. 尽量使用命名结果参数，由于被命名的结果已经初始化，且已经关联至无参数的返回，它们就能让代码简单而清晰。
func ReadFull(r Reader, buf []byte) (n int, err error) {
    for len(buf) > 0 && err == nil {
        var nr int
        nr, err = r.Read(buf)
        n += nr
        buf = buf[nr:]
    }
    return
}
8. 数据：
  a. 使用构造函数和复合字面量：
// 冗余的方式
func NewFile(fd int, name string) *File {
    if fd < 0 {
        return nil
    }
    f := new(File)
    f.fd = fd
    f.name = name
    f.dirinfo = nil
    f.nepipe = 0
    return f
}
// 使用字面量
func NewFile(fd int, name string) *File {
    if fd < 0 {
        return nil
    }
    f := File{fd, name, nil, 0}
    return &f
}
// 最佳方式（每当获取一个复合字面的地址时，都将为一个新的实例分配内存）
func NewFile(fd int, name string) *File {
    if fd < 0 {
        return nil
    }
    return &File{fd, name, nil, 0}
}
  b. 数组：
    ⅰ.   数组是值。将一个数组赋予另一个数组会复制其所有元素
    ⅱ. 若将某个数组传入某个函数，它将接收到该数组的一份副本而非指针。
    ⅲ. 大小是类型的一部分
  c. 切片
    ⅰ. 在for-loop里对某个slice 使用 append()请先把 slice的容量很扩充到位，这样可以避免内存重新分享以及系统自动按2的N次方幂进行扩展但又用不到，从而浪费内存。
  d. 映射
    ⅰ. 若仅需判断映射中是否存在某项而不关心实际的值，可使用空白标识符 （_）来代替该值的一般变量。
    ⅱ. 使用map的时候，使用整型的key会比字符串的要快，因为整型比较比字符串比较要快。
  e. 字符串
    ⅰ. 数字转字符串，使用 strconv.Itoa() 会比 fmt.Sprintf() 要快一倍左右
    ⅱ. 避免把String转成[]Byte 。这个转换会导致性能下降。
    ⅲ. StringBuffer 或是StringBuild 来拼接字符串，会比使用 + 或 += 性能高三到四个数量级。
    ⅳ. 
9. 方法
  a. 尝试去满足标准接口例如 append方法
func (p *ByteSlice) Append(data []byte) {
    slice := *p
    // 主体同上，只是没有返回值
    *p = slice
}
// 改造后,实现io.writer接口
func (p *ByteSlice) Write(data []byte) (n int, err error) {
    slice := *p
    // 同上。
    *p = slice
    return len(data), nil
}


10. 其他语言的常见做法是将类型组织在一个称为模型或类型的包中。在 Go 中，我们按功能职责组织代码。
11. 将核心类型分组在文件顶部通常是一种很好的做法。
12. 零值的mutex是有效的
//bad
mu := new(sync.Mutex)
mu.Lock()

//good
var mu sync.Mutex
mu.Lock()

13. channel的要么是无缓冲的，要么长度是1， 足以应对绝大多数场景。
14. 断言
//bad
t := i.(string)

//good
t, ok := i.(string)
if !ok {
  // 优雅地处理错误
}

15. 避免把公共结构体嵌入到别的结构体
//bad
// ConcreteList 是一个实体列表。
type ConcreteList struct {
  *AbstractList
}

//good
// ConcreteList 是一个实体列表。
type ConcreteList struct {
  list *AbstractList
}
// 添加将实体添加到列表中。
func (l *ConcreteList) Add(e Entity) {
  l.list.Add(e)
}
// 移除从列表中移除实体。
func (l *ConcreteList) Remove(e Entity) {
  l.list.Remove(e)
}

16. 导入应该分为两组，标准库，其他库
//bad
import (
  "fmt"
  "os"
  "go.uber.org/atomic"
  "golang.org/x/sync/errgroup"
)

//good
import (
  "fmt"
  "os"

  "go.uber.org/atomic"
  "golang.org/x/sync/errgroup"
)

17. 未导出的顶层常量和变量用_开头
//good
// foo.go

const (
  _defaultPort = 8080
  _defaultUser = "user"
)

18. 缩小变量作用域
//bad
err := ioutil.WriteFile(name, data, 0644)
if err != nil {
 return err
}

//good
if err := ioutil.WriteFile(name, data, 0644); err != nil {
 return err
}
19. 参数语义不明显时，应添加注释
//bad
// func printInfo(name string, isLocal, done bool)

printInfo("foo", true, true)

//good
// func printInfo(name string, isLocal, done bool)

printInfo("foo", true /* isLocal */, true /* done */)

20. 对零值结构使用var
//bad
user := User{}

//good
var user User

21. Printf-style 函数的格式字符串，请将其设置为const常量。
//bad
msg := "unexpected values %v, %v\n"
fmt.Printf(msg, 1, 2)
//good
const msg = "unexpected values %v, %v\n"
fmt.Printf(msg, 1, 2)


22. 使用 Go Modules 作为依赖管理的项目时，不建议提交 vendor 目录。
23. 使用 Go Modules 作为依赖管理的项目时，必须提交 go.sum 文件。

代码质量
1. 单元测试
  a. 标准：进行单元测试，不仅需要编写单元测试用例，还需要我们确保代码是可测试的，以及具有一个高的单元测试覆盖率，常见的无法进行单元测试的情况有以下两种。
    ⅰ. 可能无法连接数据库
    ⅱ. 可能无法访问第三方服务
  b. 解决方案：将依赖的数据库、第三方服务等抽象成接口，在被测代码中调用接口的方法，在测试时传入 mock 类型，从而将数据库、第三方服务等依赖从具体的被测函数中解耦出去
//bad

package post

import "google.golang.org/grpc"

type Post struct {
  Name    string
  Address string
}
// listposts方法无法测试，因为需要连接第三方服务
func ListPosts(client *grpc.ClientConn) ([]*Post, error) {
  return client.ListPosts()
}
---
//good

package main

type Post struct {
  Name    string
  Address string
}

type Service interface {
  ListPosts() ([]*Post, error)
}

func ListPosts(svc Service) ([]*Post, error) {
  return svc.ListPosts()
}
---

package main

import "testing"

type fakeService struct {
}

func NewFakeService() Service {
  return &fakeService{}
}

func (s *fakeService) ListPosts() ([]*Post, error) {
  posts := make([]*Post, 0)
  posts = append(posts, &Post{
    Name:    "colin",
    Address: "Shenzhen",
  })
  posts = append(posts, &Post{
    Name:    "alex",
    Address: "Beijing",
  })
  return posts, nil
}

func TestListPosts(t *testing.T) {
  fake := NewFakeService()
  if _, err := ListPosts(fake); err != nil {
    t.Fatal("list posts failed")
  }
}
2. 单元测试覆盖率
  a. 使用 gotests 工具自动生成单元测试代码，减少编写单元测试用例的工作量，将你从重复的劳动中解放出来
gotests --all  -w main.go ,main_test.go
  b. 定期检查单元测试覆盖率。你可以通过以下方法来检查：

$ go test -race -cover  -coverprofile=./coverage.out -timeout=10m -short -v ./...
$ go tool cover -func ./coverage.out

编程哲学
1. 面向接口编程：接口的作用，其实就是为不同层级的模块提供一个定义好的中间层。这样，上游不再需要依赖下游的具体实现，充分地对上下游进行了解耦

package main

import "fmt"

// 定义了一个鸟类
type Bird interface {
  Fly()
  Type() string
}

// 鸟类：金丝雀
type Canary struct {
  Name string
}

func (c *Canary) Fly() {
  fmt.Printf("我是%s，用黄色的翅膀飞\n", c.Name)
}
func (c *Canary) Type() string {
  return c.Name
}

// 鸟类：乌鸦
type Crow struct {
  Name string
}

func (c *Crow) Fly() {
  fmt.Printf("我是%s，我用黑色的翅膀飞\n", c.Name)
}

func (c *Crow) Type() string {
  return c.Name
}

// 让鸟类飞一下
func LetItFly(bird Bird) {
  fmt.Printf("Let %s Fly!\n", bird.Type())
  bird.Fly()
}

func main() {
  LetItFly(&Canary{"金丝雀"})
  LetItFly(&Crow{"乌鸦"})
}
  a. 代码扩展性更强了。例如，同样的 Bird，可以有不同的实现。在开发中用的更多的是，将数据库的 CURD 操作抽象成接口，从而可以实现同一份代码对接不同数据库的目的。
  b. 可以解耦上下游的实现。例如，LetItFly 不用关注 Bird 是如何 Fly 的，只需要调用 Bird 提供的方法即可。提高了代码的可测性。
  c. 因为接口可以解耦上下游实现，我们在单元测试需要依赖第三方系统 / 数据库的代码时，可以利用接口将具体实现解耦，实现 fake 类型。
  d. 代码更健壮、更稳定了。例如，如果要更改 Fly 的方式，只需要更改相关类型的 Fly 方法即可，完全影响不到 LetItFly 函数。

2. 面向对象编程: go不支持面向对象，但可以模拟

package main

import "fmt"

// 基类：Bird
type Bird struct {
  Type string
}

// 鸟的类别
func (bird *Bird) Class() string {
  return bird.Type
}

// 定义了一个鸟类
type Birds interface {
  Name() string
  Class() string
}

// 鸟类：金丝雀
type Canary struct {
  Bird
  name string
}

func (c *Canary) Name() string {
  return c.name
}

// 鸟类：乌鸦
type Crow struct {
  Bird
  name string
}

func (c *Crow) Name() string {
  return c.name
}

func NewCrow(name string) *Crow {
  return &Crow{
    Bird: Bird{
      Type: "Crow",
    },
    name: name,
  }
}

func NewCanary(name string) *Canary {
  return &Canary{
    Bird: Bird{
      Type: "Canary",
    },
    name: name,
  }
}

func BirdInfo(birds Birds) {
  fmt.Printf("I'm %s, I belong to %s bird class!\n", birds.Name(), birds.Class())
}

func main() {
    canary := NewCanary("CanaryA")
    crow := NewCrow("CrowA")
  BirdInfo(canary)
  BirdInfo(crow)
}

软件设计
  a. solid原则go实践
  b. go编程模式
  c. 设计模式分类及举例
    ⅰ. 创建型模式
      1. 单例模式
        a. 饿汉方式：包引入时就创建

package singleton

type singleton struct {
}

var ins *singleton = &singleton{}

func GetInsOr() *singleton {
    return ins
}
        b. 懒汉方式：第一次用到时创建

package singleton

import (
    "sync"
)

type singleton struct {
}

var ins *singleton
var once sync.Once

func GetInsOr() *singleton {
    once.Do(func() {
        ins = &singleton{}
    })
    return ins
}
      2. 工厂模式
        a. 简单工厂

type Person struct {
  Name string
  Age int
}

func (p Person) Greet() {
  fmt.Printf("Hi! My name is %s", p.Name)
}

func NewPerson(name string, age int) *Person {
  return &Person{
    Name: name,
    Age: age
  }
}
        b. 抽象工厂：在你不公开内部实现的情况下，让调用者使用你提供的各种功能

type Person interface {
  Greet()
}

type person struct {
  name string
  age int
}

func (p person) Greet() {
  fmt.Printf("Hi! My name is %s", p.name)
}

// Here, NewPerson returns an interface, and not the person struct itself
func NewPerson(name string, age int) Person {
  return person{
    name: name,
    age: age
  }
}
        c. 工厂方法：返回工厂函数，固定住一些默认值

type Person struct {
  name string
  age int
}

func NewPersonFactory(age int) func(name string) Person {
  return func(name string) Person {
    return Person{
      name: name,
      age: age,
    }
  }
}

newBaby := NewPersonFactory(1)
baby := newBaby("john")

newTeenager := NewPersonFactory(16)
teen := newTeenager("jill")
    ⅱ. 结构型模式
      1. 策略模式：定义一组算法，将每个算法都封装起来，并且使它们之间可以互换。在项目开发中，我们经常要根据不同的场景，采取不同的措施，也就是不同的策略。比如，假设我们需要对 a、b 这两个整数进行计算，根据条件的不同，需要执行不同的计算方式。我们可以把所有的操作都封装在同一个函数中，然后通过 if ... else ... 的形式来调用不同的计算方式，这种方式称之为硬编码。

package strategy

// 策略模式

// 定义一个策略类
type IStrategy interface {
  do(int, int) int
}

// 策略实现：加
type add struct{}

func (*add) do(a, b int) int {
  return a + b
}

// 策略实现：减
type reduce struct{}

func (*reduce) do(a, b int) int {
  return a - b
}

// 具体策略的执行者
type Operator struct {
  strategy IStrategy
}

// 设置策略
func (operator *Operator) setStrategy(strategy IStrategy) {
  operator.strategy = strategy
}

// 调用策略中的方法
func (operator *Operator) calculate(a, b int) int {
  return operator.strategy.do(a, b)
}

func TestStrategy(t *testing.T) {
  operator := Operator{}

  operator.setStrategy(&add{})
  result := operator.calculate(1, 2)
  fmt.Println("add:", result)

  operator.setStrategy(&reduce{})
  result = operator.calculate(2, 1)
  fmt.Println("reduce:", result)
}
      2. 模板模式：模版模式 (Template Pattern) 定义一个操作中算法的骨架，而将一些步骤延迟到子类中。这种方法让子类在不改变一个算法结构的情况下，就能重新定义该算法的某些特定步骤。简单来说，模板模式就是将一个类中能够公共使用的方法放置在抽象类中实现，将不能公共使用的方法作为抽象方法，强制子类去实现，这样就做到了将一个类作为一个模板，让开发者去填充需要填充的地方。

package template

import "fmt"

type Cooker interface {
  fire()
  cooke()
  outfire()
}

// 类似于一个抽象类
type CookMenu struct {
}

func (CookMenu) fire() {
  fmt.Println("开火")
}

// 做菜，交给具体的子类实现
func (CookMenu) cooke() {
}

func (CookMenu) outfire() {
  fmt.Println("关火")
}

// 封装具体步骤
func doCook(cook Cooker) {
  cook.fire()
  cook.cooke()
  cook.outfire()
}

type XiHongShi struct {
  CookMenu
}

func (*XiHongShi) cooke() {
  fmt.Println("做西红柿")
}

type ChaoJiDan struct {
  CookMenu
}

func (ChaoJiDan) cooke() {
  fmt.Println("做炒鸡蛋")
}

func TestTemplate(t *testing.T) {
  // 做西红柿
  xihongshi := &XiHongShi{}
  doCook(xihongshi)

  fmt.Println("\n=====> 做另外一道菜")
  // 做炒鸡蛋
  chaojidan := &ChaoJiDan{}
  doCook(chaojidan)

}
    ⅲ. 行为型模式
      1. 代理模式：可以为另一个对象提供一个替身或者占位符，以控制对这个对象的访问。

package proxy

import "fmt"

type Seller interface {
  sell(name string)
}

// 火车站
type Station struct {
  stock int //库存
}

func (station *Station) sell(name string) {
  if station.stock > 0 {
    station.stock--
    fmt.Printf("代理点中：%s买了一张票,剩余：%d \n", name, station.stock)
  } else {
    fmt.Println("票已售空")
  }

}

// 火车代理点
type StationProxy struct {
  station *Station // 持有一个火车站对象
}

func (proxy *StationProxy) sell(name string) {
  if proxy.station.stock > 0 {
    proxy.station.stock--
    fmt.Printf("代理点中：%s买了一张票,剩余：%d \n", name, proxy.station.stock)
  } else {
    fmt.Println("票已售空")
  }
}
//StationProxy 代理了 Station，
      2. 选项模式：创建属性比较多，可以有很多默认值时使用

package options

import (
  "time"
)

type Connection struct {
  addr    string
  cache   bool
  timeout time.Duration
}

const (
  defaultTimeout = 10
  defaultCaching = false
)

type options struct {
  timeout time.Duration
  caching bool
}

// Option overrides behavior of Connect.
type Option interface {
  apply(*options)
}

type optionFunc func(*options)

func (f optionFunc) apply(o *options) {
  f(o)
}

func WithTimeout(t time.Duration) Option {
  return optionFunc(func(o *options) {
    o.timeout = t
  })
}

func WithCaching(cache bool) Option {
  return optionFunc(func(o *options) {
    o.caching = cache
  })
}

// Connect creates a connection.
func NewConnect(addr string, opts ...Option) (*Connection, error) {
  options := options{
    timeout: defaultTimeout,
    caching: defaultCaching,
  }
 // 在这里修改默认值
  for _, o := range opts {
    o.apply(&options)
  }

  return &Connection{
    addr:    addr,
    cache:   options.caching,
    timeout: options.timeout,
  }, nil
}

接口规范
1. RESTful API：REST 规范把所有内容都视为资源，也就是说网络上一切皆资源
  a. 核心规范
    ⅰ. 以资源 (resource) 为中心，所有的东西都抽象成资源，所有的行为都应该是在资源上的 CRUD 操作。
      1. 资源对应着面向对象范式里的对象，面向对象范式以对象为中心。
      2. 资源使用 URI 标识，每个资源实例都有一个唯一的 URI 标识。例如，如果我们有一个用户，用户名是 admin，那么它的 URI 标识就可以是 /users/admin。
    ⅱ. 资源是有状态的，使用 JSON/XML 等在 HTTP Body 里表征资源的状态。
    ⅲ. 无状态，这里的无状态是指每个 RESTful API 请求都包含了所有足够完成本次操作的信息，服务器端无须保持 session。无状态对于服务端的弹性扩容是很重要的。
  b. 具体规范
    ⅰ. 资源名使用名词而不是动词，并且用名词复数表示。资源分为 Collection 和 Member 两种。
      1. Collection：一堆资源的集合。例如我们系统里有很多用户（User）, 这些用户的集合就是 Collection。Collection 的 URI 标识应该是 域名/资源名复数, 例如https:// iam.api.marmotedu.com/users。
      2. Member：单个特定资源。例如系统中特定名字的用户，就是 Collection 里的一个 Member。Member 的 URI 标识应该是 域名/资源名复数/资源名称, 例如https:// iam.api.marmotedu/users/admin。
    ⅱ. URI 结尾不应包含/
    ⅲ. URI 中不能出现下划线 _，必须用中杠线 -代替（有些人推荐用 _，有些人推荐用 -，统一使用一种格式即可，我比较推荐用 -）。
    ⅳ. URI 路径用小写，不要用大写
    ⅴ. 避免层级过深的 URI。超过 2 层的资源嵌套会很乱，建议将其他资源转化为?参数，比如：

/schools/tsinghua/classes/rooma/students/zhang # 不推荐
/students?school=qinghua&class=rooma # 推荐
    ⅵ. 在实际的 API 开发中，可能你会发现有些操作不能很好地映射为一个 REST 资源，这时候，你可以参考下面的做法。
      1. 将一个操作变成资源的一个属性，比如想在系统中暂时禁用某个用户，可以这么设计 URI：/users/zhangsan?active=false。
      2. 将操作当作是一个资源的嵌套资源，比如一个 GitHub 的加星操作：

PUT /gists/:id/star # github star action
DELETE /gists/:id/star # github unstar action
      3. 如果以上都不能解决问题，有时可以打破这类规范。比如登录操作，登录不属于任何一个资源，URI 可以设计为：/login。
  c. REST 资源操作映射为 HTTP 方法
    ⅰ. 
    ⅱ. 
    ⅲ. 在使用 HTTP 方法的时候，有以下点需要你注意
      1. GET 返回的结果，要尽量可用于 PUT、POST 操作中。例如，用 GET 方法获得了一个 user 的信息，调用者修改 user 的邮件，然后将此结果再用 PUT 方法更新。这要求 GET、PUT、POST 操作的资源属性是一致的。
      2. 如果对资源进行状态 / 属性变更，要用 PUT 方法，POST 方法仅用来创建或者批量删除这两种场景
      3. 操作路径中带多个 id，id 之间用分隔符分隔, 例如：DELETE /users?ids=1,2,3 。
  d. 返回格式
    ⅰ. 一般来说，一个系统的 RESTful API 会向外界开放多个资源的接口，每个接口的返回格式要保持一致。另外，每个接口都会返回成功和失败两种消息，这两种消息的格式也要保持一致。不然，客户端代码要适配不同接口的返回格式，每个返回格式又要适配成功和失败两种消息格式，会大大增加用户的学习和使用成本
  e. 版本管理
    ⅰ. URL 中，比如/v1/users。
    ⅱ. HTTP Header 中，比如Accept: vnd.example-com.foo+json; version=1.0。
    ⅲ. Form 参数中，比如/users?version=v1。
  f. 命名
    ⅰ. API 通常的命名方式有三种，分别是驼峰命名法 (serverAddress)、蛇形命名法 (server_address) 和脊柱命名法 (server-address)。
    ⅱ. 驼峰命名法和蛇形命名法都需要切换输入法，会增加操作的复杂性，也容易出错，所以这里建议用脊柱命名法。GitHub API 用的就是脊柱命名法，例如 selected-actions。
  g. 统一分页 / 过滤 / 排序 / 搜索功能
    ⅰ. 分页：在列出一个 Collection 下所有的 Member 时，应该提供分页功能，例如/users?offset=0&limit=20（limit，指定返回记录的数量；offset，指定返回记录的开始位置）。引入分页功能可以减少 API 响应的延时，同时可以避免返回太多条目，导致服务器 / 客户端响应特别慢，甚至导致服务器 / 客户端 crash 的情况。
    ⅱ. 过滤：如果用户不需要一个资源的全部状态属性，可以在 URI 参数里指定返回哪些属性，例如/users?fields=email,username,address。
    ⅲ. 排序：用户很多时候会根据创建时间或者其他因素，列出一个 Collection 中前 100 个 Member，这时可以在 URI 参数中指明排序参数，例如/users?sort=age,desc。
    ⅳ. 搜索：当一个资源的 Member 太多时，用户可能想通过搜索，快速找到所需要的 Member，或着想搜下有没有名字为 xxx 的某类资源，这时候就需要提供搜索功能。搜索建议按模糊匹配来搜索。
2. RPC API

项目管理
1. makefile
  a. 引入makefile

include scripts/make-rules/common.mk
include scripts/make-rules/golang.mk
  b. 核心语法
    ⅰ. 规则：一般由目标、依赖和命令组成，用来指定源文件编译的先后顺序

target ...: prerequisites ...
    command
    ...
    ...
      1. target：可以是一个 object file（目标文件），也可以是一个执行文件，还可以是一个标签（label）。target 可使用通配符，当有多个目标时，目标之间用空格分隔。
      2. prerequisites：代表生成该 target 所需要的依赖项。当有多个依赖项时，依赖项之间用空格分隔。
      3. command：代表该 target 要执行的命令（可以是任意的 shell 命令）。
        a. 在执行 command 之前，默认会先打印出该命令，然后再输出命令的结果；如果不想打印出命令，可在各个 command 前加上@
        b. command 可以为多条，也可以分行写，但每行都要以 tab 键开始。另外，如果后一条命令依赖前一条命令，则这两条命令需要写在同一行，并用分号进行分隔。
        c. 如果要忽略命令的出错，需要在各个 command 之前加上减号-。
      4. 只要 targets 不存在，或 prerequisites 中有一个以上的文件比 targets 文件新，那么 command 所定义的命令就会被执行，从而产生我们需要的文件，或执行我们期望的操作。
    ⅱ. 伪目标：伪目标总是会被执行

.PHONY: clean
clean:
    rm hello.o
    ⅲ. order-only 依赖：只有当 prerequisites 中的部分文件改变时，才重新构造 target

targets : normal-prerequisites | order-only-prerequisites
    command
    ...
    ...
      1.  |  后面的prerequisites 只有第一次执行make的时候才被依赖
  c. 语法概览
    ⅰ. 命令：Makefile 支持 Linux 命令，调用方式跟在 Linux 系统下调用命令的方式基本一致。默认情况下，make 会把正在执行的命令输出到当前屏幕上。但我们可以通过在命令前加@符号的方式，禁止 make 输出当前正在执行的命令。
    ⅱ. 变量
      1. 变量赋值， 像shell一样展开
        a. = 最基本的赋值方法，最终值。
        b. :=直接赋值，赋予当前位置的值。
        c. ?= 表示如果该变量没有被赋值，则赋予等号后的值。
        d. +=表示将等号后面的值添加到前面的变量上。

GO=go
build:
    $(GO) build -v .
    
// 多行变量
define 变量名
变量内容
...
endef
      2. 环境变量
export CWR=666

      3. 特殊变量：make 提前定义好的，可以在 makefile 中直接引用

      4. 自动化变量
    ⅲ. 条件
      1. 基本结构

ifeq 条件表达式
...
else
...
endif
      2. 判断相等

ifeq (<arg1>, <arg2>)
ifeq '<arg1>' '<arg2>'
ifeq "<arg1>" "<arg2>"
ifeq "<arg1>" '<arg2>'
ifeq '<arg1>' "<arg2>"
      3. 判断不相等

ifneq (<arg1>, <arg2>)
ifneq '<arg1>' '<arg2>'
ifneq "<arg1>" "<arg2>"
ifneq "<arg1>" '<arg2>'
ifneq '<arg1>' "<arg2>"
      4. 判断已定义

ifdef <variable-name>
      5. 判断未定义

ifndef <variable-name>
    ⅳ. 函数
      1. 自定义函数
        a. 定义语法和多行变量相同，使用的时候加个call
      2. 预定义函数：调用方法$(<function> <arguments>)


define Foo
    @echo "my name is $(0)"
    @echo "param is $(1)"
endef
var := $(call Foo)
new := $(Foo)


  d. 功能规划
  e. 物理结构
2. 静态检查
  a. golangci-lint
    ⅰ. 安装
go get github.com/golangci/golangci-lint/cmd/golangci-lint@v1.41.1

    ⅱ. 配置：https://golangci-lint.run/usage/configuration/
    ⅲ. 检测：
golangci-lint run
3. swagger api文档
  a. go-swagger：swagger generate 命令会找到 main 函数，然后遍历所有源码文件，解析源码中与 Swagger 相关的注释，然后自动生成 swagger.json/swagger.yaml 文件。
    ⅰ. 安装
go get -u github.com/go-swagger/go-swagger/cmd/swagger
    ⅱ. 语法:https://goswagger.io/
    ⅲ. 使用

日志规范
1. 基础功能
  a. 基本日志信息
    ⅰ. 时间戳、文件名、行号、日志级别和日志信息
  b. 不同的日志级别
  c. 自定义配置
    ⅰ. 不同环境采用不同的配置。通过配置，可以在不重新编译代码的情况下，改变记录日志的行为。
  d. 支持标准输出和输出到文件
2. 高级功能
  a. 支持多种日志格式
    ⅰ. TEXT 格式：TEXT 格式的日志具有良好的可读性，可以方便我们在开发联调阶段查看日志，例如：
    ⅱ. JSON 格式：JSON 格式的日志可以记录更详细的信息，日志中包含一些通用的或自定义的字段，可供日后的查询、分析使用，而且可以很方便地供 filebeat、logstash 这类日志采集工具采集并上报。
  b. 能够按级别分类输出
  c. 支持结构化日志
  d. 支持日志轮转
  e. 支持hook能力
3. 可选功能
  a. 颜色
  b. 兼容标准log包
  c. 支持输出到不同位置

错误码规范
1. 错误码的功能
  a. 业务 Code 码标识
    ⅰ. 因为 HTTP Code 码有限，并且都是跟 HTTP Transport 层相关的 Code 码，所以我们希望能有自己的错误 Code 码。一方面，可以根据需要自行扩展，另一方面也能够精准地定位到具体是哪个错误。同时，因为 Code 码通常是对计算机友好的 10 进制整数，基于 Code 码，计算机也可以很方便地进行一些分支处理。当然了，业务码也要有一定规则，可以通过业务码迅速定位出是哪类错误。
  b. 考虑到安全，希望能够对外对内分别展示不同的错误信息。
    ⅰ. 当开发一个对外的系统，业务出错时，需要一些机制告诉用户出了什么错误，如果能够提供一些帮助文档会更好。但是，我们不可能把所有的错误都暴露给外部用户，这不仅没必要，也不安全。所以也需要能让我们获取到更详细的内部错误信息的机制，这些内部错误信息可能包含一些敏感的数据，不宜对外展示，但可以协助我们进行问题定位。
2. 错误码设计思路
  a. 有区别于http status code的业务码，业务码需要有一定规则，可以通过业务码判断出是哪类错误。
  b. 请求出错时，可以通过http status code直接感知到请求出错
  c. 需要在请求出错时，返回详细的信息，通常包括 3 类信息：业务 Code 码、错误信息和参考文档（可选）。
  d. 返回的错误信息，需要是可以直接展示给用户的安全信息，也就是说不能包含敏感信息；同时也要有内部更详细的错误信息，方便 debug。
  e. 返回的数据格式应该是固定的、规范的。
  f. 错误信息要保持简洁，并且提供有用的信息。
3. 业务code码设计
  a. 新浪设计规范：纯数字表示，不同部位代表不同的服务，不同的模块。错误代码说明：100101
    ⅰ. 10: 服务。
    ⅱ. 01: 某个服务下的某个模块。
    ⅲ. 01: 模块下的错误码序号，每个模块可以注册 100 个错误。
4. http status code
  a. Go net/http 包提供了 60 个错误码，大致分为如下 5 类：
    ⅰ. 1XX - （指示信息）表示请求已接收，继续处理。
    ⅱ. 2XX - （请求成功）表示成功处理了请求的状态代码。
    ⅲ. 3XX - （请求被重定向）表示要完成请求，需要进一步操作。通常，这些状态代码用来重定向。
    ⅳ. 4XX - （请求错误）这些状态代码表示请求可能出错，妨碍了服务器的处理，通常是客户端出错，需要客户端做进一步的处理。
    ⅴ. 5XX - （服务器错误）这些状态代码表示服务器在尝试处理请求时发生内部错误。这些错误可能是服务器本身的错误，而不是客户端的问题。
  b. 简化建议
    ⅰ. 200 - 表示请求成功执行。
    ⅱ. 400 - 表示客户端出问题。
      1. 401 - 表示认证失败。
      2. 403 - 表示授权失败。
      3. 404 - 表示资源找不到，这里的资源可以是 URL 或者 RESTful 资源。
    ⅲ. 500 - 表示服务端出问题。
错误包设计
1. 功能
  a. 支持错误堆栈
  b. 支持不同的打印格式
  c. 能支持 Wrap/Unwrap 功能，也就是在已有的错误上，追加一些新的信息
  d. 有Is方法
  e. 支持 As 函数。
  f. 非格式化创建和格式化创建
认证


实用工具

参考资料
1. https://time.geekbang.org/column/article/380033
2. https://learnku.com/docs/effective-go/2020/introduction/6236
3. https://coolshell.cn/articles/series/go%e7%bc%96%e7%a8%8b%e6%a8%a1%e5%bc%8f
4. https://rakyll.org/style-packages/
5. https://github.com/xxjwxc/uber_go_guide_cn
6. https://github.com/marmotedu/geekbang-go/blob/master/SOLID%E5%8E%9F%E5%88%99%E4%BB%8B%E7%BB%8D.md
7. https://goswagger.io/
8. https://github.com/marmotedu/geekbang-go/blob/master/%E4%BC%98%E7%A7%80%E5%BC%80%E6%BA%90%E6%97%A5%E5%BF%97%E5%8C%85%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B.md
