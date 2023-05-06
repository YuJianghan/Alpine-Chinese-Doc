# 过渡: x-transition

---

Alpine 提供了一个开箱即用的创建过渡的指令。使用**`x-transition`**指令，你可以在元素的显示或隐藏之间创建平滑的过渡。

在 Alpine 中处理过渡有两种主要的方法：

- **过渡助手**
- **应用 CSS 类别**

# 过渡助手

---

使用 Alpine 实现过渡最简单的方法是将**`x-transition`**添加到带有**`x-show`**的元素上。例如：

```html
<div x-data="{ open: false }">
    <button @click="open = ! open">Toggle</button>
 
    <span x-show="open" x-transition>
        Hello 👋
    </span>
</div>
```

正如你所看到的，默认情况下，**`x-transition`**使用不透明度和缩放的过渡来显示和隐藏元素。

你可以使用附加到**`x-transition`**指令的修饰符来修改这些默认值。让我们来看看这些。

## ****自定义持续时间****

默认情况下，过渡持续时间在进入时设置为150毫秒，离开时设置为75毫秒。

你可以使用**`.duration`**修饰符修改过渡的持续时间：

```html
<div ... x-transition.duration.500ms>
```

上面的**`<div>`**的过渡时间在进入时和离开时都是500毫秒。

如果你希望单独为进入和离开自定义过渡时间，你可以这样做：

```html
<div ...
    x-transition:enter.duration.500ms
    x-transition:leave.duration.400ms
>
```

## ****自定义延迟****

你可以使用**`.delay`**修饰符延迟过渡，如下所示：

```html
<div ... x-transition.delay.50ms>
```

上面的示例将使元素的进出延迟50毫秒执行。

## ****自定义不透明度****

默认情况下，Alpine 的**`x-transition`**使用不透明度和缩放过渡以实现“淡入淡出”效果。

如果只希望应用不透明度过渡（无缩放），可以使用**`.opacity`**修饰符完成：

```html
<div ... x-transition.opacity>
```

## ****自定义比例****

与**`.opacity`**修饰符类似，你可以将**`x-transition`**设置为仅缩放（不过渡不透明度），如下所示：

```html
<div ... x-transition.scale>
```

**`.scale`**修饰符还提供配置其比例值和原点值的功能：

```html
<div ... x-transition.scale.80>
```

上面的代码片段会把元素放大和缩小80%。

同样，你可以为单独为进入和离开自定义比例值，如下所示：

```html
<div ...
    x-transition:enter.scale.80
    x-transition:leave.scale.90
>
```

如果要自定义缩放过渡的原点，可以使用**`.origin`**修饰符：

```html
<div ... x-transition.scale.origin.top>
```

现在，将使用元素的顶部作为原点（而不是默认情况下的中心）来应用比例缩放。

正如你可能已经猜到的那样，它可以定义为：**`top`**、**`bottom`**、**`left`**和**`right`**。

如果愿意，你还可以组合两个原点值。例如，如果希望缩放的原点位于“右上角”，则可以使用：**`.origin.top.right`**作为修饰符。

# 应用 CSS 类别

---

为了直接控制过渡中的确切内容，你可以在过渡的不同阶段应用 CSS 类别。

> 以下示例使用 TailwindCSS 实用程序类别。
> 

```html
<script defer src="https://cdn.tailwindcss.com"></script>

<div x-data="{ open: false }">
    <button @click="open = ! open">Toggle</button>
 
    <div
        x-show="open"
        x-transition:enter="transition ease-out duration-300"
        x-transition:enter-start="opacity-0 scale-90"
        x-transition:enter-end="opacity-100 scale-100"
        x-transition:leave="transition ease-in duration-300"
        x-transition:leave-start="opacity-100 scale-100"
        x-transition:leave-end="opacity-0 scale-90"
    >你好 👋</div>
</div>
```

| 指令 | 说明 |
| --- | --- |
| :enter | 在整个进入阶段应用。 |
| :enter-start | 在触发进入过渡之前添加，在元素进入后删除一帧。 |
| :enter-end | 在元素进入后添加一帧（同时 enter-start 删除），在过渡/动画完成时删除。 |
| :leave | 在整个离开阶段应用。 |
| :leave-start | 在触发离开过渡时立即添加，在一帧后删除。 |
| :leave-end | 在触发离开过渡后添加一帧（同时 leave-start 删除），在过渡/动画完成时删除。 |