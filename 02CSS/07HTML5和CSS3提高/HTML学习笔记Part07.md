<h1>CSS学习笔记 Part07</h1>

<strong>目录</strong>
<a href="#title01">1. HTML5 的新特性</a>
<a href="#title02">2. CSS3 的新特性</a>

<!-- more -->

<!-- p274--p297 -->

<style>
    .redFont {
        color: red;
    }
    table>thead>tr>th {
        background-color: #4f4f4f;
        color: #fff;
    }
</style>

<h2 id="title01">1. HTML5 的新特性</h2>

<span class="redFont">HTML5</span>的新增特性主要是针对于以前的不足，增加了一些<span class="redFont">新的标签、新的表单、新的表单属性</span>等

这些新特性都有兼容性问题，基本是 IE9+以上版本的浏览器才支持，如果不考虑兼容性问题，可以大量使用这些新特性

声明：新特性增加了很多，但应专注于开发常用的新特性

<h3>1.1 HTML5新增的语义化标签</h3>

以前布局，基本使用 div 制作。div 对于搜索引擎来说，是没有语义的。例如：

```html
<div class="header"></div>
<div class="nav"></div>
<div class="content"></div>
<div class="footer"></div>
```

新增的语义化标签：

- \<header>：头部标签
- \<nav>：导航标签
- \<article>：内容标签
- \<section>：定义文档某个区域
- \<aside>：侧边栏标签
- \<footer>：尾部标签

注意：

- 这种语义化标准主要是针对<span class="redFont">搜索引擎</span>的
- 这些新标签页面中可以使用<span class="redFont">多次</span>
- 在 IE9 中，需要把这些元素转换为<span class="redFont">块级元素</span>
- 移动端更常用这些标签

<h3>1.2 HTML5新增的多媒体标签</h3>

新增的多媒体标签：

1. 音频：\<audio>
2. 视频：\<video>

使用它们可以很方便地在页面中嵌入音频和视频，而不再去使用 flash 和其他浏览器插件

<strong>1. 视频\<video></strong>

当前\<video>元素支持三种视频格式：尽量使用 mp4 格式

 <table>
    <thead>
        <tr>
            <th>浏览器</th>
            <th>MP4</th>
            <th>WebM</th>
            <th>Ogg</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>IE（Internet Explorer）</td>
            <td>Yes</td>
            <td>No</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Chrome</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>Firefox</td>
            <td>Yes<br>从Firefox21版本开始<br>Linux系统从Firefox30开始</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>Safari</td>
            <td>Yes</td>
            <td>No</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Opera</td>
            <td>Yes<br>从Opera25版本开始</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
    </tbody>
</table>

语法：

```html
<video src="文件地址" controls="controls"></video>
```

考虑兼容性可以用以下写法：

```html
<video controls="controls" width="300px">
  <source scr="move.mp4" type="video/mp4" />
  <source scr="move.ogg" type="video/ogg" />
  您的浏览器不支持<video>标签</video>
</video>
```

<strong>1. 视频\<video>——常见属性</strong>

 <table>
    <thead>
        <tr>
            <th>属性</th>
            <th>值</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>autoplay</td>
            <td>autoplay</td>
            <td>视频就绪自动播放（谷歌浏览器需要添加muted来解决自动播放问题）</td>
        </tr>
        <tr>
            <td>contrs</td>
            <td>controls</td>
            <td>向用户显示播放控件</td>
        </tr>
        <tr>
            <td>width</td>
            <td>pixels（像素）</td>
            <td>设置播放器宽度</td>
        </tr>
        <tr>
            <td>height</td>
            <td>pixels（像素）</td>
            <td>设置播放器高度</td>
        </tr>
        <tr>
            <td>loop</td>
            <td>loop</td>
            <td>播放完是否继续播放该视频，循环播放</td>
        </tr>
        <tr>
            <td>preload</td>
            <td>auto（预先加载视频）<br>none（不应加载视频）</td>
            <td>规定是否预加载视频（如果有了autoplay属性，则忽略该属性）</td>
        </tr>
        <tr>
            <td>src</td>
            <td>url</td>
            <td>视频url地址</td>
        </tr>
        <tr>
            <td>poster</td>
            <td>imgurl</td>
            <td>加载等待的画面图片</td>
        </tr>
        <tr>
            <td>muted</td>
            <td>muted</td>
            <td>静音播放</td>
        </tr>
    </tbody>
