##Modern Layout
###Flexbox
- What is Flexbox？
   - A set of CSS Properties
   - Creating Flexible Layouts
   - distributing Extra Space
   - Aligning Content

- Arrange items in any direction items in any direction(easyly to rearrange)
   - left to right
   - right to left
   - top to bottom
   - bottom to left

 #### Basics
- main axis
     - main start
     - main end
     - main size (from main start to main end)
- cross axis
     - cross start
     - cross end
     - cross size

 ####Flex Container Style
``` 
.flex-container{
    display: flex;
    flex-wrap:;
    flex-direction:;
    justify-content:;
    align-items:;
    align-content:;
 }
 .flex-item{
    flex-grow:;
 }
 .flex-item:first-child{
    flex-grow:;
    align-self:;
    order:;
 }
 .flex-item:nth-child{
 }
```
- `display: inline-flex;` 与子元素大小自适应

 ####Flex Flow Direction
    `flex-direction:row；`
| code           | view |
| -------------- | ---- |
| row            | 行    |
| row-reverse    | 行反   |
| column         | 列    |
| column-reverse | 列反   |

 ####Flex Line Wrapping
	`flex-wrap:nowarp;`
| code         | view      |
| ------------ | --------- |
| nowrap       | 单行        |
| wrap         | 多行，溢出放置新行 |
| wrap-reverse | 反转        |
- flow 和 wrap 可合并

 ####Display Order
 `order：-1/0/1；`自定义顺序（只改变View Order不改变Source Order）

 ####Flexibility
 可单独可全部(main axis)
 `flex-grow:4;`是其他元素的4倍
 `flex-shrink:1;`
 `flex-basics:10em;`
 默认`flex: 0 1 auto` 分别代表grow, shrink, basics

 ####Alignment
- `justify-content: flex-start;`
    对齐方式 **main axis**，与flex-direction配合
| code          | view   |
| ------------- | ------ |
| flex-start    | 头对齐    |
| flex-end      | 尾对齐    |
| center        | 居中     |
| space-between | 元素之间空余 |
| space-around  | 元素两边空余 |
- `align-items:flex-start;`
    对齐方式 **cross axis**
| code       | view          |
| ---------- | ------------- |
| flex-start | 头对齐           |
| flex-end   | 尾对齐           |
| center     | 居中            |
| baseline   | 以文字基线对齐       |
| stretch    | 拉伸填满container |
- `align-self:flex-start;`
    单独元素对齐方式
- `align-content: flex-start;`
    多行情况

###CSS Grid
| Flexbox                  | CSS Grid                    |
| ------------------------ | --------------------------- |
| one dimension            | two dimensions              |
| lets content size itself | relies on defined gridlines |

- Grid Container
- Grid Lines (Rows and Column)
- Grid Tracks (Rows and Column)
- Grid Cells
- Grid Area (由四条Grid Lines组成，包括任意数量Cell)


 ####Grid Style
``` 
.grid-container{
    display: grid/inline-grid;
    grid:;
    grid-auto-flow:;
 }
 .grid-item{
  
 }
 .grid-item:first-child{
    grid-area:;
    order:;
 }
 .grid-item:nth-child{
 }
```
 ####Setting up a Grid
- Difining Columns & Rows
    `grid-template-rows: height height height;`
    `grid-template-columns: width width width;`
    合并成：
    `grid: column column/ row row;`
    使用`grid-template-rows: repeat(3, 1em 6em);`重复相同的单元格

- Placing Grid Items 
    `grid-column-start: 1;`
    `grid-column-end: 2;`
    `grid-row-start: 3;`
    `grid-row-end: 4;`
    合并成：
    `grid-area: row-start/ column-start/ row-end/ column-end;`
    或者用`gird-row: 2/ span 3;`代替

 ####Auto Grid Features
 `grid-auto-flow；row/column/dense;` 排列方向

 ####Naming Grid Lines & Grid Areas
- Grid Lines
 ```
.grid-container:{
    gird:[main-content-start] 1fr [main-content-end] 1em [sidebar-start] 25% [siderbar-end]/ 6em 1em 1fr;
    }
.grid-item-content:{
	grid-column: main-content-start/ main-content-end;
}
 ```
使用repeat，名字后面空格加序号

- Grid Areas
 ```
 grid-area: name;
 grid-template-areas:"name name name"
                      ". . ."
                      "name . name";
 ```
 重复名字占满所有column, 空白用` . `(加空格)

- auto 根据内容自适应
- fr 剩余空间根据比例分配
- 可以overlap，使用`z-index`设置上下顺序
 ####Alignment Properity
 justify-content
 justify-items   横向
 align-content
 align-items 纵向
 justify-self
 align-self

###Gotchas, Browser support, & Resources
 ####Resources
- [Rachel Andrew](http://rachelandrew.co.uk)
- [Css Layout Newsletter](http://csslayout.news)
- [Grid By Example](http://gridbyexample.com)
- [A Visual Guide to Flexbox Properties](http://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properities)
- [Complete Guide to Flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox)
- [Complete Guide to Grid](http://css-tricks.com/snippets/css/complete-guide-grid)





