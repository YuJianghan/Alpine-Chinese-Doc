# 绑定: x-bind

---

使用**`x-bind`**指令可以将数据绑定到元素属性的属性值上。

例如下面的输入框组件，使用**`x-bind`**指令将数据绑定到输入框的占位符属性上。

```html
<div x-data="{ placeholder: '请在此处输入...' }">
    <input type="text" x-bind:placeholder="placeholder">
</div>
```

# 简写语法

---

如果你觉得**`x-bind:`**这种写法过于冗长，你也可以使用简写：**`:`**。例如，下面的示例中输入框的作用与上面相同，只是使用了简写语法。

```html
<input type="text" :placeholder="placeholder">
```

# 绑定到 class 属性

---

**`x-bind`**指令更常见的用法是给元素的 class 属性绑定不同的属性值来控制样式的改变。

下面的示例中，同样实现了一个下拉组件，但是并没有使用**`x-show`**指令，而是通过控制是否给元素的 class 属性绑定属性值 hidden 来实现。

```html
<div x-data="{ open: false }">
    <button x-on:click="open = !open">下拉切换按钮</button>
 
    <div :class="open ? '' : 'hidden'">
        下拉组件内容...
    </div>
</div>
```

现在，当**`open`**变为**`false`**时，元素的 class 属性将绑定上 hidden。

# class 属性的短路表达式

---

如果你觉得 JavaScript 三元表达式的写法过于冗长，你也可以使用 JavaScript 的短路表达式。下面的示例展示了这种写法：

```html
<div :class="show ? '' : 'hidden'">
<!-- 等同于： -->
<div :class="show || 'hidden'">
```

你也可以使用相反的结果。比如我们不使用**`open`**来控制，而是使用具有相反值的变量：**`closed`**。

```html
<div :class="closed ? 'hidden' : ''">
<!-- 等同于： -->
<div :class="closed && 'hidden'">
```

在一些流行的 JavaScript 代码风格规范中，都推荐使用短路表达式来替代非必要的三元表达式。

# class 属性的实体语法

---

Alpine 还提供了一个额外的语法来控制 class 属性的属性值。通过给其传递一个 JavaScript 实体来控制，这个 JavaScript 实体内的数据只有一对键值对，使用这个实体更应该被叫做映射，其中映射的键为 class 属性名，映射的值为布尔值。例如：

```html
<div :class="{ 'hidden': !show }">
```

实体语法和之前的表达式语法不同，使用实体语法时，Alpine 不会保留元素原本 class 属性的同名属性值。例如：

```html
<div x-data="{ isHidden: false }">
    <div class="hidden" :class="{ 'hidden': isHidden }">我的 hidden 属性值将被移除</div>
    <div class="hidden" :class="isHidden && 'hidden'">我的 hidden 属性值仍然保留</div>
</div>
```

如果你仍然不太理解，接下来让我们深入研究 Alpine 是如何以不同于其他属性的方式处理**`x-bind:class`**。

# **x-bind:class 的特殊行为**

---

**`x-bind`**绑定到 class 属性的行为和绑定其他属性的行为有一些不同。

例如以下情况。

```html
<div class="opacity-50" :class="hide && 'hidden'">
<div id="opacity-50" :id="hide && 'hidden'">
```

如果**`hide`**为true，对于绑定到 class 的情况，上面的示例会将 hidden 属性值附加到 class 中，而对于绑定到其他属性的情况，例如 id ，示例的 hidden 属性值将会覆盖原本的属性值 opacity-50 。最终结果将会是这样：

```html
<div class="opacity-50 hidden">
<div id="hidden">
```

这种行为看上去是十分符合逻辑的，因为 class 属性本就应该支持接受多个属性值来复合多种样式，使用这种特殊行为能更好的满足需求。

# 绑定到 style 属性

---

与 class 属性的实体语法类似，Alpine 也提供了一种实体语法来将属性值绑定到 style 属性上。

```html
<div :style="{ color: 'red', display: 'flex' }">
 
<!-- 渲染为: -->
<div style="color: red; display: flex;" ...>
```

你同样可以使用三元表达式和短路表达式。

```html
<div x-bind:style="true ? { color: 'red' } : {}">
<div x-bind:style="true && { color: 'red' }">
 
<!-- 渲染为: -->
<div style="color: red;">
```

使用实体语法的优点是能将其与元素上的现有样式混合在一起：

```html
<div style="padding: 1rem;" :style="{ color: 'red', display: 'flex' }">
 
<!-- 渲染为: -->
<div style="padding: 1rem; color: red; display: flex;" ...>
```

同 Alpine 中的其他指令一样，你也可以使用**`x-data`**中的数据来作为实体：

```html
<div x-data="{ styles: { color: 'red', display: 'flex' }}">
    <div :style="styles">
</div>
 
<!-- 渲染为: -->
<div ...>
    <div style="color: red; display: flex;" ...>
</div>
```

# 绑定 Alpine 指令

---

**`x-bind`**也可以将具有不同指令和属性的实体绑定到元素。

```html
<div x-data="dropdown()">
    <button x-bind="trigger">打开下拉组件</button>
 
    <span x-bind="dialogue">下拉组件内容</span>
</div>
 
<script>
    document.addEventListener('alpine:init', () => {
        Alpine.data('dropdown', () => ({
            open: false,
 
            trigger: {
                ['x-ref']: 'trigger',
                ['@click']() {
                    this.open = true
                },
            },
 
            dialogue: {
                ['x-show']() {
                    return this.open
                },
                ['@click.outside']() {
                    this.open = false
                },
            },
        }))
    })
</script>
```

对于**`x-bind`**的这种用法需要注意的是：

> 当被绑定的指令是**`x-for`**时，你应该从回调中返回一个表达式字符串。例如：**`['x-for']() { return 'item in items' }`**
>