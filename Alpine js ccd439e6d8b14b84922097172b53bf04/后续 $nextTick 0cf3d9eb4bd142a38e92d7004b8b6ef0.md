# 后续: $nextTick

---

**`$nextTick`**魔法一个神奇的属性，它会在 Alpine 进行了响应式的 DOM 数据更新之后才执行一个给定的表达式。这在需要在完成数据更新后用 DOM 状态做交互时非常有用。

```html
<div x-data="{ title: '你好' }">
    <button
        @click="
            title = '你好，世界！';
            $nextTick(() => { console.log($el.innerText) });
        "
        x-text="title"
    ></button>
</div>
```

在上面的示例中，点击按钮后不是将“你好”输出到控制台，而是将“你好，世界！”输出到控制台，因为**`$nextTick`**魔法会等待 Alpine 完成 DOM 更新后再执行表达式。

# 承诺

---

**`$nextTick`**返回一个承诺，你可以使用**`$nextTick`**暂停一个异步函数，直到等待的 DOM 更新结束。当这样使用时，**`$nextTick`**不需要传递参数。

```html
<div x-data="{ title: '你好' }">
    <button
        @click="
            title = '你好，世界！';
            await $nextTick();
            console.log($el.innerText);
        "
        x-text="title"
    ></button>
</div>
```