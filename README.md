# Alpine.js

---

本文是 Alpine.js 官方文档的拙劣翻译，因为在学习时并没有找到 Alpine 3 的中文文档，所以在配合机翻学习 Alpine.js 时顺带做了一下翻译。

如有纰漏，欢迎指正。

官方文档：

[Start Here — Alpine.js](https://alpinejs.dev/start-here)  

[Notion](https://yujianghan.notion.site/Alpine-js-ccd439e6d8b14b84922097172b53bf04)

# 安装

---

[安装](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%AE%89%E8%A3%85%20722568095e144c0d85da5506f186bb2d.md)

# 指令

---

指令为 Alpine 为 HTML 标签定义的特殊的属性。

[数据: x-data](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%95%B0%E6%8D%AE%20x-data%200ebab51629c943f68a0fd1f25e0c37d2.md)

[初始化: x-init](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%88%9D%E5%A7%8B%E5%8C%96%20x-init%20eb4378e7f44f4c99b1f3c3727f4d45d5.md)

[显示: x-show](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%98%BE%E7%A4%BA%20x-show%20852d0974df4e4fb7b0d812e6df8dc4ca.md)

[绑定: x-bind](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%BB%91%E5%AE%9A%20x-bind%206e9ad8b7f4ec46b4a6f70cd0a0a72f43.md)

[监听: x-on](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%9B%91%E5%90%AC%20x-on%20d53a0d61b4d644bca70247cf6d5e135f.md)

[文本: x-text](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%96%87%E6%9C%AC%20x-text%201aa819295953456a84319ecbfe26f8d7.md)

[超文本: x-html](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E8%B6%85%E6%96%87%E6%9C%AC%20x-html%2041adf05c1f2840f5869f2a656207fcd9.md)

[双向绑定: x-model](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%8F%8C%E5%90%91%E7%BB%91%E5%AE%9A%20x-model%209672f919b6cd45b1af0d4db9a3a2276f.md)

[可双向绑定: x-modelable](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%8F%AF%E5%8F%8C%E5%90%91%E7%BB%91%E5%AE%9A%20x-modelable%20fb959d59133c427aac4691c60bb1debf.md)

[遍历: x-for](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E9%81%8D%E5%8E%86%20x-for%20a0bf2dd9c90a4965a1b748d72811ca71.md)

[过渡: x-transition](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E8%BF%87%E6%B8%A1%20x-transition%200863fca2c49649a4bfffd43ee954042f.md)

[影响: x-effect](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%BD%B1%E5%93%8D%20x-effect%20f0e97d1a60f64099a0c8cd6592b6be08.md)

[忽略: x-ignore](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%BF%BD%E7%95%A5%20x-ignore%20e19b1841af234ecdbcc54f46484f8698.md)

[参照: x-ref](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%8F%82%E7%85%A7%20x-ref%200539997b5eed4f6ca9602ca76d684c1e.md)

[隐身衣: x-cloak](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E9%9A%90%E8%BA%AB%E8%A1%A3%20x-cloak%20936381c877684cef954226d064212828.md)

[传输: x-teleport](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E4%BC%A0%E8%BE%93%20x-teleport%209e43be43325c47dca78feb989b082e35.md)

[判断: x-if](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%88%A4%E6%96%AD%20x-if%20a77602c35bdc4d4596cb5b542b31c5df.md)

[编号: x-id](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%BC%96%E5%8F%B7%20x-id%205af9dd8f2a4d435685e544bb817cd9a9.md)

# 魔法

---

[自身: $el](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E8%87%AA%E8%BA%AB%20$el%204fc52ed627124c74b0648a41ea47b234.md)

[选择: $refs](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E9%80%89%E6%8B%A9%20$refs%20aecef58027974ad69136f1a67481c6a4.md)

[全局: $store](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%85%A8%E5%B1%80%20$store%200dabf63a2fd14416866fb4cc77aab0bc.md)

[监视: $watch](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%9B%91%E8%A7%86%20$watch%20753f5cf480d440019235e7185bf30183.md)

[分派: $dispatch](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%88%86%E6%B4%BE%20$dispatch%202dd2487c34f34a6d95a168c3d09f7665.md)

[后续: $nextTick](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%90%8E%E7%BB%AD%20$nextTick%200cf3d9eb4bd142a38e92d7004b8b6ef0.md)

[根: $root](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%A0%B9%20$root%202fb70fcd4092459ea35a754fe9f62679.md)

[数据: $data](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%95%B0%E6%8D%AE%20$data%205641f36e81ed46e4a589b6acc12dcbfa.md)

[编号: $id](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%BC%96%E5%8F%B7%20$id%2010a02d55df6c4e88bda2161d4f2da997.md)

# 全局

---

[数据: Alpine.data](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E6%95%B0%E6%8D%AE%20Alpine%20data%20465da3509c054afb878dade2d27617da.md)

[全局: Alpine.store](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E5%85%A8%E5%B1%80%20Alpine%20store%208123650a52814de78e792cb46424dc0a.md)

[绑定: Alpine.bind](Alpine%20js%20ccd439e6d8b14b84922097172b53bf04/%E7%BB%91%E5%AE%9A%20Alpine%20bind%20dc4513e362414105bea19f878cb0d9d5.md)
