### React state 和 props 区别是什么 ?

State:

- 定义：state 是组件内部管理的状态数据。
- 用途：用于存储和管理组件内部的动态数据，这些数据可能会在组件生命周期内发生变化。
- 修改方式：只能通过 this.setState 在类组件中或 useState 钩子在函数组件中进行修改。

Props:

- 定义：props 是组件从父组件接收的数据。
- 用途：用于将数据从父组件传递到子组件，子组件可以使用这些数据进行渲染。
- 修改方式：props 是只读的，不能在子组件中修改。

### 什么是 Redux？

Redux 是一个用于 JavaScript 应用程序中的状态管理库，通常与 React 一起使用，但也可以与其他框架或库结合使用。Redux 的主要目的是帮助开发者管理和维持应用程序的状态，使得在复杂应用中状态的变化更可预测和可控。

### 如何在 React 中使用样式？

1. 内联样式 (Inline Styles)
   React 支持在 JSX 中直接使用内联样式。内联样式使用对象语法，键是驼峰命名的 CSS 属性名，值是字符串或数字。

```jsx
import React from "react";

function App() {
  const divStyle = {
    color: "blue",
    backgroundColor: "lightgray",
    padding: "10px",
    borderRadius: "5px",
  };

  return <div style={divStyle}>这是一个有样式的 div</div>;
}

export default App;
```

2. CSS 样式表 (CSS Stylesheets)
   可以像传统 HTML 一样使用外部 CSS 文件，并通过 className 属性来应用样式。

```jsx
// App.js
import React from "react";
import "./App.css"; // 引入 CSS 文件

function App() {
  return <div className="container">这是一个有样式的 div</div>;
}

export default App;
```

```CSS
/* App.css */
.container {
  color: blue;
  background-color: lightgray;
  padding: 10px;
  border-radius: 5px;
}
```

3. CSS 模块 (CSS Modules)
   CSS 模块允许你将 CSS 样式限定在特定组件内，避免全局命名冲突。CSS 模块文件通常以 .module.css 结尾。

```jsx
// App.js
import React from "react";
import styles from "./App.module.css"; // 引入 CSS 模块

function App() {
  return <div className={styles.container}>这是一个有样式的 div</div>;
}

export default App;
```

```CSS
/* App.module.css */
.container {
  color: blue;
  background-color: lightgray;
  padding: 10px;
  border-radius: 5px;
}
```

4. Tailwind CSS
   使用 Tailwind CSS，可以通过类名快速应用样式。

```
function App() {
  return (
    <div className="text-blue-500 bg-gray-200 p-5">
      Hello, World!
    </div>
  );
}
```

### 简述 React 有什么特点？

1. **组件化**

   - **定义**：React 基于组件来构建应用程序。组件是可以独立使用和复用的 UI 单元。
   - **优点**：组件化使得代码更容易维护、复用和测试。

2. **虚拟 DOM (Virtual DOM)**

   - **定义**：React 使用虚拟 DOM 来提高性能。虚拟 DOM 是 React 在内存中维护的一份 DOM 结构的副本。
   - **优点**：当状态发生变化时，React 会先更新虚拟 DOM，然后将其与真实 DOM 进行比较，仅更新必要的部分，从而提高了性能。

3. **单向数据流**

   - **定义**：React 中的数据流是单向的，从父组件流向子组件。
   - **优点**：单向数据流使得数据管理更加清晰和可预测，易于调试和维护。

4. **声明式编程**

   - **定义**：React 采用声明式编程风格，开发者只需描述 UI 应该呈现的状态，而不需要手动操作 DOM。
   - **优点**：声明式编程使得代码更简洁、易于理解和维护。

5. **JSX 语法**

   - **定义**：JSX 是一种 JavaScript 的语法扩展，允许在 JavaScript 中编写类似 HTML 的代码。
   - **优点**：JSX 使得组件的结构更加直观，代码更加清晰。

6. **强大的社区和生态系统**

   - **定义**：React 由 Facebook 维护，并且有一个庞大的开发者社区和丰富的生态系统。
   - **优点**：丰富的第三方库和工具可以帮助开发者更高效地构建应用。

7. **灵活性**

   - **定义**：React 只关注视图层，可以与其他库或框架搭配使用，如 Redux、React Router 等。
   - **优点**：开发者可以根据需要自由选择技术栈，构建灵活的应用架构。

8. **React Hooks**
   - **定义**：React Hooks 是 React 16.8 引入的新特性，让函数组件也能使用状态和生命周期等特性。
   - **优点**：Hooks 简化了组件逻辑，使代码更加简洁和可复用。

