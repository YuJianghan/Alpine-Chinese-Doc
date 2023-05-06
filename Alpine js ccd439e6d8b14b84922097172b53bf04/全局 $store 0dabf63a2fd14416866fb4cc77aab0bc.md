# 全局: $store

---

你可以使用**`$store`**魔法方便地使用**`Alpine.store()`**在全局定义的属性和行为。例如：

```html
<button x-data @click="$store.darkMode.toggle()">切换深色模式</button>
 
...
 
<div x-data :class="$store.darkMode.on && 'bg-black'">
    ...
</div>
 
 
<script>
    document.addEventListener('alpine:init', () => {
        Alpine.store('darkMode', {
            on: false,
 
            toggle() {
                this.on = !this.on
            }
        })
    })
</script>
```

假设我们已经实现了**`darkMode`**并将**`on`**属性设置为“false”，当按下**`<button>`**时，属性**`on`**将为“true”，页面的背景颜色将变为深色。

# 全局属性

---

如果不需要定义整个实体作为全局的数据，也可以定义和访问任何简单类型的数据作为全局属性。

下面和上面的例子行为一致，但使用简单的布尔值作为全局属性：

```html
<button x-data @click="$store.darkMode = ! $store.darkMode">切换深色模式</button>
 
...
 
<div x-data :class="$store.darkMode && 'bg-black'">
    ...
</div>
 
 
<script>
    document.addEventListener('alpine:init', () => {
        Alpine.store('darkMode', false)
    })
</script>
```