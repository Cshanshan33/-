# -
前端知识点总结
H5和CSS3

1.H5是html语言的第五代重大修改版本。

2.最新版本的 Safari、Chrome、Firefox 以及 Opera 支持某些 HTML5 特性。Internet Explorer 9 将支持某些 HTML5 特性。

3.改变了用户与文档的交互发方式

4.增加了一些新特性。语义特性，本地存储特性，网页多媒体，三维二维。

5.相对于H4，新增了：代码结构更加清晰，有利于搜索引擎对网页的理解。

HTML5 中的一些有趣的新特性：

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

# HTML 5 Canvas

**canvas 元素用于在网页上绘制图形。**

canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

```
<canvas id="myCanvas" width="200" height="100"></canvas>
```

**HTML5 支持内联 SVG。**

## 什么是SVG？

- SVG 指可伸缩矢量图形 (Scalable Vector Graphics)

- SVG 用于定义用于网络的基于矢量的图形

- SVG 使用 XML 格式定义图形

- SVG 图像在放大或改变尺寸的情况下其图形质量不会有损失

- SVG 是万维网联盟的标准

  ## SVG 的优势

  与其他图像格式相比（比如 JPEG 和 GIF），使用 SVG 的优势在于：

  - SVG 图像可通过文本编辑器来创建和修改
  - SVG 图像可被搜索、索引、脚本化或压缩
  - SVG 是可伸缩的
  - SVG 图像可在任何的分辨率下被高质量地打印
  - SVG 可在图像质量不下降的情况下被放大

**Canvas 和 SVG 都允许您在浏览器中创建图形，但是它们在根本上是不同的。**

## SVG

SVG 是一种使用 XML 描述 2D 图形的语言。

SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。

在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。

## Canvas

Canvas 通过 JavaScript 来绘制 2D 图形。

Canvas 是逐像素进行渲染的。

在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

## Canvas 与 SVG 的比较

下表列出了 canvas 与 SVG 之间的一些不同之处。

### Canvas

- 依赖分辨率
- 不支持事件处理器
- 弱的文本渲染能力
- 能够以 .png 或 .jpg 格式保存结果图像
- 最适合图像密集型的游戏，其中的许多对象会被频繁重绘

### SVG

- 不依赖分辨率
- 支持事件处理器
- 最适合带有大型渲染区域的应用程序（比如谷歌地图）
- 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
- 不适合游戏应用

**HTML5 Geolocation（地理定位）用于定位用户的位置。**



# HTML 5 Web 存储

## 在客户端存储数据

HTML5 提供了两种在客户端存储数据的新方法：

- localStorage - 没有时间限制的数据存储
- sessionStorage - 针对一个 session 的数据存储

之前，这些都是由 cookie 完成的。但是 cookie 不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得 cookie 速度很慢而且效率也不高。

在 HTML5 中，数据不是由每个服务器请求传递的，而是只有在请求时使用数据。它使在不影响网站性能的情况下存储大量数据成为可能。

对于不同的网站，数据存储于不同的区域，并且一个网站只能访问其自身的数据。

HTML5 使用 JavaScript 来存储和访问数据。

## localStorage 方法

localStorage 方法存储的数据没有时间限制。

```
<script type="text/javascript">
localStorage.lastname="Smith";
document.write(localStorage.lastname);
</script>
```

## sessionStorage 方法

sessionStorage 方法针对一个 session 进行数据存储。当用户关闭浏览器窗口后，数据会被删除。

```
<script type="text/javascript">
sessionStorage.lastname="Smith";
document.write(sessionStorage.lastname);
</script>
```

# HTML 5 应用程序缓存

**使用 HTML5，通过创建 cache manifest 文件，可以轻松地创建 web 应用的离线版本。**

应用程序缓存为应用带来三个优势：

- 离线浏览 - 用户可在应用离线时使用它们

- 速度 - 已缓存资源加载得更快

- 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源。

  ```
  <!DOCTYPE HTML>
  <html manifest="demo.appcache">
  ...
  </html>
  ```