### React setState 调用之后发生了什么？是同步还是异步？

1. **异步特性解释**

   - 当你调用 `setState`，React 会将状态更新请求放入队列中，并在稍后的某个时间点进行批量更新。这种异步处理方式可以减少重新渲染的次数，从而提高性能。

2. **具体过程**
   - **状态更新请求加入队列**：`setState` 被调用时，React 将状态更新请求放入队列中，而不是立即更新状态。
   - **批量处理**：在 React 的事件处理机制或者生命周期方法结束之后，React 会检查队列中的状态更新请求，并进行批量处理。这意味着多个 `setState` 调用可能会被合并成一次更新。
   - **重新渲染**：状态更新后，React 重新计算虚拟 DOM，并将变化应用到真实 DOM 上，触发组件的重新渲染。

### React 类组件和函数组件之间的区别是什么？

1. **定义方式**

   - **类组件**：使用类语法。
   - **函数组件**：使用函数语法。

2. **状态管理**

   - **类组件**：使用 `this.state` 和 `this.setState`。
   - **函数组件**：使用 `useState` Hook。

3. **生命周期方法**

   - **类组件**：有一系列生命周期方法。
   - **函数组件**：使用 `useEffect` Hook。

4. **代码简洁性**

   - **类组件**：通常代码较多。
   - **函数组件**：通常更简洁，代码更少。

5. **性能**
   - **类组件**：在某些情况下可能不如函数组件高效。
   - **函数组件**：在某些情况下可能更高效。

### 父子组件的通信方式？

1. **通过 props 传递数据**

   - 适用于简单的父子组件通信。

2. **通过回调函数传递数据**

   - 适用于子组件向父组件传递数据。

3. **使用 Context**

   - 适用于需要在组件树中共享数据的情况。

4. **使用 Redux 或其他状态管理库**
   - 适用于更复杂的应用，提供全局状态管理。

### 简述虚拟 DOM 的概念和机制 ？

**虚拟 DOM (Virtual DOM)** 是一种编程概念，用于提高 web 应用的性能和开发效率。它是实际 DOM 的抽象表示，用纯 JavaScript 对象实现。虚拟 DOM 描述了 UI 的结构和状态，与真实 DOM 相比，更新操作更快、更高效。

### 虚拟 DOM 的机制

虚拟 DOM 的工作机制主要包括以下几个步骤：

1. **创建虚拟 DOM**：

   - React 用 JavaScript 对象来表示组件的结构和状态，这些对象统称为虚拟 DOM。
   - 每次组件状态变化时，React 都会创建一个新的虚拟 DOM。

2. **比较虚拟 DOM（Diffing）**：

   - 当状态或属性发生变化时，React 会生成新的虚拟 DOM 树。
   - React 使用一种高效的算法（Diffing 算法）比较新旧虚拟 DOM 树，找出变化的部分。

3. **更新真实 DOM（Reconciliation）**：
   - React 根据比较结果，仅对真实 DOM 中需要更新的部分进行修改，而不是重新渲染整个页面。
   - 这种部分更新的方式大大提高了性能，减少了浏览器的重绘和重排。

### 解释为什么调用 setState 而不是直接改变 state？

1. **确保状态更新的正确性**

   - `setState` 和 `useState` 的更新函数确保状态更新是正确的，特别是在异步更新的情况下。

2. **触发重新渲染**

   - 状态更新后会触发组件重新渲染，确保 UI 根据最新状态进行更新。

3. **批量更新和性能优化**

   - React 会对多次状态更新进行批量处理，提高性能。

4. **保持状态管理的一致性**
   - 保证状态管理的一致性和可预测性，特别是在复杂应用中。

### 请简述 React 生命周期调用方法的顺序 ？

```
挂载: constructor -> getDerivedStateFromProps -> render -> componentDidMount
更新: getDerivedStateFromProps -> shouldComponentUpdate -> render -> getSnapshotBeforeUpdate -> componentDidUpdate
卸载: componentWillUnmount
```

### React 和 ReactDOM 有什么区别？

使用 React 来定义和创建组件，利用其核心功能。

使用 ReactDOM 来将这些组件渲染到 Web 页面的浏览器 DOM 中。

### react-dom 包有什么用？

- 渲染组件

使用 `ReactDOM.render` 将 React 组件渲染到 DOM 中。

- 创建门户

使用 `ReactDOM.createPortal` 在 DOM 的其他节点中渲染组件。

- 服务端渲染

使用 `react-dom/server` 模块在服务端渲染 React 组件。

