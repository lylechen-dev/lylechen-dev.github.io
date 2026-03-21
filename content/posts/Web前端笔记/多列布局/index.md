---
title: "多列布局"
categories: ["Web前端笔记"]
date: 2026-03-15
---

在写微信小程序的时候就非常喜欢使用多列的布局模式，当时觉得`flex`布局不好看，特地在里面嵌套了一个`grid`布局让其更整洁。但是现在学了多列布局，虽然整体上不如`flex` 和`grid` 写的舒服和快捷，但是我还是觉得这个布局还是有一定的用武之处，比如考试。

## 概念
多列布局其实就是我们经常看见报纸，书籍上面常见的分栏方式，缺点也是非常明显，在标题行上面没有办法指定合并行数，所以`grid` 目前还是我认为的最优解。

## 语法格式
### 属性
* `column-count`：规定列数的属性
* `column-gap`：规定每列之间间距的属性
* `column-rule`：每列之间间隔的线样式的属性
* `column-width`：每列的宽度，可以和`column-count`同时使用
* `column-span`：用于横跨列的属性。只有两个值,`none`不横跨任何列，`all`横跨所有行

### 格式
```css
.elements {
    column-count: 3;
    column-gap: 3px;
    column-rule: 1px solid red;
    column-span: all;
}
```
## 案例
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>多列布局示例</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 20px;
            background-color: #f5f5f5;
        }
        
        .multi-column {
            /* 设置列数为3 */
            column-count: 3;
            /* 设置列间距 */
            column-gap: 30px;
            /* 设置列之间的分割线 */
            column-rule: 1px solid #ddd;
            max-width: 1000px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .multi-column h2 {
            /* 让标题横跨所有列 */
            column-span: all;
            text-align: center;
            color: #333;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eee;
        }
        
        .multi-column p {
            margin-bottom: 15px;
            text-align: justify;
        }
        
        @media (max-width: 768px) {
            .multi-column {
                column-count: 2;
            }
        }
        
        @media (max-width: 480px) {
            .multi-column {
                column-count: 1;
            }
        }
    </style>
</head>
<body>
    <div class="multi-column">
        <h2>多列布局示例</h2>
        <p>这是第一列的内容。多列布局是一种将内容自动分布到多个列中的CSS技术，类似于报纸的排版方式。这种布局特别适合展示大量的文本内容。</p>
        <p>通过简单的CSS属性，我们可以控制列的数量、间距和样式，而无需复杂的HTML结构。</p>
        <p>这是第二列的内容。多列布局会自动平衡各列的内容高度，使阅读体验更加舒适。当内容超过一列时，会自动流入下一列。</p>
        <p>使用多列布局可以创建出类似印刷品的视觉效果，同时保持内容的可访问性和响应式特性。</p>
        <p>这是第三列的内容。在多列布局中，我们可以使用column-span属性让某些元素横跨所有列，比如标题或重要的图片。</p>
        <p>通过媒体查询，我们可以为不同屏幕尺寸设置不同的列数，确保在各种设备上都有良好的显示效果。</p>
    </div>
</body>
</html>
```