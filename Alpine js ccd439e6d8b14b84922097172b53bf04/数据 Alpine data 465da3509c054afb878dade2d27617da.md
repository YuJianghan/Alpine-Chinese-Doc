# 数据: Alpine.data

---

**`Alpine.data(...)`**提供了一种在程序中复用**`x-data`**数据的方法。

下面是一个下拉组件的示例：

```html
<div x-data="dropdown">
    <button @click="toggle">...</button>
 
    <div x-show="open">...</div>
</div>
 
<script>
    document.addEventListener('alpine:init', () => {
        Alpine.data('dropdown', () => ({
            open: false,
 
            toggle() {
                this.open = !this.open
            }
        }))
    })
</script>
```

正如你所看到的，我们已经将通常在**`x-data`**中直接定义的属性和行为提取到一个单独的 Alpine 组件实体中。

# 作为模块导入

---

如果使用的是模块化导入的 Alpine.js，上面的代码逻辑可以按下面的方式注册组件：

```jsx
import Alpine from `alpinejs`
import dropdown from './dropdown.js'
 
Alpine.data('dropdown', dropdown)
 
Alpine.start()
```

这里假设您有一个名为**`dropdown.js`**的文件，其中包含以下内容：

```jsx
export default () => ({
    open: false,
 
    toggle() {
        this.open = !this.open
    }
})
```

# 初始化参数

---

除了直接引用**`Alpine.data`**提供的名称（如**`x-data="dropdown"`**）之外，你还可以将它们作为函数引用（**`x-data="dropdown()"`**）。通过直接将它们作为函数调用，同时也可以传入额外的参数以在创建初始数据实体时使用。如下所示：

```html
<div x-data="dropdown(true)">
```

```jsx
Alpine.data('dropdown', (initialOpenState = false) => ({
    open: initialOpenState
}))
```

现在，你可以根据为其提供的不同的参数来复用**`dropdown`**对象。

# 初始化函数

---

如果你的组件包含**`init()`**方法，Alpine 会在渲染组件之前自动执行该方法。例如：

```jsx
Alpine.data('dropdown', () => ({
    init() {
        // 这段代码将在 Alpine 初始化组件的其他逻辑前执行
    }
}))
```

# 使用魔法

---

如果你想从一个组件实体中使用魔术，你可以使用**`this`**上下文来实现：

```jsx
Alpine.data('dropdown', () => ({
    open: false,
 
    init() {
        this.$watch('open', () => {...})
    }
}))
```

# 使用 x-bind 封装指令

---

如果你希望重用的不仅仅是组件的数据实体，你还可以使用**`x-bind`**指令封装整个 Alpine 模板。

下面是一个使用**`x-bind`**提取之前的下拉组件的模板详细信息的示例：

```html
<div x-data="dropdown">
    <button x-bind="trigger"></button>
 
    <div x-bind="dialogue"></div>
</div>
```

```jsx
Alpine.data('dropdown', () => ({
    open: false,
 
    trigger: {
        ['@click']() {
            this.open = !this.open
        },
    },
 
    dialogue: {
        ['x-show']() {
            return this.open
        },
    },
}))
```