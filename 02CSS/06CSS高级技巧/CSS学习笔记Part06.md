<h1>CSS学习笔记 Part06</h1>

<strong>目录</strong>
<a href="#title01">1. 精灵图</a>
<a href="#title02">2. 字体图标</a>
<a href="#title03">3. CSS三角</a>
<a href="#title04">4. CSS用户界面样式</a>
<a href="#title05">5. vertical-align属性应用</a>
<a href="#title06">6. 溢出的文字省略号显示</a>
<a href="#title07">7. 常见布局技巧</a>

<!-- more -->

<style>
    .red {
        color: red;
    }
</style>

<h2 id="title01">1. 精灵图</h1>

<h3>1.1 为什么需要精灵图</h3>

一个网页往往会应用很多小的背景图像作为修饰，当网页中的图像过多时，服务器就会频繁地接收和发送请求图片，造成服务器请求压力过大，这将大大降低页面的加载速度

因此，<strong class="red">为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度</strong>，出现了<span class="red">CSS精灵技术</span>（CSS Sprites）

<span class="red">核心原理：将网页中的一些小背景图像整合到一张大图中，这样服务器只需要一次请求就可以了</span>

<h3>1.2 精灵图（sprites）的使用</h3>

使用精灵图核心：

1. 精灵技术主要针对背景图片使用，就是把多个小背景图片整合到一张大图片中
2. 这个大图片也成为sprites（精灵图/雪碧图）
3. 移动背景图片位置，此时可以使用<span class="red">background-position</span>
4. 移动的距离就是这个目标图片的x和y坐标。注意网页坐标采取屏幕坐标系
    - 屏幕坐标系：该坐标系是以屏幕的左上角为原点 (0, 0), 水平向右代表 x 方向的正方向， 垂直向下代表 y方向的正方向
5. 因为一般情况下，都是将图片向上或向左移动，所以数值是负值
6. 使用精灵图时需要精确测量每个背景图片的大小和位置

总结：

1. 精灵图主要针对小的背景图片使用
2. 主要借助于背景位置来实现<span class="red">background-position</span>
3. 一般情况下精灵图的background-position的属性值都是负值

<h2 id="title02">2. 字体图标</h1>

<h3>2.1 字体图标的产生</h3>

字体图标的使用场景：主要用于显示网页中通用、常用的一些小图标

精灵图是有诸多优点的，但是缺点明显：
1. 图片文件还是比较大的
2. 图片本身放大缩小会失真
3. 一旦图片制作完毕想要更换非常复杂

此时，有一种技术的出现很好地解决了以上问题，就是<span class="red">字体图标iconfont</span>

<span class="red">字体图标</span>可以为前端工程师提供一种方便高效的图标使用方式，<span class="red">展示的是图标，本质属于字体</span>

字体图标是一些网页常见的小图标，直接网上下载即可。使用步骤如下：
1. 字体图标的下载
2. 字体图标的引入（引入到html页面中）
3. 字体图标的追加

<h3>2.2 字体图标的优点</h3>

- 轻量级：一个字体图标比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求
- 灵活性：本质其实是文字，可以很随意地改变颜色、产生阴影、透明效果、旋转等
- 兼容性：几乎支持所有的浏览器，可放心使用

注意：字体图标不能替代精灵技术，只是对工作中图标部分的提升和优化

总结：
1. 如果遇到一些结构和样式比较简单的小图标，就用字体图标
2. 如果遇到一些结构和样式比较复杂一点的小图片，就用精灵图

<h3>2.3 字体图标的下载</h3>

<strong>推荐下载网站：</strong>

- <strong class="red">icomoon</strong> <a href=http://icomoon.io>http://icomoon.io</a>
- <strong class="red">阿里iconfont字库</strong> <a href=http://www.iconfont.cn>http://www.iconfont.cn/</a>

<h3>2.4 字体图标的引入</h3>

下载完毕之后，注意原先的文件不要删，后面会用

1. 把下载包里面的fonts文件夹放入页面根目录下
2. 在CSS样式中全局声明字体：简单理解就是把这些字体文件通过css引入到我们页面中(见下方代码)
    - 一定要注意字体文件路径的问题
3. html标签内添加小图标

```css
@font-face {
  font-family: 'icomoon';
  src:  url('fonts/icomoon.eot?8ft78i');
  src:  url('fonts/icomoon.eot?8ft78i#iefix') format('embedded-opentype'),
    url('fonts/icomoon.ttf?8ft78i') format('truetype'),
    url('fonts/icomoon.woff?8ft78i') format('woff'),
    url('fonts/icomoon.svg?8ft78i#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
  font-display: block;
}
```
上述字体声明代码在下载的style.css文件中复制获得