- 测试

用于模拟组件渲染和交互测试。

通过使用 `react-dom`，开发者可以将 React 组件的虚拟 DOM 树与实际的浏览器 DOM 进行连接，实现高效、灵活的用户界面更新和渲染。

### React 必须使用 JSX 吗？

React 并不强制使用 JSX，但推荐使用它来提高代码的可读性和开发效率。如果你不想使用 JSX，可以直接使用 React.createElement 来创建 React 组件。选择哪种方式取决于你的项目需求和个人偏好。

### React 组件命名推荐的方式是哪个？

- ascalCase

每个单词的首字母大写，无分隔符。

- 单一职责原则

组件名称应反映其功能或用途。

- 避免缩写

尽量使用完整的单词，以提高代码的可读性。

### 为什么 Redux state 函数被称为 Reducer？

### 为什么 React 使用 className 而不是 class 属性？

### 什么是 Flux？

Flux 的单向数据流模型使得应用的状态管理更加清晰和可预测

1. **用户交互或其他事件** 触发 **动作**。
2. **动作** 被分发到 **分发器**。
3. **分发器** 调用所有注册的 **存储** 中的处理函数。
4. **存储** 更新状态并发出变化事件。
5. **视图** 监听 **存储** 的变化事件，重新获取数据并重新渲染。

总结

Flux 是一种架构模式，特别适用于使用 React 构建的复杂客户端应用。它通过单向数据流的方式，使得应用的状态管理更加清晰、可预测。Flux 的核心部分包括 **动作**、**分发器**、**存储** 和 **视图**，每个部分各司其职，共同构成一个高效的数据流管理体系。

### 什么是 ReactDOMServer？

ReactDOMServer

`ReactDOMServer` 允许你在服务器上渲染 React 组件，并将生成的 HTML 发送到客户端。这不仅提高了页面加载速度，还改善了 SEO。通过结合客户端的 `ReactDOM.hydrate` 方法，你可以在初始加载后接管服务器渲染的内容，实现无缝的客户端交互体验。

### 什么是 Fragment？

Fragment 是 React 提供的一个方便的工具，用于包裹一组子元素而不会在 DOM 中添加额外的节点。它可以通过 React.Fragment 或简写形式 <>...</> 来使用，主要用于避免不必要的 DOM 元素，提高性能，并保持 HTML 结构的语义化。

### 什么是无状态组件？

无状态组件是通过函数定义的简单组件，只负责接收 props 并渲染 UI。它们没有内部状态和生命周期方法，非常适合用于渲染静态内容或展示数据。通过 React Hooks，即使是函数组件也可以管理状态和副作用，使得函数组件更加强大和灵活。

### 什么是有状态组件？

有状态组件在 React 中通过管理内部状态来实现动态和交互式的用户界面。它们可以使用类组件或结合 Hooks 的函数组件来实现，适合处理需要内部状态管理和复杂逻辑的情况。无状态组件则更适合用于渲染静态内容或展示数据的简单组件。

### 有状态组件 vs 无状态组件

#### 有状态组件

- 维护和管理自己的内部状态。
- 可以使用生命周期方法（类组件）。
- 适合处理复杂逻辑和交互的组件。

#### 无状态组件（Stateless Component）

- 不维护内部状态。
- 只接收 props 并渲染 UI。
- 更简单和轻量，适合只负责展示数据的组件。

### 简述 React store 的概念 ？

在 React 中，"store" 通常指的是一个集中式的状态管理机制，用于管理组件的共享状态。虽然 React 本身没有内置的 store 概念，但在很多状态管理库（如 Redux、MobX、Recoil）中，store 这个术语非常常见。

### 简述点(…)在 React 的作用 ？

在 React 中，点（...）符号主要用作展开语法（spread syntax）和剩余参数（rest parameters）。以下是它们的具体作用：

### 解释 React 中 render() 的目的和作用 ？

### props 的变动，是否会引起 state hook 中数据的变动？

在 React 中，props 和 state 是两个独立的概念。props 是从父组件传递给子组件的数据，而 state 是组件内部管理的数据。通常情况下，props 的变动不会直接引起 state hook 中数据的变动，除非你在组件中显式地处理这种关系。

### React Context 和 React Redux 有什么区别？

React Context

- 内置于 React，不需要额外依赖。
- 适用于简单的状态共享和全局配置。
- 在频繁更新场景下可能存在性能问题。

React Redux

- 需要额外安装 `redux` 和 `react-redux`。
- 适用于复杂的大型应用，提供单一数据源和可预测的状态管理。
- 支持中间件和强大的调试工具，适合处理复杂的状态管理需求。

