# 							CSS

 
 

 \###简介

 
 

 层叠 cascading 样式 style 表 sheets 

 
 

 用于调整HTML元素的样式, 通常存储在.css文件中.

 
 

 优点: 让网页内容 与 网页的样式 完全分离, 提高了代码的复用性 和 维护性 以及 可扩展性.

 
 

 \###样式

 
 

 样式表中 包含一个个的样式.

 每一个样式, 就是样式表中的一个键值对.

 格式:

 键与值之间通过冒号连接.

 多个键值对之间通过分号分割.

 
 

 常见的样式:

 \1. 字体大小: font-size:长度+单位;

 \2. 文本颜色: color:颜色值;

 \3. 文字位置: text-align:left/center/right;

 \4. 元素宽度: width:长度+单位;

 \5. 元素高度: height:长度+单位;

 \6. 背景颜色: background-color:颜色值;

 \7. 背景图片: background-image:url("图片地址");

 
 

 
 

 \###CSS的三种使用方式 *****

 
 

 \1. 内联样式表

 定义在 每一个元素的style属性中.

 案例: <div style="color:red;font-size:50px;">床前明月光, 地上鞋两双.</div>

 \2. 内部样式表

 定义在网页的style标签中, style标签通常编写在head标签中.

 案例:

 <style>

 div{

 text-align: center;

 }

 \#div1{

 font-size:12px;

 }

 .c1{

 background-color: #000;

 color:#fff;

 }

 </style>

 \3. 外部样式表 ( 推荐 )

 定义在独立的css文件中, 在html的head里通过link标签 引入css文件.

 css文件:

 @charset "UTF-8";

 \#div1{

 color:#999;

 }

 link标签:

 <link rel="stylesheet" type="text/css" href="css/demo1.css">

 \###CSS选择器 

 
 

 作用: 用于将样式给定到选择的一个或一组元素 !

 
 

 \####基本选择器 *****

 
 

 \#####元素名称选择器

 
 

 作用: 通过元素的名称, 选择一组元素, 将样式给定.

 
 

 格式:

 元素名称{

 样式列表;

 }

 
 

 \#####id选择器

 作用: 通过元素的id, 选择一个元素, 将样式给定.

 
 

 格式:

 \#id值{

 样式列表;

 }

 
 

 注意: HTML规则是松散的, 所以id值可以重复.

 
 

 \#####类选择器

 
 

 作用: 通过元素的class属性值, 来选择一组元素, 将样式给定.

 
 

 格式:

 .class值{

 样式列表;

 }

 
 

 注意: 每一个元素都可以设置class属性值, 值的作用是将元素分类!

 每一个元素都可以设置多个class值, 编写格式: class="值1 值2 值3... 值n"

 
 

 \###CSS样式的三大特性 *****

 
 

 \- 继承性

 部分父元素的样式, 会被子元素继承 !

 \- 层叠性

 对于同一个元素, 通过多种方式添加的样式, 不冲突的部分 可以叠加. 冲突的部分参考优先级特性.

 \- 优先级

 样式定义来源优先级:

 \1. 内联样式 , 优先级最高.

 \2. 相同选择器的情况下 , 定义距离body较近的内部样式表 或 外部样式表.

 \3. 浏览器默认样式.

 \4. 继承得到的样式.

 
 

 
 

 选择器优先级:

 在内部样式表和外部样式表中 , 不同选择器的优先级不同:

 \1. id选择器   100

 \2. 类选择器   10

 \3. 元素名称选择器 1

 
 

 绝对优先样式:

 在样式值的后面, 加入绝对优先关键字: !important;

 
 

 
 

 \###伪类选择器

 
 

 \####鼠标悬停选择器 *

 
 

 作用: 当鼠标悬停在元素上方时 , 样式生效! 鼠标离开元素后 , 样式还原!

 
 

 格式:

 选择器:hover{

 样式列表;

 }

 
 

 \####获取焦点 选择器

 
 

 作用: 当输入组件正在被用户操作时, 样式生效. 失去焦点后 ,样式还原.

 
 

 格式:

 选择器:focus{

 样式列表;

 }

 
 

 
 

 \###组合选择器 熟悉

 
 

 优先级权重 计算方式为: 组合中所有选择器 权重的和.

 
 

 \####选择器组

 
 

 通过多个选择器, 组合起来锁定一个或多个元素. (当多个选择器都满足时, 样式生效.)

 
 

 格式:

 元素名称选择器选择器1选择器2...选择器n{

 样式列表;

 }

 
 

 
 

 \####选择器列表

 
 

 将一组样式, 给定到多个选择器的结果上. (当任意一个选择器满足, 样式就生效)

 
 

 格式:

 选择器1,选择器2,...选择器n{

 样式列表;

 }

 
 

 \###派生选择器 * 

 
 

 \####子选择器

 格式:

 选择器1>选择器2{

 
 

 }

 
 

 作用:

 从选择器1选的元素中 , 寻找满足选择器2的子元素.

 
 

 例如:

 选择器id为div1的元素的 id为heihei的子元素

 \#div1>#heihei{

 
 

 }

 
 

 \####后代选择器

 
 

 格式:

 选择器1 选择器2{

 
 

 }

 
 

 作用:

 从选择器1选的元素中 , 寻找满足选择器2的后代元素.

 
 

 例如:

 选择器id为div1的元素的 id为heihei的后代元素

 \#div1 #heihei{

 
 

 }

 
 

 \###常用样式

 
 

 \####背景样式

 
 

 \- 背景颜色 *

 background-color:颜色值;

 \- 背景图片 *

 background-image:url("图片地址1"),url("图片地址2")...;

 多个图片堆叠显示 , 堆叠的顺序是: URL定义的越靠前, 显示时越靠上.

 
 

 \- 背景图片的控制 - 平铺   (了解)

 background-repeat:

 \- repeat ; 默认值平铺

 \- repeat-x ; 仅横向值平铺

 \- repeat-y ; 仅纵向平铺

 \- no-repeat ; 不平铺

 
 

 \- 背景图片的控制 - 缩放   (了解)

 background-size:宽度% 高度%;

 
 

 \- 背景图片的控制 - 滑动   (了解)

 background-attachment:

 \- scroll : 滑动, 默认效果.

 \- fixed : 固定

 
 

 -	背景图片的控制 - 定位 掌握  

 常用于CSS精灵图片

 格式:

 
 

 background-position:x偏移值 y偏移值;

 
 

 \--------------------------------------------------------

 **第三章** **CSS 02**  

 
 

 2019/10/22 8:57:44  

 
 

 \----

 
 

 \## 常用样式

 
 

 \### 文字样式

 
 

 \- 字体大小

 font-size:长度+单位;

 \- 文字颜色

 color:颜色值;

 \- 内容横向位置

 text-align:left/center/right;

 \- 内容纵向位置:

 vertical-align:

 \- top  : 顶部对齐

 \- middle : 中间对齐

 \- bottom : 底部对齐

 \- text-top: 文字顶部对齐.

 \- text-bottom: 文字底部对齐

 
 

 \- 文本样式 (斜体)

 font-style:oblique;

 \- 文字加粗

 font-weight:bold;

 \- 文字修饰

 text-decoration:

 \- underline : 下划线

 \- overline : 上划线

 \- line-through: 删除线

 \- none  去除修饰线

 \- 文本行高(设置一行文本的高度)

 line-height:长度+单位;

 注意: 文本行高等于元素高度时, 一行文字相当于垂直居中

 \- 字体设置:

 font-family:字体名称;

 
 

 \- CSS3版本 安装临时字体 (只在当前页面生效)

 步骤:

 \1. 安装字体

 @font-face{

 font-family:自定义字体名称;

 src:url("字体地址");

 }

 \2. 使用安装的字体

 选择器{

 font-family:字体名称;

 }

 
 

 \- 文字阴影

 text-shadow:x偏移 y偏移 [阴影模糊距离] 阴影颜色;

 
 

 \### 边框 *

 
 

 边框不占用元素的宽高. 

 
 

 格式1:

 一次指定四个方向的边框 (宽度+样式+颜色)

 border:宽度 样式 颜色值;

 
 

 格式2:

 单独指定某一个方向边框的宽度 / 样式 / 颜色.

 左: border-left:宽度 样式 颜色值;

 上: border-top:宽度 样式 颜色值;

 右: border-right:宽度 样式 颜色值;

 下: border-bottom:宽度 样式 颜色值;

 
 

 
 

 边框样式:

 \- 实线 : solid

 \- 虚线 : dashed

 \- 点  : dotted

 
 

 \### 边框圆角  

 
 

 格式1.

 一次指定四个角的圆角宽度值.

 border-radius:长度+单位;

 
 

 格式2.

 单独指定每个角的圆角宽度值.

 上左: border-top-left-radius:长度+单位;

 上右: border-top-right-radius:长度+单位;

 下左: border-bottom-left-radius:长度+单位;

 下右: border-bottom-right-radius:长度+单位;

 
 

 边框宽度值 支持百分比, 表示占用元素宽和高的百分比

 
 

 \### 边框阴影

 ? 格式:

 ? box-shadow:x偏移 y偏移 [阴影模糊大小] 阴影大小 阴影颜色;

 
 

 \###处理溢出边框的内容

 
 

 格式:

 overflow:

 \- visible : 默认值 , 溢出显示.

 \- hidden : 溢出隐藏  *

 \- scroll : 添加滚动条

 \- auto : 当溢出时, 自动添加滚动条

 
 

 \### 表格的边框双线问题

 
 

 设置给 table 如下的样式:

 border-collapse:collapse;

 
 

 \### CSS盒模型 ( 框模型 ) ***

 
 

 指的是元素在网页中 占用空间大小 的计算模型.

 
 

 占用的宽度的空间:

 元素自身宽度+左右边框宽度+左右内边距+左右外边距.

 
 

 占用的高度的空间:

 元素自身高度+上下边框宽度+上下内边距+上下外边距.

 
 

 \### 内边距 padding ***

 
 

 指的是元素的内容 距离 自身边框的距离.

 
 

 格式1.

 一次指定四个方向的内边距

 padding:长度+单位;

 
 

 格式2.

 通过一个样式, 分别指定上下 和 左右的内边距.

 padding: 上下内边距 左右内边距;

 
 

 格式3.

 通过一个样式, 分别指定 上,右,下,左的内边距

 padding:上 右 下 左;

 
 

 格式4.

 单独指定每一个方向的内边距

 左: padding-left:长度+单位;

 右: padding-right:长度+单位;

 上: padding-top:长度+单位;

 下: padding-bottom:长度+单位;

 
 

 \### 外边距 margin ***

 
 

 指的是元素的边框 距离 其他元素 盒模型的距离. 值可以是负数.

 
 

 格式1.

 一次指定四个方向的外边距

 margin:长度+单位;

 
 

 格式2.

 通过一个样式, 分别指定上下 和 左右的外边距.

 margin: 上下外边距 左右外边距;

 
 

 格式3.

 通过一个样式, 分别指定 上,右,下,左的外边距

 margin:上 右 下 左;

 
 

 格式4.

 单独指定每一个方向的外边距

 左: margin-left:长度+单位;

 右: margin-right:长度+单位;

 上: margin-top:长度+单位;

 下: margin-bottom:长度+单位;

 
 

 \### 外边距的特殊使用方式: 了解

 
 

 \1. 可以通过指定左右外边距的值 为 auto , 来实现自动居中.

 \2. 两个块元素之间, 上下外边距不会累加. 值较大者生效.

 \3. 外边距可以设置负数

 
 

 \### 鼠标形状 * 

 
 

 cursor :

 \- default : 默认鼠标形状, 跟随场景自动变化.

 \- pointer : 手指形状 , 常用于提示用户 元素可点击.

 \- text : 焦点形状(工字形)

 \- wait : 等待

 \- help : 帮助

 \- progress: 进行中

 
 

 \### 列表样式 * 

 
 

 取消列表前置的数字 或 小圆点.

 
 

 list-style-type:none;

 
 

 \### 透明度 *

 
 

 opacity:0-1的浮点数字.

 当值为1时, 表示不透明.

 当值为0时, 表示完全透明.

 当值为0.5时 , 半透明.

 
 

 \## ### 定位 ****

 
 

 用于控制元素在网页中显示的位置 

 
 

 \#### 默认定位 ( 静态定位 ) *****

 
 

 默认定位情况下, 元素分为三类:

 \1. 块元素: 独占一行, 可以设置宽度和高度. 例如: div , p ,ul ,ol ,li 等等

 \2. 行内元素: 与其它元素共享一行, 从左至右排列. 一行排满时自动换行. 宽度和高度无法设置, 由内容撑开. 例如: span,b,i等等

 \3. 行内块元素: 与其它元素共享一行, 从左至右排列, 一行排满时自动换行, 可以设置宽度和高度, 例如: img, button ,input等等

 
 

 在默认定位情况下, 通过display样式, 调整元素的显示分类:

 display:

 \- block   : 块元素

 \- inline   : 行内元素

 \- inline-block : 行内块元素

 \- none   : 不显示.

 
 

 \#### 浮动定位 掌握

 
 

 格式:

 float:left/right;

 
 

 浮动已经脱离了原有的默认定位方式. 

 浮动极易引起周围元素的 显示错乱.

 
 

 清除浮动带来的影响:

 控制元素的某个方向不允许出现浮动:

 clear:left/right/both;

 
 

 \#### 相对定位

 
 

 作用: 元素相对于自身当前位置, 进行x和y轴的移动.

 
 

 格式:

 position:relative;

 
 

 特点:

 元素偏移后, 依然占用原有的网页空间, 偏移后的元素 采用覆盖方式显示.

 
 

 \#### 绝对定位

 
 

 作用: 根据body的边框, 来确定自身的位置;

 如果元素存在一个 设置了相对/绝对/固定定位的 祖先元素 . 就变成了根据这个祖先元素的边框来确定自身的位置;

 
 

 格式:

 position:absolute;

 
 

 特点:

 元素不再占用任何的网页空间 ,采用覆盖显示.

 \#### 固定定位

 
 

 作用: 根据浏览器的边框, 来固定自身的位置. 不会因为内容的滑动而滑动

 
 

 格式:

 position:fixed;

 
 

 特点:

 不占用网页空间 ,采用覆盖显示

 
 

 \#### 相对定位 / 绝对定位 / 固定定位 确定自身位置的方式:

 
 

 这三种定位, 都是通过如下四种样式来完成位置确定的:

 
 

 \1. left:长度+单位;

 \2. top:长度+单位;

 \3. right:长度+单位;

 \4. bottom:长度+单位;

 
 

 在相对定位中:

 表示元素相对与当前自身位置 , 进行指定方向的偏移.

 例如: 想让元素 向右移动10个像素:

 left:10px 或 right:-10px

 例如: 想让元素 向上移动10个像素

 bottom:10px 或 top:-10px;

 
 

 在绝对定位中:

 默认情况下是: 距离body四个边框的距离

 存在相对/绝对/固定定位祖先元素时: 距离此祖先元素四个边框的距离.

 
 

 设置bottom:0px时, 不是距离body底边0px , 而是浏览器窗口;

 
 

 在固定定位中:

 距离浏览器某个方向边界的 距离;

 
 

 \------------------------------------------------

 
 

 **第四章**  **CSS 03**  

 
 

 2019/10/23 08:39:18  

 
 

 \-----

 
 

 \###CSS常用样式

 
 

 \####定位时的堆叠顺序 熟悉

 
 

 默认情况下, 元素编写越靠后, 显示时越靠前.

 
 

 设置堆叠优先级:

 z-index:数字值;

 
 

 作用:

 默认值为0 , 值越大, 越靠前. 负数表示显示在内容的后面.

 
 

 \####过渡 * 

 
 

 在元素的样式变更时 , 增加过渡时长, 让样式的更改更圆润.

 
 

 格式1:

 transition:样式名 时长s;

 格式2:

 transition:all 时长s;

 
 

 案例:

 
 

 .login_w{

 position: relative;

 left:200px;

 top:100px;

 width:300px;

 height:300px;

 background-color: #fff;

 }

 .qrcode{

 width:300px;

 position: absolute;

 left:75px;

 top:0px;

 transition:all 1s;

 }

 .hide{

 opacity: 0;

 transition:all 1s;

 }

 .hide:hover{

 opacity: 1;

 }

 .qrcode:hover{

 left:0px;

 }

 </style>

 </head>

 <body>

 <div class="login_w">

 <div class="qrcode">

 <img src="images/qrcode.png"><img class="hide" src="images/phone.png">

 </div>

 </div>

 </body>

 
 

 
 

 \###转换 熟悉

 
 

 \####2D转换

 
 

 transform:

 	-	位置移动	:	translate(x,y);  

 x和y 表示横向和纵向的移动坐标.

 \- 旋转     : rotate(数字deg);

 数字值表示旋转的度数.

 \- 缩放   : scale(x,y);

 x和y 表示缩小和放大的倍数.

 \- 翻转  : skew(xdeg,ydeg);

 x和y 表示根据x轴和y轴翻转的度数

 
 

 \####3D旋转

 
 

 transform:

 \- x轴旋转: rotateX(数字deg);

 \- y轴旋转: rotateY(数字deg);

 
 

 \###动画

 
 

 指的是元素在多个样式之间 平稳的过渡.

 
 

 格式:

 步骤1. 定义一个动画

 @keyframes 定义动画名称{

 0%{

 样式列表;

 }

 ...

 100%{

 样式列表;

 }

 }

 步骤2. 使用这个动画

 选择器{

 animation:动画名称 执行时长s;

 animation-iteration-count:重复次数;

 }

 \--------------------------------------------------