<h4>2.4.1 字体文件格式</h4>

不同浏览器所支持的字体格式是不一样的，字体图标之所以兼容，就是因为包含了主流浏览器支持的字体文件

1. TureType(.ttf)格式
2. Web Open Font Format(.woff)格式
3. Embeddeed Open Type(.eot)格式
4. SVG(.svg)格式

<h3>2.5 字体图标的追加</h3>

如果工作中，原来的字体图标不够用了，我们需要添加新的字体图标到原来的字体文件中

把压缩包里面的<span class="red">selection.json</span>重新上传，然后选中自己想要的图标，重新下载压缩包，并替换原来的文件即可

<strong>字体图标加载的原理：</strong>

1. 浏览器发送请求
2. 服务器接收请求，返回请求页面

<h2 id="title03">3. CSS三角</h2>

网页中常见一些三角，使用CSS直接画出来就可以了，不必做成图片或者字体图标

做法如下：
```css
div {
    width: 0;
    height: 0;
    line-height: 0;     /*考虑兼容性*/
    font-size: 0;       /*考虑兼容性*/
    border: 50px solid transparent;
    border-left-color: pink;
}
```

<strong>案例：京东三角</strong>
略

<h2 id="title04">4. CSS用户界面样式</h2>

所谓的<span class="red">界面样式</span>，就是更改一些用户操作样式，以便于提高更好的用户体验。常用类型如下：

- 更改用户的鼠标样式
- 表单轮廓
- 防止表单域拖拽

<h3>4.1 鼠标样式cursor</h3>

语法：
```css
li { cursor: pointer; }
```

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形式

<table>
    <thead>
        <tr>
            <th>属性值</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>default</td>
            <td>小白 默认值</td>
        </tr>
        <tr>
            <td>pointer</td>
            <td>小手</td>
        </tr>
        <tr>
            <td>move</td>
            <td>移动</td>
        </tr>
        <tr>
            <td>text</td>
            <td>文本</td>
        </tr>
        <tr>
            <td>not-allowed</td>
            <td>禁止</td>
        </tr>
    </tbody>
</table>

<h3>4.2 表单轮廓线outline</h3>

语法:
```css
input {
    outline: none;
}
```

<h3>4.3 防止拖拽文本域resize</h3>

实际开发中，文本域右下角是不可以拖拽的

语法：
```css
textarea {
    resize: none;
}
```

<h2 id="title05">5. vertical-align属性应用</h2>

CSS的<span class="red">vertical-align</span>属性使用场景：经常用于设置图片或者表单（行内块元素）和文字垂直对齐

官方解释：用于设置一个元素的<span class="red">垂直对齐方式</span>，但是它只针对于行内元素或者行内块元素有效

语法：
```css
vertical-align: baseline | top | middle | bottom 
```

<table>
    <thead>
        <tr>
            <th>值</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>baseline</td>
            <td>默认。元素放在父元素的基线上</td>
        </tr>
        <tr>
            <td>top</td>
            <td>把元素的顶端与行中最高元素的顶端对齐</td>
        </tr>
        <tr>
            <td>middle</td>
            <td>把此元素放置在父元素的中部</td>
        </tr>
        <tr>
            <td>bottom</td>
            <td>把元素的顶端与行中最低元素的顶端对齐</td>
        </tr>
    </tbody>
</table>

<h3>5.1 图片、表单和文字对齐</h3>

图片、表单都属于行内块元素，默认的vertical-align是基线对齐

此时给图片、表单这些行内块元素的<span class="red">vertical-align属性设置为middle</span>就可以让文字和图片垂直居中对齐了

<h3>5.2 解决图片底部默认空白缝隙问题</h3>

bug：图片底侧会有一个空白缝隙，原因是行内块元素会和文字的基线对齐

解决方法：（两种）
1. 给图片添加<span class="red">vertical-align: middle | top | bottom</span>等（提倡使用）
2. 把图片转换为块级元素<span class="red">display: block;</span>

<h2 id="title06">6. 溢出文字的省略号显示</h2>

<h3>6.1 单行文本溢出显示省略号</h3>

三个必要条件：
1. 先强制一行内显示文本
2. 超出的部分隐藏
3. 文字用省略号替代超出的部分

语法：
```css
/* 1. 先强制一行内显示文本 */
white-space: nowrap; /* 默认值：normal 自动换行 */
/* 2. 超出的部分隐藏 */
overflow: hidden;
/* 3. 文字用省略号替代超出的部分 */
text-overflow: ellipsis;
```