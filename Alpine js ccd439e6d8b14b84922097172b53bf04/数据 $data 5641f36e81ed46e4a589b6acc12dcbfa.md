# 数据: $data

---

**`$data`**魔法允许你访问当前的 Alpine 数据范围（通常由**`x-data`**提供）。

大多数情况下，你可以直接在表达式中访问 Alpine 数据。例如**`x-data="{ message: 'Hello Caleb!' }"`**会允许你执行类似于**`x-text="message"`**的操作。

然而，有时候使用**`$data`**魔法封装作用域里的数据是有用的，你可以把数据传递给其他函数：

```html
<div x-data="{ greeting: '你好' }">
    <div x-data="{ name: '丁仪' }">
        <button @click="sayHello($data)">Say Hello</button>
    </div>
</div>
 
<script>
    function sayHello({ greeting, name }) {
        alert(greeting + '，' + name + '！')
    }
</script>
```

现在，当按下按钮时，浏览器将弹出你好，丁仪！，因为它传递了一个包含数据的实体，实体内的数据是调用它的表达式所在的 Alpine 作用域的数据（**`@click="..."`**）。

大多数应用程序都不需要这个魔法，但它对更深入、更复杂的 Alpine 程序非常有用。