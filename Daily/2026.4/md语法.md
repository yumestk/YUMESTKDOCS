#                       markdown语法
- 这是一个文档
代码块如需代码高亮则在```后面加语言
```javascript
javascript {.line-numbers}
function add(x, y) {
  return x + y
}
```

# 这是一个一级标题

## 这是一个二级标题

## 这也是二级标题

_这是一个斜体文字_
**这会是粗体文字**
~~将会被横线画一下~~

1. 这是有序列表
    - 这是无序列表
    - 这也是无序列表
2. 这是另一个有序列表
   1. 有序1
   2. 有序2

ctrl + alt + v粘贴图片

- (这是引用)
正如 Kanye West 所说：


> We're living the future so
> the present is our past.

> [!NOTE]
> This is a note blockquote.

> [!WARNING]
> This is a warning blockquote.

这是一行 行内代码`interesting`


--- 

分割线上方

代码块 class（MPE 扩展的特性）

- 你可以给你的代码块设置 class。

例如，添加 class1 class2 到一个 代码块：

```javascript {.class1 .class}
function add(x, y) {
  return x + y
}
```

代码行数
- 如果你想要你的代码块显示代码行数，只要添加 line-numbers class 就可以了。

例如：

```javascript {.line-numbers}
function add(x, y) {
  return x + y
}
```


高亮代码行数
- 你可以通过添加 highlight 属性的方式来高亮代码行数：

```javascript {highlight=10}
```

```javascript {highlight=10-20}

```

```javascript {highlight=[1-10,15,20-22]}
```
- 任务列表
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
