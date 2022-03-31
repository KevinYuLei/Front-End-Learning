<h1>CSS学习笔记 Part05</h1>

<style>
    .red {
        color: red;
    }
</style>

<strong>目录</strong>
<a href="#title01">1. 定位</a>
<a href="#title02">2. 综合案例</a>
<a href="#title03">3. 网页布局总结</a>
<a href="#title04">4. 元素的显示与隐藏</a>

<h2 id="title01">1. 定位</h2>

<h3>1.1 为什么需要定位</h3>

1. 某个元素可以自由地在一个盒子内移动位置，并且压住其他盒子
2. 当滚动窗口时，盒子是固定在屏幕某个位置的

以上效果，标准流或浮动都无法快速实现，此时需要<span class="red">定位</span>来实现

所以：
1. 浮动可以让多个块级盒子一行没有缝隙排列显示，经常用于横向排列盒子
2. 定位则是可以让盒子自由地在某个盒子内移动位置或者固定品目中某个位置，并且可以压住其他盒子

<h3>1.2 定位组成</h3>

定位：将盒子定在某一个位置，所以定位也是在摆放盒子，按照定位的方式移动盒子

定位=定位模式+边偏移

定位模式用于指定一个元素在文档中的定位方式。边偏移则决定了该元素的最终位置。

<h4>1.2.1 定位模式</h4>

定位模式决定怨怒是的定位方式，通过CSS的position属性来设置，有四个值


<table>
    <thead>
        <tr>
            <th>值</th>
            <th>语义</th>
        </tr>
    </thead>
    <tbody>
        <tr><td>static</td><td>静态定位</td></tr>
        <tr><td>relative</td><td>相对定位</td></tr>
        <tr><td>absolute</td><td>绝对定位</td></tr>
        <tr><td>fixed</td><td>固定定位</td></tr>
    <tbody>
</table>

<h4>1.2.2 边偏移</h4>

边偏移就是定位的盒子移动到最终位置。有top、bottom、left、right四个属性

<table>
    <thead>
        <tr>
            <th>边偏移属性</th>
            <th>示例</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>top</td>
            <td>top: 80px</td>
            <td>顶部偏移量，定义元素相对于其父元素上边线的距离</td>
        </tr>
        <tr>
            <td>bottom</td>
            <td>bottom: 80px</td>
            <td>底部偏移量，定义元素相对于其父元素下边线的距离</td>
        </tr>
        <tr>
            <td>left</td>
            <td>left: 80px</td>
            <td>左侧偏移量，定义元素相对于其父元素左边线的距离</td>
        </tr>
        <tr>
            <td>right</td>
            <td>right: 80px</td>
            <td>右侧偏移量，定义元素相对于其父元素右边线的距离</td>
        </tr>
    <tbody>
</table>

<h3>1.3 静态定位</h3>

静态定位是元素的默认定位方式，无定位的意思

语法：
```css
选择器 { position: static; }
```

- 静态定位按照标准流特性拜访位置，没有边偏移
- 静态定位在布局时很少用到

<h3>1.4 相对定位</h3>

<strong class="red">相对定位</strong>是元素移动位置的时候，是相对于它<span class="red">原来的位置</span>来说的

语法：
```css
选择器 { position: relative; }
```

相对定位的特点：
1. 它是相对于自己原来的位置来移动的（<span class="red">移动位置的时候参照点是自己原来的位置</span>）
2. 原来在标注流的位置继续占有，后面的盒子仍然以标注流的方式对待它。（<span class="red">不脱标，继续保留原来位置</span>）

<h3>1.4 相对定位</h3>

<strong class="red">绝对定位</strong>是元素移动位置的时候，是相对于它<span class="red">祖先元素</span>来说的

语法：
```css
选择器 { position: absolute; }
```

相对定位的特点：
1. 如果<span class="red">没有祖先元素</span>或者<span class="red">祖先元素没有定位</span>，则以浏览器为准定位（Document文档）
2. 如果祖先元素有定位（相对、绝对、固定定位），则以最近一级有定位的祖先元素为参考点移动位置
3. 绝对定位<span class="red">不再占有原先的位置</span>（脱标）

<h3>1.5 子绝父相的由来</h3>

子绝父相：子级是绝对定位的话，父亲要用相对定位

1. 子级绝对定位，不会占有位置，可以放到父级盒子里面的任何一个地方，不会影响其他的兄弟盒子
2. 父级盒子需要加定位限制子盒子在父级盒子内显示
3. 父级盒子布局时，需要占有位置，因此父级只能时相对定位

<h3>1.6 案例：学成在线-hot new 模块添加</h3>
略

<h3>1.7 固定定位</h3>

<strong class="red">固定定位</strong>是元素<span class="red">固定于浏览器可视区的位置</span>。主要使用场景：可以在浏览器页面滚动时元素的位置不会改变

