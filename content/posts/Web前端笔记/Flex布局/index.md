---
title: "Flex布局"
categories: ["Web前端笔记"]
date: 2026-03-15
---

之前在暑假的时候自己写过一段事件的小程序，当时对于`Flex`布局有过初步的了解，当时在写完小程序之后我还记得我说过，布局只要有`Flex`和`Grid`其他的都不重要。当时觉得这个布局十分的好用，但是并没有深入的去了解，但是经过深度学习之后，感觉比自己去摸索懂得会更透彻一些。

## 概念

**`Flex`布局元素：**

- `Flex`容器：采用`Flex`布局的元素，作为父元素
- `Flex`项目：`Flex`布局内的子元素

**`Flex`容器中有以下两个基本的概念：**

- 主轴（`main axis`）：控制项目顺序的轴，方向根据`flex-direction`改变
- 交叉轴（`cross axis`）：与主轴水平垂直的轴

## 容器的属性

- `flex-direction`
- `flex-wrap`
- `flex-flow`
- `justify-content`
- `align-items`
- `align-cotent`

### `flex-direction`

- `row`（**默认值**）：主轴为水平方向，起点在左端
- `row-reverse`：主轴为水平方向，起点在右端
- `column`：主轴为垂直方向，起点在上方
- `column-reverse`：主轴为垂直方向，起点在下方

### `flex-wrap`

- `nowrap`（**默认值**）：不换行
- `wrap`：自动换行，第一行在开头
- `wrap-reverse`：自动换行，第一行在末尾

### `justify-content`

- `flex-start`（默认值）：左对齐
- `flex-end`：右对齐
- `center`：居中
- `space-between`：两端贴边，项目之间的间隔都相等
- `space-around`：每个项目两侧的间隔相等，项目到边距的间距是两个项目的一半
- `space-evenly`：每个项目之间，项目和边距之间相等

### `align-items`

- `stretch`（**默认值**）：默认拉伸填满整个容器
- `flex-start`：交叉轴的起点对齐
- `flex-end`：交叉轴的终点对齐
- `center`：交叉轴的中点对齐
- `baseline`：项目的第一行文字的基线对齐

### `align-content`（只有设置`flex-wrap`属性之后才会生效）

- `flex-start`：与交叉轴的起点对齐
- `flex-end`：与交叉轴的终点对齐
- `cneter`：与交叉轴的中点对齐
- `space-between`：与交叉轴两端对齐，轴线之间的间隔平均分布
- `space-around`：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍
- `space-evenly`：每行之间，边上两行到边距的距离都相等

### `flex-flow`（`flex-direction`属性和`flex-wrap`属性的简写形式）

- 格式：`flex-flow: <flex-direction> <flex-wrap>`

## 项目的属性

- `order`：设置排序顺序

# 项目展示
## 源码
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>05 响应式表单布局</title>
    <style>
:root {
  --primary-color: #4a6ee0;
  --primary-light: #eef2ff;
  --primary-dark: #3a5ac8;
  --text-primary: #2d3748;
  --text-secondary: #718096;
  --border-color: #e2e8f0;
  --background-color: #f8fafc;
  --white: #ffffff;
  --success-color: #48bb78;
  --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
  --transition: all 0.3s ease;
}

body {
  background-color: var(--background-color);
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  color: var(--text-primary);
  padding: 20px;
  min-height: 100vh;
}

form {
  max-width: 900px;
  margin: 0 auto;
  padding: 40px;
  box-sizing: border-box;
  border-radius: 12px;
  font-size: 16px;
  background-color: var(--white);
  box-shadow: var(--shadow);
  transition: var(--transition);
}

form:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
    0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

label {
  color: var(--text-primary);
  font-weight: 500;
  transition: var(--transition);
}

input {
  font-size: 16px;
  color: var(--text-primary);
  outline: none;
  padding: 12px 16px;
  border-radius: 8px;
  border: 1px solid var(--border-color);
  box-sizing: border-box;
  transition: var(--transition);
  background-color: var(--white);
}

input:focus {
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(74, 110, 224, 0.2);
}

input:valid {
  border-color: var(--border-color);
}

input:valid:focus {
  border-color: var(--primary-color);
}

.submit {
  color: var(--white);
  background-color: var(--primary-color);
  cursor: pointer;
  font-weight: 600;
  border: none;
  padding: 14px 16px;
  transition: var(--transition);
}

.submit:hover {
  background-color: var(--primary-dark);
  transform: translateY(-2px);
}

.submit:active {
  transform: translateY(0);
}

    </style>
</head>
<body>
<style>
  /* 请使用 flexbox 布局实现响应式表单 */
  form {
    display: flex;
    align-items: flex-end;
    gap: 24px;
    flex-wrap: wrap;
  }
  .name, .password {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .name, .password, .submit {
    flex: 1 1 200px;
  }
</style>
<form action="#" method="post">
  <label for="name" class="name"
    >姓名：
    <input type="text" id="name" name="name" required="" />
  </label>
  <label for="password" class="password"
    >密码：
    <input type="password" id="password" name="password" required="" />
  </label>
  <input type="submit" class="submit" value="提交" />
</form>

    <script>

    </script>
</body>
</html>
```

[**更多见Reference教程**](https://ref.lylebox.dpdns.org:8443/docs/css.html#css-flexbox)
