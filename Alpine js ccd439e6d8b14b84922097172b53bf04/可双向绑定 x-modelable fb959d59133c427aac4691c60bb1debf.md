# 可双向绑定: x-modelable

---

**`x-modelable`**指令允许你将任何 Alpine 属性公开为**`x-model`**指令绑定的目标。

这里有一个简单的例子，使用**`x-modelable`**公开一个变量，使**`x-model`**指令可以绑定它。

```html
<div x-data="{ number: 5 }">
  <div x-data="{ count: 0 }" x-model="number" x-modelable="count">
    <button @click="count++">增加</button>

    <p>Count: <span x-text="count"></span></p>
  </div>

  <p>Number: <span x-text="number"></span></p>
</div>
```

就像你看到的一样，外部作用域范围的属性 `**number**` 现在绑定到内部作用域范围的属性 `**count**`。

通常，此功能将与 Laravel Blade 等后端模板框架结合使用。它对于将 Alpine 组件抽象到后端模板中并通过**`x-model`**将状态公开给外部作用域非常有用，就像它是一个本地输入一样。