语法：
```css
选择器 { position: fixed; }
```

固定定位的特点：
1. 以浏览器的可视窗口为参照点移动元素
    - 跟父元素没有任何关系
    - 不随滚动条滚动
2. 固定定位<span class="red">不再占有原先的位置</span>（脱标）

固定定位小技巧：固定在版心右侧位置
1. 让固定定位的盒子 left: 50%;走到浏览器可视区（版心）的一半位置
2. 让固定定位的盒子 margin-left: 版心宽度的一半距离，多走版心宽度的一半位置

<h3>1.8 粘性定位</h3>

<strong class="red">粘性定位</strong>可以被认为是相对定位和固定定位的混合。跟页面滚动搭配使用，兼容性较差。IE不支持

语法：
```css
选择器 { position: sticky; }
```

粘性定位的特点：
1. 以浏览器的可视窗口为参照移动元素（固定定位的特点）
2. 粘性定位占有原先的位置（相对定位的特点）
3. 必须添加top、left、right、bottom其中一个才有效

<h3>1.9 定位总结</h3>

<table>
    <thead>
        <tr>
            <th>定位模式</th>
            <th>是否脱标</th>
            <th>移动位置</th>
            <th>是否常用</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>static静态定位</td>
            <td>否</td>
            <td>不能使用边偏移</td>
            <td>很少</td>
        </tr>
        <tr>
            <td>relative相对定位</td>
            <td>否（占有位置）</td>
            <td>相对于自身位置移动</td>
            <td>常用</td>
        </tr>
        <tr>
            <td>absolute绝对定位</td>
            <td>是（不占有位置）</td>
            <td>带有定位的父级</td>
            <td>常用</td>
        </tr>
        <tr>
            <td>fixed固定定位</td>
            <td>是（不占有位置）</td>
            <td>浏览器可视区</td>
            <td>常用</td>
        </tr>
        <tr>
            <td>sticky粘性定位</td>
            <td>否（占有位置）</td>
            <td>浏览器可视区</td>
            <td>目前阶段少</td>
        </tr>
    </tbody>
</table>

<h3>1.10 定位叠放次序</h3>

在使用定位布局时，可能会出现盒子重叠的情况。此时，可以使用<span class="red">z-index</span>来控制盒子的前后次序（z轴）

语法：
```css
选择器 { z-index: 1; }
```

注意：
1. 数值可以是正整数、负整数、0，默认是auto，数值越大，盒子越靠上
2. 如果属性值相同，则按照书写顺序，后来居上
3. 数字后面不能加单位
4. 只有定位的盒子才用z-index属性

<h3>1.11 定位的拓展</h3>

<h4>1. 绝对定位的盒子居中</h4>

加了绝对定位的盒子不能通过<span class="red">margin: 0 auto;</span>水平居中，但是可以通过以下计算方法实现水平和垂直居中：
1. left: 50%; ：让盒子的左侧移动到父级元组的水平中心位置
2. margin-left: -100px; 让盒子向左移动自身宽度的一半

注意：相对定位的盒子可以使用<span class="red">margin: 0 auto;</span>水平居中

<h4>2. 定位特殊特性</h4>

绝对定位和固定定位也和浮动类似：（类似行内块元素）
1. 行内元素添加绝对或者固定定位，可以直接设置高度和宽度
2. 块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小

<h4>3. 脱标的盒子不会触发外边距塌陷</h4>

浮动元素、绝对定位、固定定位的元素都不会出发外边距合并的问题

<h4>4. 绝对定位/固定定位会完全压住盒子</h4>

浮动元素不同，只会压住它下面标准流的盒子，但不会压住下面标准流盒子里面的文字/图片

但是绝对定位/固定定位会压住下面标准流盒子的所有内容

浮动定位之所以不会压住文字，因为浮动产生的目的最初是为了做文字环绕效果的。文字会围绕浮动元素

<h2 id="title02">2. 综合案例：淘宝焦点图布局</h2>

<h3>2.1 布局制作流程</h3>

1. 大盒子类名：tb-promo 淘宝推广
2. 里面先放一张图片
3. 左右两个按钮使用链接。左箭头prev，右箭头next
4. 底侧小圆点使用ul制作，类名：promo-nav

注意：如果一个盒子既有left属性也有right属性，默认执行left，同理，对top默认。

<h3>2.2 案例代码</h3>

