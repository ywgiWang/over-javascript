## 一 rem 适配布局概念

一些传统布局的缺陷：

- 传统布局、flex 布局中，文字都不能随着屏幕大小变化而变化
- 流式布局和 flex 布局主要针对宽度进行布局，高度该如何更高的设置
- 在屏幕发生变化时，如何让元素的高度、宽度进行等比例缩放

rem（root em）是一个相对单位，类似于 em，em 是父元素的字体大小，而 rem 是基于 html 元的字体大小。比如 html 设置了 `font-size=10px`，某个非根元素设置 `width:2rem;` 换算为 px 就是 20px。

布局：当使用 rem 作为单位时，只要 html 元素中的字体大小发生改变，那么整体的布局就会相应发生改变。

## 二 媒体查询

媒体查询（Media Query）是 CSS3 引入的新技术，可以针对不同的屏幕尺寸设置不同的样式，在重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面！

示例：

```css
/*
声明媒体查询：@media
参数一：mediatype，媒体类型，值有：
        all：用于所有设备
        print：用于打印机和打印预览
        screen：用于电脑、平板、手机等

参数二： 用于连接参数1与参数二，为 and not only 等值
        and：可以将多个媒体特性连接到一起，即： 且
        not：排除某个媒体类型，即：非，可以省略
        only：指定某个特性的特性，可以省略
参数二：media feature 特性，必须有小括号包含    
        width: 可视区宽度
        min-width：可视区最小宽度
        max-width：可视区最大宽度
*/
@media screen and (max-width: 800px) {
  /* 在屏幕中，且设置最大宽度为800px */
  body {
    background-color: pink;
  }
}

@media screen and (max-width: 500px) {
  body {
    background-color: green;
  }
}
```

## 三 rem 与媒体查询配合实现移动端布局

配合使用案例：

```css
@media (min-width: 320px) {
  html {
    font-size: 50px;
  }
}

@media (min-width: 640px) {
  html {
    font-size: 100px;
  }
}
```

使用媒体查询引入资源可以更好的实现移动端布局：

```css
/* 针对不同的屏幕尺寸，引入不同的css资源 */
<link rel="stylesheet" href="" media="screen and (min-width:320px)">
<link rel="stylesheet" href="" media="screen and (min-width:640px)">
```