### React diff 算法的原理是什么？

React 的 diff 算法通过层级比较、同类节点比较和唯一标识（key）来高效地计算新旧虚拟 DOM 之间的差异。这个算法使得 React 能够最小化实际 DOM 的操作，从而提高性能和响应速度。理解这些原理有助于更好地优化和使用 React 构建高性能的应用。

### React Hooks 和生命周期的关系？

Hooks 提供了在函数组件中使用状态和副作用的能力。

useEffect Hook 可以覆盖类组件的生命周期方法，通过适当的执行逻辑处理组件的不同状态。

Hooks 更加简洁，且易于组合和重用，使代码更具有可读性和可维护性。

### React 与 React Native 有何不同？

运行环境：

- **React** 运行在浏览器中，用于构建网页应用。
- **React Native** 运行在移动设备上，用于构建移动应用。

UI 组件：

- **React** 使用 HTML 标签和自定义的 React 组件。
- **React Native** 使用原生组件（如 `<View>`、`<Text>`）和自定义的 React Native 组件。

样式：

- **React** 使用 CSS 或 CSS-in-JS 库来定义样式。
- **React Native** 使用内联样式对象或 `StyleSheet` 来定义样式。

目标平台：

- **React** 主要用于构建跨浏览器的网页应用。
- **React Native** 主要用于构建跨平台的移动应用（支持 iOS 和 Android）。

### React 中的命令式和声明式有什么区别？

React 中的声明式编程

React 鼓励使用声明式编程风格，因为它简化了代码的编写和维护。通过声明式编程，你只需描述组件的最终状态，而不需要关心如何一步步地达到这个状态。React 会根据状态和 props 的变化自动更新 UI。

声明式编程：

- 描述“做什么”。
- 代码更简洁、易读。
- React 会根据状态变化自动更新 UI。

命令式编程：

- 描述“怎么做”。
- 代码更详细、复杂。
- 需要手动处理 DOM 操作和状态管理。

在 React 中，使用声明式编程可以让代码更直观、更易于维护，同时充分利用 React 的自动化更新机制。

### React 组件中怎么做事件代理？它的原理是什么？

在 React 中，事件代理是一种优化性能的技术，通过将事件监听器添加到父元素上来处理其子元素的事件，而不是为每个子元素添加单独的事件监听器。这可以减少内存消耗和提高应用的性能。

事件代理的原理

事件代理的原理基于事件冒泡（Event Bubbling），即事件从最深的元素开始触发，逐级向上传播到父元素。通过将事件监听器添加到父元素上，可以捕获并处理所有子元素的事件。

在 React 中实现事件代理

在 React 中实现事件代理非常简单。你可以在父组件中添加事件监听器，并在事件处理函数中使用事件对象 (event) 来确定具体的目标子元素。

### React 高阶组件是什么，和普通组件有什么区别，适用什么场景

高阶组件（HOC）是一种用于重用组件逻辑的模式，通过接收一个组件并返回一个新的组件，实现逻辑复用和代码抽象。与普通组件不同，高阶组件侧重于增强和修改组件的行为，适用于逻辑复用、组件增强和代码分离的场景。理解和使用高阶组件可以提高代码的可维护性和复用性。

### React 中 props.children 和 React.Children 的区别

props.children 用于直接访问组件的子元素。

React.Children 提供了一些实用函数，用于操作和处理这些子元素，特别是在需要遍历、计数或转换子元素时非常有用。

### React 中什么是受控组件和非控组件？

受控组件：表单元素的值由组件的 state 管理，React 负责更新和渲染。

非控组件：表单元素的值由 DOM 本身管理，React 只管理监听事件，不存储值。

### React 中发起网络请求应该在哪个生命周期中进行？为什么？

类组件：在 componentDidMount 生命周期方法中发起网络请求。

函数组件：使用 useEffect hook 并传递一个空依赖数组来发起网络请求。

这样做可以确保网络请求只在组件挂载后发起一次，并且组件已经准备好接收和渲染数据。

### React 中怎么检验 props？验证 props 的目的是什么？

验证 props 的目的：捕捉错误、文档化、提高开发体验。

使用 prop-types：安装 `prop-types` 库，并在组件中定义 `propTypes` 和 `defaultProps`。

常用类型：了解 `prop-types` 提供的各种类型和复合类型，以便更好地进行 props 验证。

通过使用 `prop-types` 对 props 进行验证，可以提高 React 组件的可靠性和可维护性，帮助开发者在开发过程中及时发现和修正错误。