案例代码如下：
```html
<!DOCTYPE html>
<html lang="zh-cn">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>淘宝轮播图做法</title>
</head>
<style>
    * {
        margin: 0;
        padding: 0;
    }
    li {
        list-style: none;
    }
    .tb-promo {
        position: relative;
        width: 520px;
        height: 280px;
        background-color: pink;
        margin: 100px auto;
    }
    .tb-promo img {
        width: 520px;
        height: 280px;
    }
    .prev,
    .next {
        position: absolute;
        top: 50%;
        margin-top: -15px;
        width: 20px;
        height: 30px;
        background-color: rgba(0, 0, 0, 0.3);
        text-align: center;
        line-height: 26px;
        text-decoration: none;
        color: #fff;
    }
    .prev {
        left: 0;
        border-top-right-radius: 15px;
        border-bottom-right-radius: 15px;
    }
    .next {
        right: 0;
        border-top-left-radius: 15px;
        border-bottom-left-radius: 15px;
    }
    .promo-nav {
        position: absolute;
        bottom: 15px;
        left: 50%;
        margin-left: -35px;
        width: 70px;
        height: 13px;
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 7px;
    }
    .promo-nav li {
        float: left;
        margin: 3px;
        width: 8px;
        height: 8px;
        background-color: #fff;
        border-radius: 50%;
    }
    .promo-nav li:hover {
        cursor: pointer;
    }
    .promo-nav .selected {
        background-color: #ff5000;
    }
</style>
<body>
    <div class="tb-promo">
        <img src="images/01.jpg" alt="">
        <a href="#" class="prev">&lt;</a>
        <a href="#" class="next">&gt;</a>
        <ul class="promo-nav">
            <li class="selected"></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
</body>
</html>
```

<h2 id="title03">3. 网页布局总结</h2>

通过盒子模型，清楚知道大部分html标签是盒子

通过CSS浮动、定位可以让每个盒子排列成网页

一个完整的网页，是标准流、浮动、定位一起完成布局的，每个都有自己的专门用法

1. 标准流
可以让盒子上下排列或者左右排列，<span class="red">垂直的块级盒子显示就用标注流布局</span>
2. 浮动
可以让多个块级元素一行显示或者左右对齐盒子，<span class="red">多个块级盒子水平显示就用浮动布局</span>
3. 定位
定位最大的特点就是有层叠的概念，就是可以让多个盒子前后叠压来显示。<span class="red">如果元素自由在某个盒子内移动就用定位布局</span>

<h2 id="title04">4. 元素的显示与隐藏</h2>

类似网站广告，当点击关闭不见了，但是重新刷新页面，会重新出现
本质：<span class="red">让一个元素在页面中隐藏或者显示出来</span>

<h3>4.1 display属性</h3>

display属性用于设置一个元素应该如何显示

- display: none; 隐藏对象
- display: block; 除了转换为块级元素，同时还有显示元素的意思

<span class="red">display隐藏元素后，不再占有原来的位置</span>
后面应用极其广泛，搭配JS可以做很多网页特效

<h3>4.2 visibility属性</h3>

<span class="red">visibility属性用于指定一个元素应可见还是隐藏</span>

- visibility: visible; 元素可见
- visibility: hidden; 元素隐藏

<span class="red">visibility隐藏元素后，继续占有原来的位置</span>

如果隐藏元素想要原来位置，就用visibility: hidden;
如果隐藏元素不想要原来位置，就用display: none;（用处更多，重点）

<h3>4.3 overflow溢出</h3>

<span class="red">overflow属性</span>指定了如果内容溢出一个元素的框（超过其指定高度及宽度）时，会发生什么

<table>
    <thead>
        <tr>
            <th>属性值</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>visible</td>
            <td>不剪切内容也不添加滚动条</td>
        </tr>
        <tr>
            <td>hidden</td>
            <td>不显示超过对象尺寸的内容，超出的部分隐藏掉</td>
        </tr>
        <tr>
            <td>scroll</td>
            <td>不管超出内容与否，总是显示滚动条</td>
        </tr>
        <tr>
            <td>auto</td>
            <td>超出自动显示滚动条，不超出不显示滚动条</td>
        </tr>
    </tbody>
</table>

一般情况下，不想让溢出的内容显示出来，因为溢出的部分会影响布局

但是如果有定位的盒子，请慎用overflow: hidden;因为它会隐藏多余的部分

<h3>案例：土豆网鼠标经过显示遮罩</h3>

案例代码如下：

```html
<!DOCTYPE html>
<html lang="zh-cn">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>仿土豆网显示隐藏遮罩案例</title>
</head>
<style>
    * {
        margin: 0;
        padding: 0;
    }
    .tudou {
        position: relative;
        width: 444px;
        height: 320px;
        background-color: pink;
        margin: 30px auto;
    }
    .tudou img {
        width: 100%;
        height: 100%;
    }
    .mask {
        display: none;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        /* background: rgba(0, 0, 0, 0.4) url("images/03.png") no-repeat center; */
        background: rgba(0, 0, 0, 0.4);
    }
    .tudou:hover .mask {
        display: block;
    }
</style>
<body>
    <div class="tudou">
        <div class="mask"></div>
        <img src="images/02.jfif" alt="">
    </div>
</body>
</html>
```