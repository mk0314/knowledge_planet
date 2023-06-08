<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-08 19:34:20
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-08 19:38:58
 * @FilePath: \knowledge_planet\docs\md\idea-plugin\Express\Egg.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

### Egg.js 是一款面向企业级应用的 Node.js 框架

它基于 Koa.js 进行了进一步封装，提供了更加易用、可扩展、稳定、高性能的开发环境和工具链。

Egg.js 在 Koa.js 的基础上提供了以下特性：

插件机制：Egg.js 支持通过插件的方式进行功能扩展，例如数据库、缓存、Session 等。

规范化约定：Egg.js 强调「约定优于配置」，提供了一套目录结构和编码规范，方便团队协作和开发。

统一错误处理：Egg.js 提供了统一的错误处理机制，可以在应用程序级别和插件级别进行统一的异常处理。

安全策略：Egg.js 内置了多种安全策略，例如 XSS 和 CSRF 防御、参数校验等。

可测试性：Egg.js 提供了完善的测试工具和测试框架，支持单元测试、集成测试和端到端测试。

Egg.js 的应用场景非常广泛，适合于各种大中型企业和互联网公司的 Web 应用开发。它提供了非常友好的开发环境和工具链，开发者可以用最少的代码实现最复杂的功能。同时，Egg.js 也注重安全性和可扩展性，能够满足企业级应用的需求。

### 项目结构

```
egg-example/
├── package.json
├── app.js (自定义的启动文件)
├── agent.js (自定义的 Agent 启动文件)
├── app
│   ├── router.js (路由配置)
│   ├── controller (控制器)
│   ├── service (服务)
│   ├── extend (框架扩展)
│   ├── middleware (中间件)
│   ├── schedule (定时任务)
│   ├── public (静态文件)
│   ├── view (模板文件)
│   └── ...(其它业务文件)
├── config
│   ├── plugin.js (插件配置)
│   ├── config.default.js (默认环境配置)
│   ├── config.prod.js (生产环境配置)
│   ├── config.test.js (测试环境配置)
│   └── ...(其它环境配置)
├── logs
├── run
├── test (测试代码)
└── node_modules
```

上述目录结构涉及到的一些文件和文件夹说明：

1. app.js：自定义的 Egg 应用启动文件，可以进行一些自定义的初始化。
2. agent.js：自定义的 Egg Agent 启动文件，可以进行一些自定义的初始化。
3. app/router.js：路由配置文件，用于定义路由映射规则及对应的控制器。
4. app/controller：存放控制器文件，用于处理业务逻辑并响应 HTTP 请求。
5. app/service：存放服务文件，用于处理复杂的业务逻辑。
6. app/extend：框架扩展目录，开发者可以在此处对 Egg.js 框架进行扩展。
7. app/middleware：存放中间件文件，用于处理一些公共的业务逻辑（如身份认证等）。
8. app/schedule：定时任务目录，可用于定时执行一些任务。
9. app/public：存放静态文件，如图片、CSS、JavaScript 等。
10. app/view：存放模板文件，用于渲染页面。
11. config：配置文件目录，包含插件配置和不同环境的应用程序配置。
12. logs：存放应用程序日志文件。
13. run：存放运行时文件，如 PID 文件等。
14. test：存放测试代码，用于进行单元测试和集成测试。
15. node_modules：存放 Node.js 模块依赖。
