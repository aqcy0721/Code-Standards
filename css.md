
# CSS编码规范



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

#### 7.==[强制]== html,css 较大独立模块之间注释格式统一使用     多写注释
```
<!-- XXX模块  start-->
  …
<!--  XXX模块 end -->
```

#### 8.[强制]文件保存路径
```
    style
    images  图片文件夹
    js  js文件夹
    css  css文件夹
    base.css
    img  背景图片文件夹
```



#### 9.==(1)== td要在tr里面，==(2)== li要在ul/ol里面， ==(3)== ul/ol的直接子元素只能是li
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

#### 10.[建议]  减少覆盖  (2种适用情况)
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

#### 11.[建议]  img空src的问题处理。
```
1.<img src="about:blank" alt="desc">

2.<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7">
```
#### 12.[建议] html要保持简洁，不要套太多层

#### 13.[建议] 特殊符号使用html实体
```
符号 实体编码
©   &copy;
¥   &yen;
®   &reg;
>   &gt;
<   &lt;
&   &amp;
```

#### 14.[建议] 在可以使用缩写的情况下，尽量使用属性缩写。
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
#### 15.[建议] 当数值为 0 - 1 之间的小数时，省略整数部分的 0
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
#### 16.[建议]  url()函数中的路径加引号。
```
body {
    background: url("bg.png");
}
```
#### 17.[建议]单标签不要写闭合标签（常见的单标签有img、link、input、hr、br）
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

#### 18.[建议] 推荐的CSS书写顺序  ( [建议] html使用双引号，css使用单引号。  )
```
　　(1)布局方式、位置(position, top, right, z-index, display, float等)

　　(2)盒模型(width, height, padding, margin,border ,overflow )

　　(3)文本排版(font, line-height, letter-spacing,  text-align等)

　　(4)视觉外观(background, color,list-style等)

　　(5)其他(animation, transition等)
```


#### 19.[建议]能使用background-color,就尽量不要使用background
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
#### 20.[建议]项目命名 ( 全部采用小写方式， 以下划线分隔。)
```
/* good */
my_project_name
    
/* bad */
my-project-name
```

#### 21.[建议] 对于网页中非常重要的链接采用TITLE说明，有助于帮助搜索引擎找到网页的重点URL。
```
<a href="网址" title="链接说明">网页信息</a>。
 
```
#### 22.[建议]布局时候应该从里而外


#### 23.[建议]使用适合的标签(标签使用上不要太单调)
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
#### 24.[建议] 不要设置太大的z-index

#### 25.[建议]  自定义属性要以data-开头

#### 26.[建议]  适当使用:before/:after
```
画页面的一些视觉上的辅助性元素，如三角形、短的分隔线、短竖线等，可以减少页面上没有用的标签
```

#### 27. 文字超出显示特定行（兼容IE9以上）
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


