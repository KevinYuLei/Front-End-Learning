# HTML学习笔记 Part05-CSS层叠样式表 三

## 目录
1. CSS的三大特性
2. CSS的注释
3. 盒子模型
4. PS基本操作
5. 综合案例
6. 四角边框
7. 盒子阴影
8. 文字阴影

<!--more-->

## 1. CSS的三大特性
CSS由三个非常重要的特性：层叠性、继承性、优先级。

### 1.1 层叠性
给相同选择器设置相同的样式，此时一个样式就会 **覆盖（层叠）** 另一个冲突的样式。层叠性主要解决样式冲突的问题。

层叠性原则：
- 样式冲突，遵循的原则是**就近原则**，哪个样式离结构近，就执行哪个样式（代码一行一行由上往下执行）
- 样式不冲突，不会层叠

### 1.2 继承性
子标签会继承父标签的某些样式，如文本颜色和字号。

- 恰当地使用继承可以简化代码，降低CSS样式的复杂性。
- 子元素可以继承父元素的样式（text-，font-，line-这些元素开头的可以继承，以及color属性）

**行高的继承性**

```css
body {
    font: 12px/1.5 Microsoft YaHei;
}
```
- 行高可以跟单位也可以不跟单位
- 如果子元素没有设置行高，则会继承父元素的行高1.5
- 此时子元素的行高是：当前子元素的文字大小*1.5
- body行高1.5这样的写法最大的优势就是里面子元素可以根据自己文字大小自动调整行高

### 1.3 优先级
当同一个元素指定多个选择器，就会有优先级的产生

- 选择器相同，则执行层叠性
- 选择器不同，则根据**选择器权重**执行

#### 1.3.1 选择器权重

选择器权重如下表所示。

<table>
    <tr style="text-align: left"><th>选择器</th><th>选择器权重</th></tr>
    <tr><td>继承 或者 *（通配符）</td><td>0,0,0,0</td></tr>
    <tr><td>元素选择器（标签选择器）</td><td>0,0,0,1</td></tr>
    <tr><td>类选择器、伪类选择器</td><td>0,0,1,0</td></tr>
    <tr><td>ID选择器</td><td>0,1,0,0</td></tr>
    <tr><td>行内样式style=""</td><td>1,0,0,0</td></tr>
    <tr><td>!important 重要的</td><td>∞ 无穷大</td></tr>
</table>

**理解：**选择器的指定范围越精确则其权重最高

**优先级注意点：**
- 权重是由4组数字组成，但是不会有进位
- 可以理解为类选择器永远大于元素选择器，id选择器永远大于类选择器，以此类推
- 等级判断从左向右，如果某一位数值相同，则判断下一位数值
- 可以简单记忆：通配符和继承权重为0，标签选择器为1，类（伪类）选择器为10，id选择器为100，行内样式表为1000，!important为无穷大
- **继承的权重是0**，如果该元素没有直接选中，不管父元素权重多高，子元素得到的权重都是0
- 通过上条，可知：看标签执行哪个样式，先看该标签是否直接被选择还是继承的

#### 1.3.2 权重叠加

**权重叠加：** 如果是复合选择器，则会有权重叠加，需要计算权重。

例题如下：
- div ul li&nbsp;&nbsp;&nbsp;------> 0,0,0,3
- .nav ul li ------> 0,0,1,2
- a:hover&nbsp;&nbsp;------> 0,0,1,1
- .nav a&nbsp;&nbsp;&nbsp;&nbsp;------> 0,0,1,1

## 2. CSS的注释
CSS的注释格式同C语言，代码如下

```css
/* 我是注释 */
```

## 3. 盒子模型
页面布局要学习三大核心：盒子模型、浮动、定位。

学习好**盒子模型**能很好地帮助布局页面。

### 3.1 看透网页布局的本质
网页布局过程：
1. 先准备好相关的网页元素，网页元素基本都是盒子Box
2. 利用CSS设置好盒子样式，然后拜访到相应位置
3. 往盒子里装内容

网页布局的**核心本质：** 利用CSS摆盒子。

### 3.2 盒子模型（Box Model）组成
所谓**盒子模型**：就是把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。

CSS盒子模型本质上是一个盒子，封装周围的HTML元素，它包括：
边框（border）、外边距（margin）、内边距（padding）、实际内容（content）。

<img src="images/box_model.jpg" alt="盒子模型" title="盒子模型">

### 3.3 边框（border）
**border**可以设置元素的边框。边框有三部分组成：
- 边框宽度（粗细）
- 边框样式
- 边框颜色

语法：

```css
border: border-width || border-style || border-color
```

<table>
    <tr style="text-align: left;"><th>属性</th><th>作用</th></tr>
    <tr><td>border-width</td><td>定义边框的粗细，单位是px</td></tr>
    <tr><td>border-style</td><td>定义边框的样式</td></tr>
    <tr><td>border-color</td><td>定义边框的颜色</td></tr>
</table>

CSS的边框属性**border**允许你指定一个元素边框的**样式**和**颜色**

边框简写：

```css
border: 5px solid pink; /* 没有顺序 */
```

```css
/* CSS */
<style>
    .box1 {
        width: 300px;
        height: 200px;
        /*border-width: 5px;
        border-style: solid;
        border-color: pink;*/
        border: 5px solid pink;
    }
</style>
```

```html
<!--HTML-->
<body>
    <div class="box1">我是盒子1</div>
</body>
```

显示效果如下：

<style>
    .box1 {
        width: 300px;
        height: 200px;
        /*border-width: 5px;
        border-style: solid;
        border-color: pink;*/
        border: 5px solid pink;
    }
</style>

<body>
    <div class="box1">我是盒子1</div>
</body>

边框分开写法：

```css
border-top: 1px solid red; /* 只设定上边框，其余同理 */
```

**练习：**
请给一个200*200的盒子，设置上边框为红色，其余边框为蓝色（提示：注意边框的层叠性）

```css
/* CSS */
<style>
    .box2 {
        width: 200px;
        height: 200px;
        border: 1px solid blue;
        border-top: 1px solid red; 
    }
</style>
```

```html
<!--HTML-->
<body>
    <div class="box2">我是盒子2</div>
</body>
```

显示效果如下：

<style>
    .box2 {
        width: 200px;
        height: 200px;
        border: 1px solid blue;
        border-top: 1px solid red; 
    }
</style>
<body>
    <div class="box2">我是盒子2</div>
</body>

### 3.4 表格的细线边框
**border-collapse**属性控制浏览器绘制表格边框的方式，控制相邻单元格的边框。

语法：

```css
border-collapse: collapse; /* 合并相邻的边框 */
```

- collapse单词是倒塌、折叠（合并）的意思

## 4. PS基本操作
## 5. 综合案例
## 6. 四角边框
## 7. 盒子阴影
## 8. 文字阴影