</table>

<strong>2. 音频\<audio></strong>

 <table>
    <thead>
        <tr>
            <th>浏览器</th>
            <th>MP3</th>
            <th>Wav</th>
            <th>Ogg</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>IE（Internet Explorer）</td>
            <td>Yes</td>
            <td>No</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Chrome</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>Firefox</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>Safari</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Opera</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
    </tbody>
</table>

语法：

```html
<audio src="文件地址" controls="controls"></audio>
```

考虑兼容性可以用以下写法：

```html
<audio controls="controls" width="300px">
  <source scr="happy.mp3" type="audio/mp3" />
  <source scr="happy.ogg" type="audio/ogg" />
  您的浏览器不支持<audio>标签</audio>
</audio>
```

<strong>2. 音频\<audio>——常见属性</strong>

 <table>
    <thead>
        <tr>
            <th>属性</th>
            <th>值</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>autoplay</td>
            <td>autoplay</td>
            <td>如果出现该属性，则音频在就绪后马上播放</td>
        </tr>
        <tr>
            <td>contrs</td>
            <td>controls</td>
            <td>如果出现该属性，则向用户显示播放控件</td>
        </tr>
        <tr>
            <td>loop</td>
            <td>loop</td>
            <td>如果出现该属性，则每当音频结束时重新开始播放</td>
        </tr>
        <tr>
            <td>src</td>
            <td>url</td>
            <td>音频url地址</td>
        </tr>
    </tbody>
</table>

<strong>3. 多媒体标签总结</strong>

- 音频标签和视频标签使用方式基本一致
- 浏览器支持情况不同
- 谷歌浏览器把音频和视频自动播放禁止了
- 可以通过给视频标签添加 muted 属性静音播放视频，音频不可以（可以通过 JavaScript 解决）
- 视频标签是重点，经常设置自动播放，不使用 controls 控件，循环和设置大小属性

<h3>1.3 HTML5新增的input类型</h3>

 <table>
    <thead>
        <tr>
            <th>属性值</th>
            <th>说明</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>type="email"</td>
            <td>限制用户输入必须为Email类型</td>
        </tr>
        <tr>
            <td>type="url"</td>
            <td>限制用户输入必须为Url类型</td>
        </tr>
        <tr>
            <td>type="date"</td>
            <td>限制用户输入必须为日期类型</td>
        </tr>
        <tr>
            <td>type="time"</td>
            <td>限制用户输入必须为时间类型</td>
        </tr>
        <tr>
            <td>type="month"</td>
            <td>限制用户输入必须为月类型</td>
        </tr>
        <tr>
            <td>type="week"</td>
            <td>限制用户输入必须为周类型</td>
        </tr>
        <tr>
            <td>type="number"</td>
            <td>限制用户输入必须为数字类型</td>
        </tr>
        <tr>
            <td>type="tel"</td>
            <td>手机号码</td>
        </tr>
        <tr>
            <td>type="search"</td>
            <td>搜索框</td>
        </tr>
        <tr>
            <td>type="color"</td>
            <td>生成一个颜色选择表单</td>
        </tr>
    </tbody>
</table>

- 重点记住：number、tel、search

<h3>1.4 HTML5新增的表单属性</h3>

 <table>
    <thead>
        <tr>
            <th>属性</th>
            <th>值</th>
            <th>说明</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>required</td>
            <td>required</td>
            <td>表单拥有该属性表示其内容不能为空，必填</td>
        </tr>
        <tr>
            <td><strong>placeholder</strong></td>
            <td>提示文本</td>
            <td>表单的提示信息，存在默认值将不再显示</td>
        </tr>
        <tr>
            <td>autofocus</td>
            <td>autofocus</td>
            <td>自动聚焦属性，页面加载完成自动聚焦到指定表单</td>
        </tr>
        <tr>
            <td>autocomplete</td>
            <td>off/on</td>
            <td>当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出字段中填写的选项<br>默认已经打开，如autocomplete="on"，关闭autocomplete="off"<br>需要放在表单内，同时加上name属性，同时成功提交</td>
        </tr>
        <tr>
            <td><strong>multiple</strong></td>
            <td>multiple</td>
            <td>可以多选文件提交</td>
        </tr>
    </tbody>
</table>
