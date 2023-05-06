# 传输: x-teleport

---

**`x-teleport`**指令允许你将 Alpine 模板的一部分完全传输到页面 DOM 上的另一部分。

这对于诸如嵌套的弹出层之类的情况很有用，在这些情况下，它有助于打破当前 Alpine 组件的**`z-index`**。

> 警告：如果你是 Livewire 用户，此功能目前在 Livewire 组件中不起作用。对它的支持已列入计划。
> 

# x-teleport

---

通过将**`x-teleport`**指令添加到**`<template>`**元素，告诉 Alpine 将该元素“附加”到提供的选择器。

> **`x-teleport`**指令的选择器允许是你通常会传递到**`document.querySelector`**之类的东西中的任何字符串。它会找到第一个匹配的元素，可以是标签名(**`body`**)、Class(**`.my-class`**)、ID(**`#my-id`**)或任何其他有效的 CSS 选择器。
> 

下面是一个示例：

```html
<body>
    <div x-data="{ open: false }">
        <button @click="open = !open">切换按钮</button>
 
        <template x-teleport="body">
            <div x-show="open">
                弹出内容...
            </div>
        </template>
    </div>
 
    <div>弹出内容会放置在此元素之后。</div>
 
    ...
 
</body>
```

请注意，当点击切换按钮时，弹出内容显示在“弹出内容会放置在此元素之后。”之后。这是因为当 Alpine 初始化时，它会发现**`x-teleport="body"`**，然后附加和初始化该元素到提供的元素选择器，比如示例中的 `**body`** 标签。

# 事件转发

---

Alpine 尽最大努力让传输的体验做到最好。你通常能在**`<template>`**元素中做的任何事情，都应该能够在使用**`x-teleport`**指令的**`<template>`**元素中做。传输的内容可以访问正常的 Alpine 组件的作用域以及其他功能，如**`$refs`**、**`$root`**等。

但是，原生 DOM 事件没有传输的概念。因此，如果你从传输的元素内部触发点击事件，该事件会像原生 DOM 事件一样在 DOM 树中冒泡。

为了使这种体验更加丝滑，你可以通过直接在**`<template x-teleport...>`**元素本身上使用监听器来“转发”事件，如下所示：

```html
<div x-data="{ open: false }">
    <button @click="open = !open">切换按钮</button>
 
    <template x-teleport="body" @click="open = false">
        <div x-show="open">
            弹出内容...
            （点击关闭）
        </div>
    </template>
</div>
```

Alpine 通过查找在**`<template x-teleport...>`**上使用的事件监听器来实现从**`<template>`**元素本身的外部监听被传送的元素内部的事件，并阻止这些事件传播到传输的 DOM 元素之外。然后它会从 `**<template x-teleport...>**` 创建该事件的副本。

# 嵌套

---

如果你试图将一个弹出层嵌套在另一个弹出层中，则传输尤其有用。Alpine 让这一切变得十分简单：

```html
<div x-data="{ open: false }">
    <button @click="open = !open">切换按钮</button>
 
    <template x-teleport="body">
        <div x-show="open">
            弹出内容...
 
            <div x-data="{ open: false }">
                <button @click="open = !open">嵌套切换按钮</button>
 
                <template x-teleport="body">
                    <div x-show="open">
                        嵌套弹出内容...
                    </div>
                </template>
            </div>
        </div>
    </template>
</div>
```

在“打开”两个弹出层之后，内容都被创建为 `**body`** 的子元素，并将呈现为页面上的同级元素，而不再是嵌套关系。