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

 ####Basics
 - main axis
      - main start
      - main end
      - main size (from main start to main end)
 - cross axis
      - cross start
      - cross end
      - cross size

 ####flex container style
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

 ####flex flow direction
    `flex-direction:row；`
| code | view |
|--------|--------|
|row            |行      |
|row-reverse    |行反    |
|column         |列      |
|column-reverse |列反    |

 ####flex line wrapping
	`flex-wrap:nowarp;`
| code | view |
|--------|--------|
|nowrap        |单行            |
|wrap          |多行，溢出放置新行|
|wrap-reverse  |反转            |
   - flow 和 wrap 可合并

 ####display order
 `order：-1/0/1；`自定义顺序（只改变View Order不改变Source Order）
 
 ####flexibility
 可单独可全部(main axis)
 `flex-grow:4;`是其他元素的4倍
 `flex-shrink:1;`
 `flex-basics:10em;`
 默认`flex: 0 1 auto` 分别代表grow, shrink, basics
 
 ####alignment
 - `justify-content: flex-start;`
 对齐方式 **main axis**，与flex-direction配合
| code | view |
|--------|--------|
|flex-start    |头对齐      |
|flex-end      |尾对齐      |
|center        |居中        |
|space-between |元素之间空余 |
|space-around  |元素两边空余 |
 - `align-items:flex-start;`
 对齐方式 **cross axis**
 | code | view |
|--------|--------|
|flex-start |头对齐           |
|flex-end   |尾对齐           |
|center     |居中             |
|baseline   |以文字基线对齐     |
|stretch    |拉伸填满container |
 - `align-self:flex-start;`
 单独元素对齐方式
 - `align-content: flex-start;`
 多行情况
