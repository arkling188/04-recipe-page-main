# Frontend Mentor - 食谱页面解决方案

这是我完成的 [Frontend Mentor Recipe page 挑战](https://www.frontendmentor.io/challenges/recipe-page-KiTsR8QQKm)。

## 概览

这个页面是一个完整的食谱详情页，包含菜品图片、标题简介、准备时间、食材列表、制作步骤和营养信息表格。

这个挑战和之前的一屏卡片项目不同，它是一个长页面。设计图本身高度超过一屏，因此页面允许滚动展示。

## 使用的技术

- HTML5
- CSS
- Flexbox
- CSS 自定义字体 `@font-face`
- 本地字体文件
- 有序列表 `ol`
- 无序列表 `ul`
- 表格 `table`

## 我学到了什么

### 1. 使用本地字体

这个项目使用了 `Young Serif` 和 `Outfit` 两种字体。

我通过 `@font-face` 引入本地字体文件：

```css
@font-face {
  font-family: "Young Serif";
  src: url("./assets/fonts/young-serif/YoungSerif-Regular.ttf");
  font-weight: 400;
}
```

然后再通过 `font-family` 使用字体。

### 2. 长页面不需要垂直居中

之前的小卡片项目适合用 `align-items: center` 做垂直居中。

但这个食谱页面是长页面，更适合只水平居中：

```css
body {
  min-height: 100vh;
  display: flex;
  justify-content: center;
}
```

再用 `.container` 的 `margin` 控制页面上下距离。

### 3. 列表样式

食材使用 `ul`，制作步骤使用 `ol`。

我还学习了使用 `::marker` 控制列表前面的点和数字：

```css
li::marker {
  color: hsl(14, 45%, 36%);
  font-weight: 700;
}
```

### 4. 营养表格

营养信息适合用 `table`，每一行用 `tr`，每个格子用 `td`。

横线通过 `border-bottom` 实现：

```css
.nutrition-table td {
  border-bottom: 1px solid hsl(30, 18%, 87%);
}
```

最后一行去掉横线：

```css
.nutrition-table tr:last-child td {
  border-bottom: none;
}
```

## 遇到的问题

### 1. 标题和段落之间为什么有默认距离

后来知道是因为浏览器会给 `h1`、`p`、`ul` 等元素自带默认样式。

解决方法是先清除默认 margin，再自己控制距离：

```css
body,
h1,
h2,
p,
ul,
ol {
  margin: 0;
}
```

### 2. `gap` 为什么在 ul 上不生效

普通 `ul` 默认不是 flex 或 grid 容器，所以直接写 `gap` 不会生效。

要使用 `gap`，需要：

```css
ul {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
```

### 3. 横线和标题之间距离过大

原因是 `hr` 的 margin 和外层区域的 margin 可能叠加。

解决思路是让一个元素负责一段距离，不要相邻元素都加 margin。

### 4. `box-sizing: border-box`

我理解了 `border-box` 会让 `width` 包含：

```text
content + padding + border
```

但不包含 `margin`。

## 继续改进

- 可以把 CSS 拆到单独的 `style.css` 文件中。
- 可以增加移动端媒体查询，让小屏幕更接近设计稿。
- 可以进一步调整字体大小、行高和间距，让页面更贴近设计图。

## 作者

- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
