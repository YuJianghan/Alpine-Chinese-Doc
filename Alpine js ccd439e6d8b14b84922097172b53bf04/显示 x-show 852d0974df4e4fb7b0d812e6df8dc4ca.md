# 显示: x-show

---

**`x-show`**指令可以控制显示和隐藏某一元素。

下面是一个使用**`x-show`**指令的下拉组件的示例。

```html
<div x-data="{ open: false }">
    <button x-on:click="open = !open">下拉切换按钮</button>
 
    <div x-show="open">
        下拉组件内容...
    </div>
</div>
```

当点击下拉切换按钮时，下拉组件的内容将会相应地显示和隐藏。

> 如果页面加载时**`x-show`**的默认状态为“false”，由于**`x-show`**会在 Alpine 组件初始化完成后生效，会产生”页面闪烁“的问题。你可以在页面上使用**`x-cloak`**来避免这个问题。更多关于**`x-cloak`**的内容你可以在其文档中了解。
> 

# 过渡

---

如果想在**`x-show`**指令控制元素时加上一些过渡动画，你可以将其与**`x-transition`**结合使用。下面的示例与上面基本相同，只是加上了过渡动画。

```html
<div x-data="{ open: false }">
    <button x-on:click="open = !open">下拉切换按钮</button>
 
    <div x-show="open" x-transition>
        下拉组件内容...
    </div>
</div>
```

# 权重修饰符

---

有时你需要给**`x-show`**指令设置更高的权重。类似在设置CSS时将**`display`**属性的属性值加上**`!important`**修饰符增加这个样式的权重，使它优先生效。而在 Alpine 的组件中，你可以使用**`.important`**修饰符达成同样的效果。

```html
<div x-data="{ open: false }">
    <button x-on:click="open = ! open">下拉切换按钮n</button>
 
    <div x-show.important="open">
        下拉组件内容...
    </div>
</div>
```