
# CSS编码规范





[1 代码风格](#1-%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC)

　　[1.1 注释](#11-注释)

　　[1.2 文件](#12-%E6%96%87%E4%BB%B6)

　　[1.3 缩进](#13-%E7%BC%A9%E8%BF%9B)

　　[1.4 空格](#14-%E7%A9%BA%E6%A0%BC)

　　[1.5 选择器](#15-%E9%80%89%E6%8B%A9%E5%99%A8)

　　[1.6 属性](#16-%E5%B1%9E%E6%80%A7)

[2 通用](#2-%E9%80%9A%E7%94%A8)

　　[2.1 属性缩写](#21-%E5%B1%9E%E6%80%A7%E7%BC%A9%E5%86%99)

　　[2.2 属性书写顺序](#22-%E5%B1%9E%E6%80%A7%E4%B9%A6%E5%86%99%E9%A1%BA%E5%BA%8F)

　　[2.3 !important](#23-important)

　　[2.4 z-index](#24-z-index)

[3 值与单位](#3-%E5%80%BC%E4%B8%8E%E5%8D%95%E4%BD%8D)

　　[3.1 文本](#31-%E6%96%87%E6%9C%AC)

　　[3.2 数值](#32-%E6%95%B0%E5%80%BC)

　　[3.3 url()](#33-url)

　　[3.4 长度](#34-%E9%95%BF%E5%BA%A6)

　　[3.5 颜色](#35-%E9%A2%9C%E8%89%B2)

　　[3.6 2D 位置](#36-2d-%E4%BD%8D%E7%BD%AE)

[4 文本编排](#4-%E6%96%87%E6%9C%AC%E7%BC%96%E6%8E%92)

　　[4.1 字体族](#41-%E5%AD%97%E4%BD%93%E6%97%8F)

　　[4.2 字号](#42-%E5%AD%97%E5%8F%B7)

　　[4.3 字体风格](#43-%E5%AD%97%E4%BD%93%E9%A3%8E%E6%A0%BC)

　　[4.4 字重](#44-%E5%AD%97%E9%87%8D)

　　[4.5 行高](#45-%E8%A1%8C%E9%AB%98)

[5 变换与动画](#5-%E5%8F%98%E6%8D%A2%E4%B8%8E%E5%8A%A8%E7%94%BB)

[6 响应式](#6-%E5%93%8D%E5%BA%94%E5%BC%8F)

[7 兼容性](#7-%E5%85%BC%E5%AE%B9%E6%80%A7)

　　[7.1 属性前缀](#71-%E5%B1%9E%E6%80%A7%E5%89%8D%E7%BC%80)

　　[7.2 Hack](#72-hack)




## 1 代码风格

### 1.1 注释

### [强制] 注释统一用`'/* */'`（scss中也不要用`'//'`）

```css
/* Modal header */
.comment {
    line-height: 1.5;
}
```

### 1.2 文件

### [强制] 使用`@charset "utf-8";`声明css文件页面编码为UTF-8；防止css注释出现乱码

#### [建议] `CSS` 文件使用无 `BOM` 的 `UTF-8` 编码。

解释：

UTF-8 编码具有更广泛的适应性。BOM 在使用程序或工具处理文件时可能造成不必要的干扰。

### 1.3 缩进


#### [强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。


示例：

```css
.selector {
    margin: 0;
    padding: 0;
}
```

### 1.4 空格


#### [强制] `选择器` 与 `{` 之间必须包含空格。

示例：

```css
.selector {
}
```

#### [强制] `属性名` 与之后的 `:` 之间不允许包含空格， `:` 与 `属性值` 之间必须包含空格。

示例：

```css
margin: 0;
```

#### [强制] `列表型属性值` 书写在单行时，`,` 后必须跟一个空格。

示例：

```css
font-family: Arial, sans-serif;
```

### 1.5 选择器


#### [强制] `>`、`+`、`~` 选择器的两边各保留一个空格。

示例：

```css
/* good */
main > nav {
    padding: 10px;
}

label + input {
    margin-left: 5px;
}

input:checked ~ button {
    background-color: #69C;
}

/* bad */
main>nav {
    padding: 10px;
}

label+input {
    margin-left: 5px;
}

input:checked~button {
    background-color: #69C;
}
```

#### [强制] 属性选择器中的值必须用双引号包围。

解释：

不允许使用单引号，不允许不使用引号。


示例：

```css
/* good */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female
}

/* bad */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female
}
```

#### [强制] 如无必要，不得为 id、class 选择器添加类型选择器进行限定

解释：

在性能和维护性上，都有一定的影响。


示例：

```css
/* good */
#error,
.danger-message {
    font-color: #c00;
}

/* bad */
dialog#error,
p.danger-message {
    font-color: #c00;
}
```
### [建议] 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确

示例：

```css
/* good */
#username input {}
.comment .avatar {}

/* bad */
.page .header .login #username input {}
.comment div * {}
```
### 1.6 属性


#### [强制] 属性定义必须另起一行。

示例：

```css
/* good */
.selector {
    margin: 0;
    padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```

#### [强制] 属性定义后必须以分号结尾。

示例：

```css
/* good */
.selector {
    margin: 0;
}

/* bad */
.selector {
    margin: 0
}
```






## 2 通用


### 2.1 属性缩写


#### [建议] 在可以使用缩写的情况下，尽量使用属性缩写。

示例：

```css
/* good */
.post {
    font: 12px/1.5 arial, sans-serif;
}

/* bad */
.post {
    font-family: arial, sans-serif;
    font-size: 12px;
    line-height: 1.5;
}
```

#### [建议] 使用 `border` / `margin` / `padding` 等缩写时，应注意隐含值对实际数值的影响，确实需要设置多个方向的值时才使用缩写。

解释：

border / margin / padding 等缩写会同时设置多个属性的值，容易覆盖不需要覆盖的设定。如某些方向需要继承其他声明的值，则应该分开设置。


示例：

```css
/* centering <article class="page"> horizontally and highlight featured ones */
article {
    margin: 5px;
    border: 1px solid #999;
}

/* good */
.page {
    margin-right: auto;
    margin-left: auto;
}

.featured {
    border-color: #69c;
}

/* bad */
.page {
    margin: 5px auto; /* introducing redundancy */
}

.featured {
    border: 1px solid #69c; /* introducing redundancy */
}
```


### 2.2 属性书写顺序


#### [建议] 同一 rule set 下的属性在书写时，应按功能进行分组，并以 **Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果）** 的顺序书写，以提高代码的可读性。

解释：

- Formatting Model 相关属性包括：`position` / `top` / `right` / `bottom` / `left` / `float` / `display` / `overflow` 等
- Box Model 相关属性包括：`border` / `margin` / `padding` / `width` / `height` 等
- Typographic 相关属性包括：`font` / `line-height` / `text-align` / `word-wrap` 等
- Visual 相关属性包括：`background` / `color` / `transition` / `list-style` 等

另外，如果包含 `content` 属性，应放在最前面。


示例：

```css
.sidebar {
    /* formatting model: positioning schemes / offsets / z-indexes / display / ...  */
    position: absolute;
    top: 50px;
    left: 0;
    overflow-x: hidden;

    /* box model: sizes / margins / paddings / borders / ...  */
    width: 200px;
    padding: 5px;
    border: 1px solid #ddd;

    /* typographic: font / aligns / text styles / ... */
    font-size: 14px;
    line-height: 20px;

    /* visual: colors / shadows / gradients / ... */
    background: #f5f5f5;
    color: #333;
    -webkit-transition: color 1s;
       -moz-transition: color 1s;
            transition: color 1s;
}
```

### 2.3 !important


#### [建议] 尽量不使用 `!important` 声明。


#### [建议] 当需要强制指定样式且不允许任何场景覆盖时，通过标签内联和 `!important` 定义样式。

解释：

必须注意的是，仅在设计上 `确实不允许任何其它场景覆盖样式` 时，才使用内联的 `!important` 样式。通常在第三方环境的应用中使用这种方案。下面的 z-index 章节是其中一个特殊场景的典型样例。



### 2.4 z-index



#### [建议] 将 `z-index` 进行分层，对文档流外绝对定位元素的视觉层级关系进行管理。

解释：

同层的多个元素，如多个由用户输入触发的 Dialog，在该层级内使用相同的 `z-index` 或递增 `z-index`。

建议每层包含100个 `z-index` 来容纳足够的元素，如果每层元素较多，可以调整这个数值。


#### [建议] 在可控环境下，期望显示在最上层的元素，`z-index` 指定为 `999999`。

解释：

可控环境分成两种，一种是自身产品线环境；还有一种是可能会被其他产品线引用，但是不会被外部第三方的产品引用。

不建议取值为 `2147483647`。以便于自身产品线被其他产品线引用时，当遇到层级覆盖冲突的情况，留出向上调整的空间。


#### [建议] 在第三方环境下，期望显示在最上层的元素，通过标签内联和 `!important`，将 `z-index` 指定为 `2147483647`。

解释：

第三方环境对于开发者来说完全不可控。在第三方环境下的元素，为了保证元素不被其页面其他样式定义覆盖，需要采用此做法。




## 3 值与单位


### 3.1 文本


#### [强制] 文本内容必须用双引号包围。

解释：

文本类型的内容可能在选择器、属性值等内容中。


示例：

```css
/* good */
html[lang|="zh"] q:before {
    font-family: "Microsoft YaHei", sans-serif;
    content: "“";
}

html[lang|="zh"] q:after {
    font-family: "Microsoft YaHei", sans-serif;
    content: "”";
}

/* bad */
html[lang|=zh] q:before {
    font-family: 'Microsoft YaHei', sans-serif;
    content: '“';
}

html[lang|=zh] q:after {
    font-family: "Microsoft YaHei", sans-serif;
    content: "”";
}
```

### 3.2 数值


#### [强制] 当数值为 0 - 1 之间的小数时，省略整数部分的 `0`。

示例：

```css
/* good */
panel {
    opacity: .8
}

/* bad */
panel {
    opacity: 0.8
}
```

### 3.3 url()


#### [强制] `url()` 函数中的路径不加引号。

示例：

```css
body {
    background: url(bg.png);
}
```


#### [建议] `url()` 函数中的绝对路径可省去协议名。


示例：

```css
body {
    background: url(//baidu.com/img/bg.png) no-repeat 0 0;
}
```


### 3.4 长度


#### [强制] 长度为 `0` 时须省略单位。 (也只有长度单位可省)

示例：

```css
/* good */
body {
    padding: 0 5px;
}

/* bad */
body {
    padding: 0px 5px;
}
```


### 3.5 颜色


#### [强制] RGB颜色值必须使用十六进制记号形式 `#rrggbb`。不允许使用 `rgb()`。 

解释：

带有alpha的颜色信息可以使用 `rgba()`。使用 `rgba()` 时每个逗号后必须保留一个空格。


示例：

```css
/* good */
.success {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
}

/* bad */
.success {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
}
```

#### [强制] 颜色值可以缩写时，必须使用缩写形式。

示例：

```css
/* good */
.success {
    background-color: #aca;
}

/* bad */
.success {
    background-color: #aaccaa;
}
```

#### [强制] 颜色值不允许使用命名色值。

示例：

```css
/* good */
.success {
    color: #90ee90;
}

/* bad */
.success {
    color: lightgreen;
}
```

#### [建议] 颜色值中的英文字符采用小写。如不用小写也需要保证同一项目内保持大小写一致。


示例：

```css
/* good */
.success {
    background-color: #aca;
    color: #90ee90;
}

/* good */
.success {
    background-color: #ACA;
    color: #90EE90;
}

/* bad */
.success {
    background-color: #ACA;
    color: #90ee90;
}
```


### 3.6 2D 位置


#### [强制] 必须同时给出水平和垂直方向的位置。

解释：

2D 位置初始值为 `0% 0%`，但在只有一个方向的值时，另一个方向的值会被解析为 center。为避免理解上的困扰，应同时给出两个方向的值。[background-position属性值的定义](http://www.w3.org/TR/CSS21/colors.html#propdef-background-position)


示例：

```css
/* good */
body {
    background-position: center top; /* 50% 0% */
}

/* bad */
body {
    background-position: top; /* 50% 0% */
}
```





## 4 文本编排


### 4.1 字体族


#### [强制] `font-family` 属性中的字体族名称应使用字体的英文 `Family Name`，其中如有空格，须放置在引号中。

解释：

所谓英文 Family Name，为字体文件的一个元数据，常见名称如下：

字体 | 操作系统 | Family Name
-----|----------|------------
宋体 (中易宋体) | Windows | SimSun
黑体 (中易黑体) | Windows | SimHei
微软雅黑 | Windows | Microsoft YaHei
微软正黑 | Windows | Microsoft JhengHei
华文黑体 | Mac/iOS | STHeiti
冬青黑体 | Mac/iOS | Hiragino Sans GB
文泉驿正黑 | Linux | WenQuanYi Zen Hei
文泉驿微米黑 | Linux | WenQuanYi Micro Hei


示例：

```css
h1 {
    font-family: "Microsoft YaHei";
}
```


#### [强制] `font-family` 按「西文字体在前、中文字体在后」、「效果佳 (质量高/更能满足需求) 的字体在前、效果一般的字体在后」的顺序编写，最后必须指定一个通用字体族( `serif` / `sans-serif` )。

解释：

更详细说明可参考[本文](http://www.zhihu.com/question/19911793/answer/13329819)。

示例：

```css
/* Display according to platform */
.article {
    font-family: Arial, sans-serif;
}

/* Specific for most platforms */
h1 {
    font-family: "Helvetica Neue", Arial, "Hiragino Sans GB", "WenQuanYi Micro Hei", "Microsoft YaHei", sans-serif;
}
```

#### [强制] `font-family` 不区分大小写，但在同一个项目中，同样的 `Family Name` 大小写必须统一。

示例：

```css
/* good */
body {
    font-family: Arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}

/* bad */
body {
    font-family: arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}
```

### 4.2 字号


#### [强制] 需要在 Windows 平台显示的中文内容，其字号应不小于 `12px`。

解释：

由于 Windows 的字体渲染机制，小于 12px 的文字显示效果极差、难以辨认。


### 4.3 字体风格


#### [建议] 需要在 Windows 平台显示的中文内容，不要使用除 `normal` 外的 `font-style`。其他平台也应慎用。

解释：

由于中文字体没有 italic 风格的实现，所有浏览器下都会 fallback 到 obilique 实现 (自动拟合为斜体)，小字号下 (特别是 Windows 下会在小字号下使用点阵字体的情况下) 显示效果差，造成阅读困难。


### 4.4 字重


#### [强制] `font-weight` 属性必须使用数值方式描述。

解释：

CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 400 和 700 两档，分别等价于关键词 normal 和 bold。

浏览器本身使用一系列[启发式规则](http://www.w3.org/TR/CSS21/fonts.html#propdef-font-weight)来进行匹配，在 <700 时一般匹配字体的 Regular 字重，>=700 时匹配 Bold 字重。

但已有浏览器开始支持 =600 时匹配 Semibold 字重 (见[此表](http://justineo.github.io/slideshows/font/#/3/15))，故使用数值描述增加了灵活性，也更简短。

示例：

```css
/* good */
h1 {
    font-weight: 700;
}

/* bad */
h1 {
    font-weight: bold;
}
```

### 4.5 行高


#### [建议] `line-height` 在定义文本段落时，应使用数值。

解释：

将 line-height 设置为数值，浏览器会基于当前元素设置的 font-size 进行再次计算。在不同字号的文本段落组合中，能达到较为舒适的行间间隔效果，避免在每个设置了 font-size 都需要设置 line-height。

当 line-height 用于控制垂直居中时，还是应该设置成与容器高度一致。


示例：

```css
.container {
    line-height: 1.5;
}
```



## 5 变换与动画



#### [强制] 使用 `transition` 时应指定 `transition-property`。

示例：

```css
/* good */
.box {
    transition: color 1s, border-color 1s;
}

/* bad */
.box {
    transition: all 1s;
}
```

#### [建议] 尽可能在浏览器能高效实现的属性上添加过渡和动画。

解释：

见[本文](http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/)，在可能的情况下应选择这样四种变换：

* `transform: translate(npx, npx);`
* `transform: scale(n);`
* `transform: rotate(ndeg);`
* `opacity: 0..1;`

典型的，可以使用 translate 来代替 left 作为动画属性。

示例：

```css
/* good */
.box {
    transition: transform 1s;
}
.box:hover {
    transform: translate(20px); /* move right for 20px */
}

/* bad */
.box {
    left: 0;
    transition: left 1s;
}
.box:hover {
    left: 20px; /* move right for 20px */
}
```




## 6 响应式



#### [强制] `Media Query` 不得单独编排，必须与相关的规则一起定义。

示例：

```css
/* Good */
/* header styles */
@media (...) {
    /* header styles */
}

/* main styles */
@media (...) {
    /* main styles */
}

/* footer styles */
@media (...) {
    /* footer styles */
}


/* Bad */
/* header styles */
/* main styles */
/* footer styles */

@media (...) {
    /* header styles */
    /* main styles */
    /* footer styles */
}
```

#### [强制] `Media Query` 如果有多个逗号分隔的条件时，应将每个条件放在单独一行中。

示例：

```css
@media
(-webkit-min-device-pixel-ratio: 2), /* Webkit-based browsers */
(min--moz-device-pixel-ratio: 2),    /* Older Firefox browsers (prior to Firefox 16) */
(min-resolution: 2dppx),             /* The standard way */
(min-resolution: 192dpi) {           /* dppx fallback */
    /* Retina-specific stuff here */
}
```

#### [建议] 尽可能给出在高分辨率设备 (Retina) 下效果更佳的样式。



## 7 兼容性


### 7.1 属性前缀


#### [强制] 带私有前缀的属性由长到短排列，按冒号位置对齐。

解释：

标准属性放在最后，按冒号对齐方便阅读，也便于在编辑器内进行多行编辑。


示例：

```css
.box {
    -webkit-box-sizing: border-box;
       -moz-box-sizing: border-box;
            box-sizing: border-box;
}
```


### 7.2 Hack


#### [建议] 需要添加 `hack` 时应尽可能考虑是否可以采用其他方式解决。

解释：

如果能通过合理的 HTML 结构或使用其他的 CSS 定义达到理想的样式，则不应该使用 hack 手段解决问题。通常 hack 会导致维护成本的增加。

#### [建议] 尽量使用 `选择器 hack` 处理兼容性，而非 `属性 hack`。

解释：

尽量使用符合 CSS 语法的 selector hack，可以避免一些第三方库无法识别 hack 语法的问题。


示例：

```css
/* IE 7 */
*:first-child + html #header {
    margin-top: 3px;
    padding: 5px;
}

/* IE 6 */
* html #header {
    margin-top: 5px;
    padding: 4px;
}
```


#### [建议] 尽量使用简单的 `属性 hack`。

示例：

```css
.box {
    _display: inline; /* fix double margin */
    float: left;
    margin-left: 20px;
}

.container {
    overflow: hidden;
    *zoom: 1; /* triggering hasLayout */
}
```

#### 1.==[强制]== 属性选择器中的值必须用双引号包围。
 ```
/* good */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female
}

/* bad */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female
}
 ```
#### 2.==[强制]== 如无必要，不得为 id、class 选择器添加类型选择器进行限定
```
/* good */
#error,
.danger-message {
    font-color: #c00;
}

/* bad */
dialog#error==,==
p.danger-message {
    font-color: #c00;
}
```
#### 3.==[强制]== 长度为 0 时须省略单位。 (也只有长度单位可省)
```
/* good */
body {
    padding: 0 5px;
}

/* bad */
body {
    padding: 0px 5px;
}
```
#### 4.==[强制]== RGB颜色值必须使用十六进制记号形式#rrggbb. 如果是带有透明度的再用rgba.  
####        ==[强制]== 颜色值不允许使用命名色值。 
####        ==[强制]== 颜色值中的英文字符采用小写
```
/* good */
.success {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
}
/* bad */
.success {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
}

/* good */
.success {
    background-color: #aca;
}
/* bad */
.success {
    background-color: #aaccaa;
}

/* good */
.success {
    background-color: #aca;
    color: #90ee90;
}
/* bad */
.success {
    background-color: #ACA;
    color: #90ee90;
}
```
#### 5.==[强制]== img标签中必须添加alt属性。
```
<img src="…" alt="logo" >
```

#### 6.==[强制]== 选择器的嵌套层级应不大于 3级
```
位置靠后的限定条件应尽可能精确(Chrome是用递归从最后一个选择器一直匹配到第一个，选择器越多，匹配的时间就越长)
/* good */
#username input {}
.comment .avatar {}

/* bad */
.page .header .login #username input {}
.comment div * {}

/*bad sass less*/
.listings-list{
    ul{
        li{
            .bed-bath{
                p{
                     color: #505050;
                }
            }
        }
    }
}
```

#### ==(1)== td要在tr里面，==(2)== li要在ul/ol里面， ==(3)== ul/ol的直接子元素只能是li
```
/*bad*/
<div>
    <li></li>
    <li></li>
</div>
<table>
    <td></td>
    <td></td>
</table>
<ol>
    <span>123</span>
    <li>a</li>
    <li>b</li>
</ol>

```

#### 7.[建议]  减少覆盖  (2种适用情况)
```
（1）为了让每个house顶部有20px的间距，但是第一个house不要有间距
/*bad*/
.house{   margin-top: 20px; }
.house:first-child{  margin-top: 0; }
/*good*/
.house + .house{    margin-top: 20px; }

（2）	
/*bad*/
.request-demo input{    border: 1px solid #282828;}
.request-demo input[type=submit]{    border: none;}

/*good*/
.request-demo input:not([type=sbumit]){    border: 1px solid #282828; }
```

#### 8.[建议]  img空src的问题处理。
```
1.<img src="about:blank" alt="desc">

2.<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7">
```
#### 9.[建议] html要保持简洁，不要套太多层

#### 10.[建议] 特殊符号使用html实体
```
符号 实体编码
©   &copy;
¥   &yen;
®   &reg;
>   &gt;
<   &lt;
&   &amp;
```

#### 11.[建议] 在可以使用缩写的情况下，尽量使用属性缩写。
```
/* good */
.post {
    font: 12px/1.5 arial, sans-serif;
    padding:20px;
}

/* bad */
.post {
    font-family: arial, sans-serif;
    font-size: 12px;
    line-height: 1.5;
    padding-top:20px;
    padding-bottom:20px;
    padding-left:20px;
    padding-right:20px;   
}
```
#### 12.[建议] 当数值为 0 - 1 之间的小数时，省略整数部分的 0
```
/* good */
panel {
    opacity: .8
}

/* bad */
panel {
    opacity: 0.8
}
```
#### 13.[建议]  url()函数中的路径加引号。
```
body {
    background: url("bg.png");
}
```
#### 14.[建议]单标签不要写闭合标签（常见的单标签有img、link、input、hr、br）
```
/*good*/
<img src="test.jpg">
<br>
<input type="email" value="">

/*bad*/
<img src="test.jpg" />
<br />
<input type="email" value="" />
```

#### 15.[建议] 推荐的CSS书写顺序  ( [建议] html使用双引号，css使用单引号。  )
```
　　(1)布局方式、位置(position, top, right, z-index, display, float等)

　　(2)盒模型(width, height, padding, margin,border ,overflow )

　　(3)文本排版(font, line-height, letter-spacing,  text-align等)

　　(4)视觉外观(background, color,list-style等)

　　(5)其他(animation, transition等)
```

#### 16.[建议] html,css 较大独立模块之间注释格式统一使用     多写注释
```
<!-- XXX模块  start-->
  …
<!--  XXX模块 end -->
```

#### 17.[建议]能使用background-color,就尽量不要使用background
```
/* good */
.success {
    background-color: #aca;
}

/* bad */
.success {
    background: #ACA;
}
```
#### 18.[建议]项目命名 ( 全部采用小写方式， 以下划线分隔。)
```
/* good */
my_project_name
    
/* bad */
my-project-name
```
#### 19.[建议]文件保存路径
```
    style
    images  图片文件夹
    js  js文件夹
    css  css文件夹
    base.css
    img  背景图片文件夹
```
#### 20.[建议] 对于网页中非常重要的链接采用TITLE说明，有助于帮助搜索引擎找到网页的重点URL。
```
<a href="网址" title="链接说明">网页信息</a>。
 
```
#### 21.[建议]布局时候应该从里而外


#### 22.[建议]使用适合的标签(标签使用上不要太单调)
```
（1）如果内容是表格就使用table，table有自适应的优点；如果是一个列表就使用ol/ul标签，扩展性比较好

（2）如果是输入框就使用input，而不是写一个p标签，然后设置contenteditable=true，因为这个在IOS Safari上光标定位容易出现问题。如果需要做特殊效果除外

（3）如果是粗体就使用b/strong，而不是自己设置font-weight

（4）如果是表单就使用form标签，注意form里面不能套form

（5）如果是跳链就使用a标签，而不是自己写onclick跳转。a标签里面不能套a标签

（6）使用html5语义化标签，如导航使用nav，侧边栏使用aside，顶部和尾部使用header/footer，页面比较独立的部分可以使用article，如用户的评论。

（7）如果是按钮就应该写一个button或者<input type=”button”>，而不是写一个a标签设置样式，因为使用button可以设置disabled，然后使用CSS的:disabled，还有:active等伪类使用，例如在:active的时候设置按钮被按下去的感觉

（8）如果是标题就应该使用标题标签h1/h2/h3，而不是自己写一个<p class=”title”></p>，相反如果内容不是标题就不要使用标题标签了

（9）在手机上使用select标签，会有原生的下拉控件，手机上原生select的下拉效果体验往往比较好，不管是IOS还是android，而使用<input type=”tel”>在手机上会弹一个电话号码的键盘，<input type=”number”> <input type=”email”>都会弹相应的键盘

（10）如果是分隔线就使用hr标签，而不是自己写一个border-bottom的样式，使用hr容易进行检查

（11）如果是换行文本就应该使用p标签，而不是写br，因为p标签可以用margin设置行间距，但是如果是长文本的话使用div，因为p标签里面不能有p标签，特别是当数据是后端给的，可能会带有p标签，所以这时容器不能使用p标签。
```
#### 23.[建议] 不要设置太大的z-index

#### 24.[建议]  自定义属性要以data-开头

#### 25.[建议]  适当使用:before/:after
```
画页面的一些视觉上的辅助性元素，如三角形、短的分隔线、短竖线等，可以减少页面上没有用的标签
```

#### 26. 文字超出显示特定行（兼容IE9以上）
```
.font_hide {
    display: inline-block;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}

.font_hide2 {
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
}

.font_hide3 {
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
}
```
#### //怪异盒模型（IE9以上兼容）
```
.bbox {
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -o-box-sizing: border-box;
    -ms-box-sizing: border-box;
    -moz-box-sizing: border-box
}
```
#### //弹性盒模型布局（pc端不建议使用,移动端最好都能用flex布局）
```
.flex {
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
}
```


#### meta标签的总结
```
<!-- 字体编码 -->
<meta charset="utf-8" />

<!-- 关键字 -->
<meta name="keywords" content="" />

<!-- 说明 -->
<meta name="description" content="" />

<!-- 作者 -->
<meta name="author" content="" />

<!-- 设置文档宽度、是否缩放 -->
<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no" />

<!-- 优先使用IE最新版本或chrome -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />

<!-- 360读取到这个标签立即钱换到极速模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="renderer" content="webkit"> 

<!-- 避免IE使用兼容模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">

<!-- 禁止百度转码 -->
<meta http-equiv="Cache-Control" content="no-siteapp" />

<!-- UC强制竖屏 -->
<meta name="screen-orientation" content="portrait" />

<!-- UC强制全屏 -->
<meta name="full-scerrn" content="yes" />

<!-- UC应用模式 -->
<meta name="browsermode" content="application">

<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait" />

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="ture" />

<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app" />

<!-- window phone 点亮无高光 -->
<meta name="msapplication-tap-highlight" content="no" />

<!-- 安卓设备不自动识别邮件地址 -->
<meta name="format-detection" name="email=no" />

<!-- 设置网页的定时跳转 -->
<meta http-equiv='refresh' content='跳转时间；url=链接地址'>   

<!-- iOS设备 -->
<!-- 添加到主屏幕的标题 -->
<meta name="apple-mobile-web-app-title" content="标题" />

<!-- 是否启用webApp全屏 -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- 设置状态栏的背景颜色，启用webapp模式时生效 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent/black/default" />

<!-- 半透明/黑色/默认白色 -->
<!-- 禁止数字识别为电话号码 -->
<meta name="format-detection" content="telephone=no;email=no" />

<!-- 
iOS图标
iPhone/iTouch默认是57*57
iPad，72*72，可以没有，但推荐有
Retina iPhone/Retina iTouch，114*114,可以没有，但推荐有
Retina iPad,144*144,可以没有，但推荐有
iPhone 6 plus是180*180，iPhone 6 是120*120
-->
<link rel="apple--touch-icon-precomposed" sizes="width*height" href="xxx.png" />

<!-- 
iOS启动画面 
iPad启动是不包含状态栏的 
标准分辨率：1、竖屏(768*1004)；2、横屏(1024*748)
Retina:1、竖屏(1536*2008)；2、横屏(2048*1496)
iPhone/iTouch启动是包含状态栏的
标准分辨率(320*480)、Retina(640*960)、iPhone 5/iTouch 5(640*1136) 
-->
<link rel="apple-touch-startup-image" sizes="width*height" href="xxx.png" />

<!-- iPhone 6对应的图片大小是750×1294，iPhone 6 Plus 对应的是1242×2148 -->
<link rel="apple-touch-startup-image" href="xxx.png" media="(device-width:375px)">
<link rel="apple-touch-startup-image" href="xxx.png" media="(device-width:414px)">

<!-- 智能添加广告条 -->
<meta name="apple-itunes-app"content="app-id=myappstoreID,affiliate-data=myaffiliatedata,app-argument=myurl" />
```


#### PC端重置CSS
```
html,body,h1,h2,h3,h4,h5,h6,hr,p,iframe,dl,dt,dd,ul,ol,li,pre,form,button,input,textarea,th,td{margin:0;padding:0;}

body,th,td,button,input,select,textarea{font:14px/1.6  "Microsoft YaHei",Arial,Tahoma, Helvetica,sans-serif; -webkit-font-smoothing:antialiased;-moz-font-smoothing:antialiased;resize: none;}

html,body{*position:static;height:100%;width:100%; }

html{font-family: sans-serif;-webkit-text-size-adjust:100%;-ms-text-size-adjust:100%;}

ul,ol,li,dl{list-style-type:none;}

label{cursor:pointer;}

fieldset,img {  border:0;}

button,h1,h2,h3,h4,h5,h6,input,select,textarea{font-size:100%;}

a{text-decoration:none;cursor:pointer;}
a:hover,a:active,a:focus{text-decoration:none;outline:none;}

img{border:0;vertical-align:middle;}

i{ display: inline-block; font-style: normal; } 

.fl{ float: left;}

.fr{ float: right;}

.clear{zoom:1;}

.clear:after{content:'';display:block;clear:both;}

i,s,b,em{ font-weight:normal;font-style:normal; }
   
textarea.resize{resize:both !important;}

input { border-radius: 0;}

input,button,textarea,select,optgroup,option{font-family:inherit;font-size:inherit;font-style:inherit;font-weight:inherit;}

input,button{overflow: visible;vertical-align:middle;outline:none;}

button,input[type="button"], input[type="submit"] {line-height:normal !important;cursor:pointer;}

textarea,
input[type="button"],
input[type="submit"],
input[type="reset"],
input[type="text"]{-webkit-appearance: none;}

button::-moz-focus-inner,
input::-moz-focus-inner,
input[type="file"] > input[type="button"]::-moz-focus-inner { border: 0; padding: 0;}

input[type=tel],
input[type=text] {-webkit-tap-highlight-color: rgba(0,0,0,0);}

input[type=button],
input[type=reset],
input[type=submit] {-webkit-appearance: none; border-radius: 0;}

/* 去掉number输入框右边点击上下的小三角 */
input::-webkit-inner-spin-button{ -webkit-appearance: none; } 
input::-webkit-outer-spin-button{ -webkit-appearance: none; }

/*placeholder 文字颜色设置*/
input::-moz-placeholder,
input::-ms-input-placeholder,
input::-webkit-input-placeholder,
textarea::-moz-placeholder,
textarea::-ms-input-placeholder,
textarea::-webkit-input-placeholder { color: #999; }

/* Chrome浏览器会在输入控制聚集的时候添加一个蓝色的outline*/
input:focus, textarea:focus, select:focus{ outline: none; }

/* 去掉select的默认样式 */ 
select{ -webkit-appearance: none; }
 
/* 如果有输入内容IE会给输入框右边加一个大大的X */ 
input::-ms-clear{ display: none; width: 0; height: 0; } 
```


