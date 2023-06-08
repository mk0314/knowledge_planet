<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-08 19:07:57
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-08 19:43:15
 * @FilePath: \knowledge_planet\docs\md\idea-plugin\Vue\Vue3知识点.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

### 概念

Vue3 是一种流行的 JavaScript 框架，用于构建交互式用户界面和单页面应用程序。它是 Vue.js 框架的最新版本，提供了一些新的特性和改进，如更好的性能、更好的 TypeScript 支持、重构的响应式系统等等。Vue3 的主要目标是简化开发过程和提高开发效率，同时保持灵活性和可扩展性。如果您正在寻找一种现代化的 JavaScript 框架来构建动态 Web 应用程序，Vue3 可能是一个很好的选择。

### 知识点

以下是 Vue3 的一些常见知识点：

1. Composition API：Vue3 中引入了 Composition API，它提供了一种新的组件组织方式。相比于 Vue2 的 Options API，Composition API 更灵活、可组合和易于测试。

2. 响应式系统的改进：Vue3 重构了响应式系统，使其运行更快、更可靠。Proxy 代理对象代替了 Vue2 中的 Object.defineProperty 方法，解决了 Vue2 在对象嵌套时监听不到问题。

3. Teleport 组件：Vue3 中引入了 Teleport 组件，它允许您将组件渲染到 DOM 文档中的任何地方，而不仅仅是父组件内部。

4. Fragment 组件：Vue3 中的 Fragment 组件允许您在不添加多余 DOM 元素的情况下返回多个子元素。

5. 更好的 TypeScript 支持：Vue3 的类型声明文件更完善，对 TypeScript 的支持更加友好。

6. 生命周期的变化：Vue3 中移除了一些生命周期钩子函数，如 activated 和 deactivated。新增了两个生命周期函数：beforeUnmount 和 renderTracked/renderTriggered。

7. 更好的性能：Vue3 改善了渲染性能，配合编译时优化，可以有效减少运行时开销。

这些是 Vue3 的一些常见知识点，当然还有很多其他的特性和改进，您可以通过阅读 Vue3 的官方文档来深入学习。