每个指定了 manifest 的页面在用户对其访问时都会被缓存。如果未指定 manifest 属性，则页面不会被缓存（除非在 manifest 文件中直接指定了该页面）。

请注意，manifest 文件需要配置*正确的 MIME-type*，即 "text/cache-manifest"。必须在 web 服务器上进行配置。

## 更新缓存

一旦应用被缓存，它就会保持缓存直到发生下列情况：

- 用户清空浏览器缓存

- manifest 文件被修改（参阅下面的提示）

- 由程序来更新应用缓存

  **web worker 是运行在后台的 JavaScript，不会影响页面的性能。**

  ## Web Workers 和 DOM

  由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象：

  - window 对象
  - document 对象
  - parent 对象

## HTML 5 服务器发送事件

**HTML5 服务器发送事件（server-sent event）允许网页获得来自服务器的更新。**

## Server-Sent 事件 - 单向消息传递

Server-Sent 事件指的是网页自动获取来自服务器的更新。

## 接收 Server-Sent 事件通知

EventSource 对象用于接收服务器发送事件通知：



### CSS

line-height 属性设置行间的距离（行高）。

该属性会影响行框的布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。

# CSS 链接

链接的四种状态：

- a:link - 普通的、未被访问的链接
- a:visited - 用户已访问的链接
- a:hover - 鼠标指针位于链接的上方
- a:active - 链接被点击的时刻

```
a:link {color:#FF0000;}		/* 未被访问的链接 */
a:visited {color:#00FF00;}	/* 已被访问的链接 */
a:hover {color:#FF00FF;}	/* 鼠标指针移动到链接上 */
a:active {color:#0000FF;}	/* 正在被点击的链接 */
```

a:hover 必须位于 a:link 和 a:visited 之后，a:action必须位于a：hover只会。

# CSS 表格

```
table, th, td
  {
  border: 1px solid blue;
  }
```

如果需要把表格显示为单线条边框，请使用 border-collapse 属性。

text-align 和 vertical-align 属性设置表格中文本的对齐方式。

如需控制表格中内容与边框的距离，请为 td 和 th 元素设置 padding 属性：

# CSS 内边距

**CSS padding 属性定义元素边框与元素内容之间的空白区域。**

# CSS 边框

**元素的边框 (border) 是围绕元素内容和内边距的一条或多条线。**

**CSS border 属性允许你规定元素边框的样式、宽度和颜色。**

# CSS 外边距

**围绕在元素边框的空白区域是外边距。设置外边距会在元素外创建额外的“空白”。**

**设置外边距的最简单的方法就是使用 margin 属性，这个属性接受任何长度单位、百分数值甚至负值。**

# CSS 外边距合并

**外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。**

**合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。**

# CSS 定位 (Positioning)

CSS 有三种基本的定位机制：普通流、浮动和绝对定位。

## CSS position 属性

position 属性值的含义：

- static

  元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。

- relative

  元素框偏移某个距离。元素仍保持其未定位前的形状，它原本所占的空间仍保留。保存原来的位置。

- absolute

  元素框从文档流完全删除，并相对于其包含块定位。包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。绝对定位使元素的位置与文档流无关，因此不占据空间。

- fixed

  元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。

  # CSS 浮动

  CSS 的 Float（浮动），会使元素向左或向右移动，其周围的元素也会重新排列。

  使用clear可以清除浮动。

  ### CSS选择器优先级和权重

  css选择器优先级顺序是：!important > 行内样式 > ID选择器 > 类选择器 > 元素选择器 > 通配符选择器 > 继承 > 浏览器默认属性。”

- ！important 特殊性最高，详情访问[重要性](https://blog.csdn.net/It_rod/article/details/80466074#t1)

- 对于内联样式，加1000

- 对于选中器中给定的ID属性值，加0100

- 对于选择器中给定的类属性值，属性选择或伪类，加0010

- 对于选择器中给定的元素选择器和伪元素，加0001.

- 结合符和通配符选择器对特殊性没有任何贡献，0000

***\*内联样式 > ID选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 元素选择器 = 关系选择器 = 伪元素选择器 > 通配符选择器\****
