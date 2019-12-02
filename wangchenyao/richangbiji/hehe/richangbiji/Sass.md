# 											Sass 

![](/home/yao/下载/1.png)

2-003 Sass:

​	https://www.sass.hk/



[Sass中文网](https://www.sass.hk/)

- [首页](https://www.sass.hk/)
- [安装](https://www.sass.hk/install/)
- [快速入门](https://www.sass.hk/guide/)
- [中文文档](https://www.sass.hk/docs/)
- [常见问题](https://www.sass.hk/faq/)
- [使用技巧](https://www.sass.hk/skill/)
- [Sass在线转换](https://www.sass.hk/css2sass/)
- [关于](https://www.sass.hk/about/)
- [Language](https://www.sass.hk/guide/#)

# 快速入门



- [1. 使用变量](https://www.sass.hk/guide/#a1)
- [2. 嵌套CSS 规则](https://www.sass.hk/guide/#b1)
- [3. 导入SASS文件;](https://www.sass.hk/guide/#c1)
- [4. 静默注释;](https://www.sass.hk/guide/#d1)
- [5. 混合器;](https://www.sass.hk/guide/#e1)
- [6. 使用选择器继承来精简CSS;](https://www.sass.hk/guide/#f1)
- [7. 小结;](https://www.sass.hk/guide/#g1)

# 1. 使用变量;

`sass`让人们受益的一个重要特性就是它为`css`引入了变量。你可以把反复使用的`css`属性值 定义成变量，然后通过变量名来引用它们，而无需重复书写这一属性值。或者，对于仅使用过一 次的属性值，你可以赋予其一个易懂的变量名，让人一眼就知道这个属性值的用途。

`sass`使用`$`符号来标识变量(老版本的`sass`使用`!`来标识变量。改成$是多半因为`!highlight-color`看起来太丑了。)，比如`$highlight-color`和`$sidebar-width`。为什么选择`$` 符号呢？因为它好认、更具美感，且在CSS中并无他用，不会导致与现存或未来的`css`语法冲突。

# 1-1. 变量声明;

`sass`变量的声明和`css`属性的声明很像：

```
$highlight-color: #F90;
```

这意味着变量`$highlight-color`现在的值是`#F90`。任何可以用作`css`属性值的赋值都 可以用作`sass`的变量值，甚至是以空格分割的多个属性值，如`$basic-border: 1px solid black;`，或以逗号分割的多个属性值，如`$plain-font: "Myriad Pro"、Myriad、"Helvetica Neue"、Helvetica、"Liberation Sans"、Arial和sans-serif; sans-serif;`。这时变 量还没有生效，除非你引用这个变量——我们很快就会了解如何引用。

与`CSS`属性不同，变量可以在`css`规则块定义之外存在。当变量定义在`css`规则块内，那么该变量只能在此规则块内使用。如果它们出现在任何形式的`{...}`块中（如`@media`或者`@font-face`块），情况也是如此：

```
$nav-color: #F90;
nav {
  $width: 100px;
  width: $width;
  color: $nav-color;
}

//编译后

nav {
  width: 100px;
  color: #F90;
}
```

在这段代码中，`$nav-color`这个变量定义在了规则块外边，所以在这个样式表中都可以像 `nav`规则块那样引用它。`$width`这个变量定义在了`nav`的`{ }`规则块内，所以它只能在`nav`规则块 内使用。这意味着是你可以在样式表的其他地方定义和使用`$width`变量，不会对这里造成影响。

只声明变量其实没啥用处，我们最终的目的还是使用它们。上例已介绍了如何使用 `$nav-color`和`$width`这两个变量，接下来我们将进一步探讨变量的使用方法。



# 1-2. 变量引用;

凡是`css`属性的标准值（比如说1px或者bold）可存在的地方，变量就可以使用。`css`生成时，变量会被它们的值所替代。之后，如果你需要一个不同的值，只需要改变这个变量的值，则所有引用此变量的地方生成的值都会随之改变。

```
$highlight-color: #F90;
.selected {
  border: 1px solid $highlight-color;
}

//编译后

.selected {
  border: 1px solid #F90;
}
```

看上边示例中的`$highlight-color`变量，它被直接赋值给`border`属性，当这段代码被编译输出`css`时，`$highlight-color`会被`#F90`这一颜色值所替代。产生的效果就是给`selected`这个类一条1像素宽、实心且颜色值为`#F90`的边框。

在声明变量时，变量值也可以引用其他变量。当你通过粒度区分，为不同的值取不同名字时，这相当有用。下例在独立的颜色值粒度上定义了一个变量，且在另一个更复杂的边框值粒度上也定义了一个变量：

```
$highlight-color: #F90;
$highlight-border: 1px solid $highlight-color;
.selected {
  border: $highlight-border;
}

//编译后

.selected {
  border: 1px solid #F90;
}
```

这里，`$highlight-border`变量的声明中使用了`$highlight-color`这个变量。产生的效 果就跟你直接为`border`属性设置了一个`1px` `$highlight-color solid`的值是一样的。 最后，我们来了解一下变量命名的实用技巧，以结束关于变量的介绍。



# 1-3. 变量名用中划线还是下划线分隔;

`sass`的变量名可以与`css`中的属性名和选择器名称相同，包括中划线和下划线。这完全取决于个人的喜好，有些人喜欢使用中划线来分隔变量中的多个词（如`$highlight-color`），而有些人喜欢使用下划线（如`$highlight_color`）。使用中划线的方式更为普遍，这也是`compass`和本文都用的方式。

不过，`sass`并不想强迫任何人一定使用中划线或下划线，所以这两种用法相互兼容。用中划线声明的变量可以使用下划线的方式引用，反之亦然。这意味着即使`compass`选择用中划线的命名方式，这并不影响你在使用`compass`的样式中用下划线的命名方式进行引用：

```
$link-color: blue;
a {
  color: $link_color;
}

//编译后

a {
  color: blue;
}
```

在上例中，`$link-color`和`$link_color`其实指向的是同一个变量。实际上，在`sass`的大 多数地方，中划线命名的内容和下划线命名的内容是互通的，除了变量，也包括对混合器和Sass函数的命名。但是在`sass`中纯`css`部分不互通，比如类名、ID或属性名。

尽管变量自身提供了很多有用的地方，但是`sass`基于变量提供的更为强大的工具才是我们关注的焦点。只有当变量与`sass`的其他特性一起使用时，才能发挥其全部的潜能。接下来，我们将探讨其中一个非常重要的特性，即规则嵌套。

# 2. 嵌套CSS 规则;

`css`中重复写选择器是非常恼人的。如果要写一大串指向页面中同一块的样式时，往往需要 一遍又一遍地写同一个`ID`：

```
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

像这种情况，`sass`可以让你只写一遍，且使样式可读性更高。在Sass中，你可以像俄罗斯套娃那样在规则块中嵌套规则块。`sass`在输出`css`时会帮你把这些嵌套规则处理好，避免你的重复书写。

```
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  aside { background-color: #EEE }
}
 /* 编译后 */
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

上边的例子，会在输出`css`时把它转换成跟你之前看到的一样的效果。这个过程中，`sass`用了两步，每一步都是像打开俄罗斯套娃那样把里边的嵌套规则块一个个打开。首先，把`#content`（父级）这个`id`放到`article`选择器（子级）和`aside`选择器（子级）的前边：

```
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  #content aside { background-color: #EEE }
}
 /* 编译后 */
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

然后，`#content article`里边还有嵌套的规则，`sass`重复一遍上边的步骤，把新的选择器添加到内嵌的选择器前边。

一个给定的规则块，既可以像普通的CSS那样包含属性，又可以嵌套其他规则块。当你同时要为一个容器元素及其子元素编写特定样式时，这种能力就非常有用了。

```
#content {
  background-color: #f5f5f5;
  aside { background-color: #eee }
}
```

容器元素的样式规则会被单独抽离出来，而嵌套元素的样式规则会像容器元素没有包含任何属性时那样被抽离出来。

```
#content { background-color: #f5f5f5 }
#content aside { background-color: #eee }
```

大多数情况下这种简单的嵌套都没问题，但是有些场景下不行，比如你想要在嵌套的选择器 里边立刻应用一个类似于`：hover`的伪类。为了解决这种以及其他情况，`sass`提供了一个特殊结 构`&`。

# 2-1. 父选择器的标识符&;

一般情况下，`sass`在解开一个嵌套规则时就会把父选择器（`#content`）通过一个空格连接到子选择器的前边（`article`和`aside`）形成（`#content article`和`#content aside`）。这种在CSS里边被称为后代选择器，因为它选择ID为`content`的元素内所有命中选择器`article`和`aside`的元素。但在有些情况下你却不会希望`sass`使用这种后代选择器的方式生成这种连接。

最常见的一种情况是当你为链接之类的元素写`：hover`这种伪类时，你并不希望以后代选择器的方式连接。比如说，下面这种情况`sass`就无法正常工作：

```
article a {
  color: blue;
  :hover { color: red }
}
```

这意味着`color: red`这条规则将会被应用到选择器`article a :hover`，`article`元素内链接的所有子元素在被`hover`时都会变成红色。这是不正确的！你想把这条规则应用到超链接自身，而后代选择器的方式无法帮你实现。

解决之道为使用一个特殊的`sass`选择器，即父选择器。在使用嵌套规则时，父选择器能对于嵌套规则如何解开提供更好的控制。它就是一个简单的`&`符号，且可以放在任何一个选择器可出现的地方，比如`h1`放在哪，它就可以放在哪。

```
article a {
  color: blue;
  &:hover { color: red }
}
```

当包含父选择器标识符的嵌套规则被打开时，它不会像后代选择器那样进行拼接，而是`&`被父选择器直接替换：

```
article a { color: blue }
article a:hover { color: red }
```

在为父级选择器添加`：hover`等伪类时，这种方式非常有用。同时父选择器标识符还有另外一种用法，你可以在父选择器之前添加选择器。举例来说，当用户在使用IE浏览器时，你会通过`JavaScript`在``标签上添加一个ie的类名，为这种情况编写特殊的样式如下：

```
#content aside {
  color: red;
  body.ie & { color: green }
}
/*编译后*/
#content aside {color: red};
body.ie #content aside { color: green }
```

`sass`在选择器嵌套上是非常智能的，即使是带有父选择器的情况。当`sass`遇到群组选择器（由多个逗号分隔开的选择器形成）也能完美地处理这种嵌套。

# 2-2. 群组选择器的嵌套;

在`CSS`里边，选择器`h1``h2`和`h3`会同时命中h1元素、h2元素和h3元素。与此类似，`.button` `button`会命中button元素和类名为.button的元素。这种选择器称为群组选择器。群组选择器 的规则会对命中群组中任何一个选择器的元素生效。

```
.button, button {
  margin: 0;
}
```

当看到上边这段代码时，你可能还没意识到会有重复性的工作。但会很快发现：如果你需要在一个特定的容器元素内对这样一个群组选择器进行修饰，情况就不同了。`css`的写法会让你在群组选择器中的每一个选择器前都重复一遍容器元素的选择器。

```
.container h1, .container h2, .container h3 { margin-bottom: .8em }
```

非常幸运，`sass`的嵌套特性在这种场景下也非常有用。当`sass`解开一个群组选择器规则内嵌的规则时，它会把每一个内嵌选择器的规则都正确地解出来：

```
.container {
  h1, h2, h3 {margin-bottom: .8em}
}
```

首先`sass`将`.container`和`h1``.container`和`h2``.container`和`h3`分别组合，然后将三 者重新组合成一个群组选择器，生成你前边看到的普通`css`样式。对于内嵌在群组选择器内的嵌 套规则，处理方式也一样：

```
nav, aside {
  a {color: blue}
}
```

首先`sass`将`nav`和`a``aside`和`a`分别组合，然后将二者重新组合成一个群组选择器：

```
nav a, aside a {color: blue}
```

处理这种群组选择器规则嵌套上的强大能力，正是`sass`在减少重复敲写方面的贡献之一。尤其在当嵌套级别达到两层甚至三层以上时，与普通的`css`编写方式相比，只写一遍群组选择器大大减少了工作量。

有利必有弊，你需要特别注意群组选择器的规则嵌套生成的`css`。虽然`sass`让你的样式表看上去很小，但实际生成的`css`却可能非常大，这会降低网站的速度。



关于选择器嵌套的最后一个方面，我们看看`sass`如何处理组合选择器，比如>、+和~的使用。你将看到，这种场景下你甚至无需使用父选择器标识符。

# 2-3. 子组合选择器和同层组合选择器：>、+和~;

上边这三个组合选择器必须和其他选择器配合使用，以指定浏览器仅选择某种特定上下文中的元素。

```
article section { margin: 5px }
article > section { border: 1px solid #ccc }
```

你可以用子组合选择器>选择一个元素的直接子元素。上例中，第一个选择器会选择article下的所有命中section选择器的元素。第二个选择器只会选择article下紧跟着的子元素中命中section选择器的元素。

在下例中，你可以用同层相邻组合选择器`+`选择`header`元素后紧跟的`p`元素：

```
header + p { font-size: 1.1em }
```

你也可以用同层全体组合选择器`~`，选择所有跟在`article`后的同层`article`元素，不管它们之间隔了多少其他元素：

```
article ~ article { border-top: 1px dashed #ccc }
```

这些组合选择器可以毫不费力地应用到`sass`的规则嵌套中。可以把它们放在外层选择器后边，或里层选择器前边：

```
article {
  ~ article { border-top: 1px dashed #ccc }
  > section { background: #eee }
  dl > {
    dt { color: #333 }
    dd { color: #555 }
  }
  nav + & { margin-top: 0 }
}
```

`sass`会如你所愿地将这些嵌套规则一一解开组合在一起：

```
article ~ article { border-top: 1px dashed #ccc }
article > footer { background: #eee }
article dl > dt { color: #333 }
article dl > dd { color: #555 }
nav + article { margin-top: 0 }
```

在`sass`中，不仅仅`css`规则可以嵌套，对属性进行嵌套也可以减少很多重复性的工作。

# 2-4. 嵌套属性;

在`sass`中，除了CSS选择器，属性也可以进行嵌套。尽管编写属性涉及的重复不像编写选择器那么糟糕，但是要反复写`border-style``border-width``border-color`以及`border-*`等也是非常烦人的。在`sass`中，你只需敲写一遍`border`：

```
nav {
  border: {
  style: solid;
  width: 1px;
  color: #ccc;
  }
}
```

嵌套属性的规则是这样的：把属性名从中划线-的地方断开，在根属性后边添加一个冒号:，紧跟一个`{ }`块，把子属性部分写在这个`{ }`块中。就像`css`选择器嵌套一样，`sass`会把你的子属性一一解开，把根属性和子属性部分通过中划线-连接起来，最后生成的效果与你手动一遍遍写的`css`样式一样：

```
nav {
  border-style: solid;
  border-width: 1px;
  border-color: #ccc;
}
```

对于属性的缩写形式，你甚至可以像下边这样来嵌套，指明例外规则：

```
nav {
  border: 1px solid #ccc {
  left: 0px;
  right: 0px;
  }
}
```

这比下边这种同等样式的写法要好：

```
nav {
  border: 1px solid #ccc;
  border-left: 0px;
  border-right: 0px;
}
```

属性和选择器嵌套是非常伟大的特性，因为它们不仅大大减少了你的编写量，而且通过视觉上的缩进使你编写的样式结构更加清晰，更易于阅读和开发。

即便如此，随着你的样式表变得越来越大，这种写法也很难保持结构清晰。有时，处理这种大量样式的唯一方法就是把它们分拆到多个文件中。`sass`通过对`css`原有`@import`规则的改进直接支持了这一特性。

# 3. 导入SASS文件;

`css`有一个特别不常用的特性，即`@import`规则，它允许在一个`css`文件中导入其他`css`文件。然而，后果是只有执行到`@import`时，浏览器才会去下载其他`css`文件，这导致页面加载起来特别慢。

`sass`也有一个`@import`规则，但不同的是，`sass`的`@import`规则在生成`css`文件时就把相关文件导入进来。这意味着所有相关的样式被归纳到了同一个`css`文件中，而无需发起额外的下载请求。另外，所有在被导入文件中定义的变量和混合器（参见2.5节）均可在导入文件中使用。



使用`sass`的`@import`规则并不需要指明被导入文件的全名。你可以省略`.sass`或`.scss`文件后缀（见下图）。这样，在不修改样式表的前提下，你完全可以随意修改你或别人写的被导入的`sass`样式文件语法，在`sass`和`scss`语法之间随意切换。举例来说，`@import`"sidebar";这条命令将把`sidebar.scss`文件中所有样式添加到当前样式表中。

![img](https://www.sass.hk/images/p1.png)

本节将介绍如何使用`sass`的`@import`来处理多个`sass`文件。首先，我们将学习编写那些被导入的`sass`文件，因为在一个大型`sass`项目中，这样的文件是你最常编写的那一类。接着，了解集中导入`sass`文件的方法，使你的样式可重用性更高，包括声明可自定义的变量值，以及在某一个选择器范围内导入`sass`文件。最后，介绍如何在`sass`中使用`css`原生的`@import`命令。

通常，有些`sass`文件用于导入，你并不希望为每个这样的文件单独地生成一个`css`文件。对此，`sass`用一个特殊的约定来解决。

# 3-1. 使用SASS部分文件;

当通过`@import`把`sass`样式分散到多个文件时，你通常只想生成少数几个`css`文件。那些专门为`@import`命令而编写的`sass`文件，并不需要生成对应的独立`css`文件，这样的`sass`文件称为局部文件。对此，`sass`有一个特殊的约定来命名这些文件。

此约定即，`sass`局部文件的文件名以下划线开头。这样，`sass`就不会在编译时单独编译这个文件输出`css`，而只把这个文件用作导入。当你`@import`一个局部文件时，还可以不写文件的全名，即省略文件名开头的下划线。举例来说，你想导入`themes/_night-sky.scss`这个局部文件里的变量，你只需在样式表中写`@import` `"themes/night-sky";`。



局部文件可以被多个不同的文件引用。当一些样式需要在多个页面甚至多个项目中使用时，这非常有用。在这种情况下，有时需要在你的样式表中对导入的样式稍作修改，`sass`有一个功能刚好可以解决这个问题，即默认变量值。

# 3-2. 默认变量值;

一般情况下，你反复声明一个变量，只有最后一处声明有效且它会覆盖前边的值。举例说明：

```
$link-color: blue;
$link-color: red;
a {
color: $link-color;
}
```

在上边的例子中，超链接的`color`会被设置为`red`。这可能并不是你想要的结果，假如你写了一个可被他人通过`@import`导入的`sass`库文件，你可能希望导入者可以定制修改`sass`库文件中的某些值。使用`sass`的`!default`标签可以实现这个目的。它很像`css`属性中`!important`标签的对立面，不同的是`!default`用于变量，含义是：如果这个变量被声明赋值了，那就用它声明的值，否则就用这个默认值。

```
$fancybox-width: 400px !default;
.fancybox {
width: $fancybox-width;
}
```

在上例中，如果用户在导入你的`sass`局部文件之前声明了一个`$fancybox-width`变量，那么你的局部文件中对`$fancybox-width`赋值`400px`的操作就无效。如果用户没有做这样的声明，则`$fancybox-width`将默认为`400px`。

接下来我们将学习嵌套导入，它允许只在某一个选择器的范围内导入`sass`局部文件。

# 3-3. 嵌套导入;

跟原生的`css`不同，`sass`允许`@import`命令写在`css`规则内。这种导入方式下，生成对应的`css`文件时，局部文件会被直接插入到`css`规则内导入它的地方。举例说明，有一个名为`_blue-theme.scss`的局部文件，内容如下：

```
aside {
  background: blue;
  color: white;
}
```

然后把它导入到一个CSS规则内，如下所示：

```
.blue-theme {@import "blue-theme"}

//生成的结果跟你直接在.blue-theme选择器内写_blue-theme.scss文件的内容完全一样。

.blue-theme {
  aside {
    background: blue;
    color: #fff;
  }
}
```

被导入的局部文件中定义的所有变量和混合器，也会在这个规则范围内生效。这些变量和混合器不会全局有效，这样我们就可以通过嵌套导入只对站点中某一特定区域运用某种颜色主题或其他通过变量配置的样式。

有时，可用`css`原生的`@import`机制，在浏览器中下载必需的`css`文件。`sass`也提供了几种方法来达成这种需求。

# 3-4. 原生的CSS导入;

由于`sass`兼容原生的`css`，所以它也支持原生的`CSS@import`。尽管通常在`sass`中使用`@import`时，`sass`会尝试找到对应的`sass`文件并导入进来，但在下列三种情况下会生成原生的`CSS@import`，尽管这会造成浏览器解析`css`时的额外下载：

- 被导入文件的名字以`.css`结尾；
- 被导入文件的名字是一个URL地址（比如http://www.sass.hk/css/css.css），由此可用谷歌字体API提供的相应服务；
- 被导入文件的名字是`CSS`的url()值。

这就是说，你不能用`sass`的`@import`直接导入一个原始的`css`文件，因为`sass`会认为你想用`css`原生的`@import`。但是，因为`sass`的语法完全兼容`css`，所以你可以把原始的`css`文件改名为`.scss`后缀，即可直接导入了。

文件导入是保证`sass`的代码可维护性和可读性的重要一环。次之但亦非常重要的就是注释了。注释可以帮助样式作者记录写`sass`的过程中的想法。在原生的`css`中，注释对于其他人是直接可见的，但`sass`提供了一种方式可在生成的`css`文件中按需抹掉相应的注释。

# 4. 静默注释;

`css`中注释的作用包括帮助你组织样式、以后你看自己的代码时明白为什么这样写，以及简单的样式说明。但是，你并不希望每个浏览网站源码的人都能看到所有注释。

`sass`另外提供了一种不同于`css`标准注释格式`/* ... */`的注释语法，即静默注释，其内容不会出现在生成的`css`文件中。静默注释的语法跟`JavaScript``Java`等类`C`的语言中单行注释的语法相同，它们以`//`开头，注释内容直到行末。

```
body {
  color: #333; // 这种注释内容不会出现在生成的css文件中
  padding: 0; /* 这种注释内容会出现在生成的css文件中 */
}
```

实际上，`css`的标准注释格式`/* ... */`内的注释内容亦可在生成的`css`文件中抹去。当注释出现在原生`css`不允许的地方，如在`css`属性或选择器中，`sass`将不知如何将其生成到对应`css`文件中的相应位置，于是这些注释被抹掉。

```
body {
  color /* 这块注释内容不会出现在生成的css中 */: #333;
  padding: 1; /* 这块注释内容也不会出现在生成的css中 */ 0;
}
```

你已经掌握了`sass`的静默注释，了解了保持`sass`条理性和可读性的最基本的三个方法：嵌套、导入和注释。现在，我们要进一步学习新特性，这样我们不但能保持条理性还能写出更好的样式。首先要介绍的内容是：使用混合器抽象你的相关样式。

# 5. 混合器;

如果你的整个网站中有几处小小的样式类似（例如一致的颜色和字体），那么使用变量来统一处理这种情况是非常不错的选择。但是当你的样式变得越来越复杂，你需要大段大段的重用样式的代码，独立的变量就没办法应付这种情况了。你可以通过`sass`的混合器实现大段样式的重用。

混合器使用`@mixin`标识符定义。看上去很像其他的`CSS @`标识符，比如说`@media`或者`@font-face`。这个标识符给一大段样式赋予一个名字，这样你就可以轻易地通过引用这个名字重用这段样式。下边的这段`sass`代码，定义了一个非常简单的混合器，目的是添加跨浏览器的圆角边框。

```
@mixin rounded-corners {
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

然后就可以在你的样式表中通过`@include`来使用这个混合器，放在你希望的任何地方。`@include`调用会把混合器中的所有样式提取出来放在`@include`被调用的地方。如果像下边这样写：

```
notice {
  background-color: green;
  border: 2px solid #00aa00;
  @include rounded-corners;
}

//sass最终生成：
.notice {
  background-color: green;
  border: 2px solid #00aa00;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

在`.notice`中的属性`border-radius``-moz-border-radius`和`-webkit-border-radius`全部来自`rounded-corners`这个混合器。这一节将介绍使用混合器来避免重复。通过使用参数，你可以使用混合器把你样式中的通用样式抽离出来，然后轻松地在其他地方重用。实际上，混合器太好用了，一不小心你可能会过度使用。大量的重用可能会导致生成的样式表过大，导致加载缓慢。所以，首先我们将讨论混合器的使用场景，避免滥用。

# 5-1. 何时使用混合器;

利用混合器，可以很容易地在样式表的不同地方共享样式。如果你发现自己在不停地重复一段样式，那就应该把这段样式构造成优良的混合器，尤其是这段样式本身就是一个逻辑单元，比如说是一组放在一起有意义的属性。

判断一组属性是否应该组合成一个混合器，一条经验法则就是你能否为这个混合器想出一个好的名字。如果你能找到一个很好的短名字来描述这些属性修饰的样式，比如`rounded-corners``fancy-font`或者`no-bullets`，那么往往能够构造一个合适的混合器。如果你找不到，这时候构造一个混合器可能并不合适。



混合器在某些方面跟`css`类很像。都是让你给一大段样式命名，所以在选择使用哪个的时候可能会产生疑惑。最重要的区别就是类名是在`html`文件中应用的，而混合器是在样式表中应用的。这就意味着类名具有语义化含义，而不仅仅是一种展示性的描述：用来描述`html`元素的含义而不是`html`元素的外观。而另一方面，混合器是展示性的描述，用来描述一条`css`规则应用之后会产生怎样的效果。

在之前的例子中，`.notice`是一个有语义的类名。如果一个`html`元素有一个`notice`的类名，就表明了这个`html`元素的用途：向用户展示提醒信息。`rounded-corners`混合器是展示性的，它描述了包含它的`css`规则最终的视觉样式，尤其是边框角的视觉样式。混合器和类配合使用写出整洁的`html`和`css`，因为使用语义化的类名亦可以帮你避免重复使用混合器。为了保持你的`html`和`css`的易读性和可维护性，在写样式的过程中一定要铭记二者的区别。

有时候仅仅把属性放在混合器中还远远不够，可喜的是，`sass`同样允许你把`css`规则放在混合器中。

# 5-2. 混合器中的CSS规则;

混合器中不仅可以包含属性，也可以包含`css`规则，包含选择器和选择器中的属性，如下代码:

```
@mixin no-bullets {
  list-style: none;
  li {
    list-style-image: none;
    list-style-type: none;
    margin-left: 0px;
  }
}
```

当一个包含`css`规则的混合器通过`@include`包含在一个父规则中时，在混合器中的规则最终会生成父规则中的嵌套规则。举个例子，看看下边的`sass`代码，这个例子中使用了`no-bullets`这个混合器：

```
ul.plain {
  color: #444;
  @include no-bullets;
}
```

`sass`的`@include`指令会将引入混合器的那行代码替换成混合器里边的内容。最终，上边的例子如下代码:

```
ul.plain {
  color: #444;
  list-style: none;
}
ul.plain li {
  list-style-image: none;
  list-style-type: none;
  margin-left: 0px;
}
```

混合器中的规则甚至可以使用`sass`的父选择器标识符`&`。使用起来跟不用混合器时一样，`sass`解开嵌套规则时，用父规则中的选择器替代`&`。

如果一个混合器只包含`css`规则，不包含属性，那么这个混合器就可以在文档的顶部调用，写在所有的`css`规则之外。如果你只是为自己写一些混合器，这并没有什么大的用途，但是当你使用一个类似于`Compass`的库时，你会发现，这是提供样式的好方法，原因在于你可以选择是否使用这些样式。

接下来你将学习如何通过给混合器传参数来让混合器变得更加灵活和可重用。

# 5-3. 给混合器传参;

混合器并不一定总得生成相同的样式。可以通过在`@include`混合器时给混合器传参，来定制混合器生成的精确样式。当`@include`混合器时，参数其实就是可以赋值给`css`属性值的变量。如果你写过`JavaScript`，这种方式跟`JavaScript`的`function`很像：

```
@mixin link-colors($normal, $hover, $visited) {
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
```

当混合器被`@include`时，你可以把它当作一个`css`函数来传参。如果你像下边这样写：

```
a {
  @include link-colors(blue, red, green);
}

//Sass最终生成的是：

a { color: blue; }
a:hover { color: red; }
a:visited { color: green; }
```

当你@include混合器时，有时候可能会很难区分每个参数是什么意思，参数之间是一个什么样的顺序。为了解决这个问题，`sass`允许通过语法`$name: value`的形式指定每个参数的值。这种形式的传参，参数顺序就不必再在乎了，只需要保证没有漏掉参数即可：

```
a {
    @include link-colors(
      $normal: blue,
      $visited: green,
      $hover: red
  );
}
```

尽管给混合器加参数来实现定制很好，但是有时有些参数我们没有定制的需要，这时候也需要赋值一个变量就变成很痛苦的事情了。所以`sass`允许混合器声明时给参数赋默认值。

# 5-4. 默认参数值;

为了在`@include`混合器时不必传入所有的参数，我们可以给参数指定一个默认值。参数默认值使用`$name: default-value`的声明形式，默认值可以是任何有效的`css`属性值，甚至是其他参数的引用，如下代码：

```
@mixin link-colors(
    $normal,
    $hover: $normal,
    $visited: $normal
  )
{
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
```

如果像下边这样调用：`@include link-colors(red)` `$hover`和`$visited`也会被自动赋值为`red`。

混合器只是`sass`样式重用特性中的一个。我们已经了解到混合器主要用于样式展示层的重用，如果你想重用语义化的类呢？这就涉及`sass`的另一个重要的重用特性：选择器继承。

# 6. 使用选择器继承来精简CSS;

使用`sass`的时候，最后一个减少重复的主要特性就是选择器继承。基于`Nicole Sullivan`面向对象的`css`的理念，选择器继承是说一个选择器可以继承为另一个选择器定义的所有样式。这个通过`@extend`语法实现，如下代码:

```
//通过选择器继承继承样式
.error {
  border: 1px solid red;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

在上边的代码中，`.seriousError`将会继承样式表中任何位置处为`.error`定义的所有样式。以`class="seriousError"` 修饰的`html`元素最终的展示效果就好像是`class="seriousError error"`。相关元素不仅会拥有一个`3px`宽的边框，而且这个边框将变成红色的，这个元素同时还会有一个浅红色的背景，因为这些都是在`.error`里边定义的样式。

`.seriousError`不仅会继承`.error`自身的所有样式，任何跟`.error`有关的组合选择器样式也会被`.seriousError`以组合选择器的形式继承，如下代码:

```
//.seriousError从.error继承样式
.error a{  //应用到.seriousError a
  color: red;
  font-weight: 100;
}
h1.error { //应用到hl.seriousError
  font-size: 1.2rem;
}
```

如上所示，在`class="seriousError"`的`html`元素内的超链接也会变成红色和粗体。

本节将介绍与混合器相比，哪种情况下更适合用继承。接下来在探索继承的工作细节之前，我们先了解一下继承的高级用法。最后，我们将看看使用继承可能会有哪些坑，学习如何避免这些坑。

# 6-1. 何时使用继承;

5-1节介绍了[混合器](https://www.sass.hk/guide/)主要用于展示性样式的重用，而类名用于语义化样式的重用。因为继承是基于类的（有时是基于其他类型的选择器），所以继承应该是建立在语义化的关系上。当一个元素拥有的类（比如说`.seriousError`）表明它属于另一个类（比如说`.error`），这时使用继承再合适不过了。

这有点抽象，所以我们从几个方面来阐释一下。想象一下你正在编写一个页面，给`html`元素添加类名，你发现你的某个类（比如说`.seriousError`）另一个类（比如说`.error`）的细化。你会怎么做？

- 你可以为这两个类分别写相同的样式，但是如果有大量的重复怎么办？使用`sass`时，我们提倡的就是不要做重复的工作。
- 你可以使用一个选择器组（比如说`.error``.seriousError`）给这两个选择器写相同的样式。如果.error的所有样式都在同一个地方，这种做法很好，但是如果是分散在样式表的不同地方呢？再这样做就困难多了。
- 

- 你可以使用一个混合器为这两个类提供相同的样式，但当`.error`的样式修饰遍布样式表中各处时，这种做法面临着跟使用选择器组一样的问题。这两个类也不是恰好有相同的 样式。你应该更清晰地表达这种关系。
- 综上所述你应该使用`@extend`。让`.seriousError`从`.error`继承样式，使两者之间的关系非常清晰。更重要的是无论你在样式表的哪里使用`.error``.seriousError`都会继承其中的样式。

现在你已经更好地掌握了何时使用继承，以及继承有哪些突出的优点，接下来我们看看一些高级用法。

# 6-2. 继承的高级用法;

任何`css`规则都可以继承其他规则，几乎任何`css`规则也都可以被继承。大多数情况你可能只想对类使用继承，但是有些场合你可能想做得更多。最常用的一种高级用法是继承一个`html`元素的样式。尽管默认的浏览器样式不会被继承，因为它们不属于样式表中的样式，但是你对`html`元素添加的所有样式都会被继承。

接下来的这段代码定义了一个名为`disabled`的类，样式修饰使它看上去像一个灰掉的超链接。通过继承a这一超链接元素来实现：

```
.disabled {
  color: gray;
  @extend a;
}
```

假如一条样式规则继承了一个复杂的选择器，那么它只会继承这个复杂选择器命中的元素所应用的样式。举例来说， 如果`.seriousError``@extend``.important.error` ， 那么`.important.error` 和`h1.important.error` 的样式都会被`.seriousError`继承， 但是`.important`或者`.error下`的样式则不会被继承。这种情况下你很可能希望`.seriousError`能够分别继承`.important`或者`.error`下的样式。

如果一个选择器序列（`#main .seriousError`）`@extend`另一个选择器（`.error`），那么只有完全匹配`#main .seriousError`这个选择器的元素才会继承`.error`的样式，就像单个类 名继承那样。拥有`class="seriousError"`的`#main`元素之外的元素不会受到影响。

像`#main .error`这种选择器序列是不能被继承的。这是因为从`#main .error`中继承的样式一般情况下会跟直接从`.error`中继承的样式基本一致，细微的区别往往使人迷惑。

现在你已经了解了通过继承能够做些什么事情，接下来我们将学习继承的工作细节，在生成对应`css`的时候，`sass`具体干了些什么事情。

# 6-3. 继承的工作细节;

跟变量和混合器不同，继承不是仅仅用`css`样式替换@extend处的代码那么简单。为了不让你对生成的`css`感觉奇怪，对这背后的工作原理有一定了解是非常重要的。

`@extend`背后最基本的想法是，如果`.seriousError @extend .error`， 那么样式表中的任何一处`.error`都用`.error``.seriousError`这一选择器组进行替换。这就意味着相关样式会如预期那样应用到`.error`和`.seriousError`。当`.error`出现在复杂的选择器中，比如说`h1.error``.error a`或者`#main .sidebar input.error[type="text"]`，那情况就变得复杂多了，但是不用担心，`sass`已经为你考虑到了这些。

关于`@extend`有两个要点你应该知道。

- 跟混合器相比，继承生成的`css`代码相对更少。因为继承仅仅是重复选择器，而不会重复属性，所以使用继承往往比混合器生成的`css`体积更小。如果你非常关心你站点的速度，请牢记这一点。
- 继承遵从`css`层叠的规则。当两个不同的`css`规则应用到同一个`html`元素上时，并且这两个不同的`css`规则对同一属性的修饰存在不同的值，`css`层叠规则会决定应用哪个样式。相当直观：通常权重更高的选择器胜出，如果权重相同，定义在后边的规则胜出。

混合器本身不会引起`css`层叠的问题，因为混合器把样式直接放到了`css`规则中，而继承存在样式层叠的问题。被继承的样式会保持原有定义位置和选择器权重不变。通常来说这并不会引起什么问题，但是知道这点总没有坏处。

# 6-4. 使用继承的最佳实践;

通常使用继承会让你的`css`美观、整洁。因为继承只会在生成`css`时复制选择器，而不会复制大段的`css`属性。但是如果你不小心，可能会让生成的`css`中包含大量的选择器复制。

避免这种情况出现的最好方法就是不要在`css`规则中使用后代选择器（比如`.foo .bar`）去继承`css`规则。如果你这么做，同时被继承的`css`规则有通过后代选择器修饰的样式，生成`css`中的选择器的数量很快就会失控：

```
.foo .bar { @extend .baz; }
.bip .baz { a: b; }
```

在上边的例子中，`sass`必须保证应用到.baz的样式同时也要应用到`.foo .bar`（位于class="foo"的元素内的class="bar"的元素）。例子中有一条应用到`.bip .baz`（位于class="bip"的元素内的class="baz"的元素）的`css`规则。当这条规则应用到`.foo .bar`时，可能存在三种情况，如下代码:

```
<!-- 继承可能迅速变复杂 -->
<!-- Case 1 -->
<div class="foo">
  <div class="bip">
    <div class="bar">...</div>
  </div>
</div>
<!-- Case 2 -->
<div class="bip">
  <div class="foo">
    <div class="bar">...</div>
  </div>
</div>
<!-- Case 3 -->
<div class="foo bip">
  <div class="bar">...</div>
</div>
```

为了应付这些情况，`sass`必须生成三种选择器组合（仅仅是.bip .foo .bar不能覆盖所有情况）。如果任何一条规则里边的后代选择器再长一点，`sass`需要考虑的情况就会更多。实际上`sass`并不总是会生成所有可能的选择器组合，即使是这样，选择器的个数依然可能会变得相当大，所以如果允许，尽可能避免这种用法。

值得一提的是，只要你想，你完全可以放心地继承有后代选择器修饰规则的选择器，不管后代选择器多长，但有一个前提就是，不要用后代选择器去继承。

# 7. 小结;

本文介绍了`sass`最基本部分,你可以轻松地使用`sass`编写清晰、无冗余、语义化的`css`。对于`sass`提供的工具你已经有了一个比较深入的了解，同时也掌握了何时使用这些工具的指导原则。

变量是`sass`提供的最基本的工具。通过变量可以让独立的`css`值变得可重用，无论是在一条单独的规则范围内还是在整个样式表中。变量、混合器的命名甚至`sass`的文件名，可以互换通用`_`和`-`。同样基础的是`sass`的嵌套机制。嵌套允许`css`规则内嵌套`css`规则，减少重复编写常用的选择器，同时让样式表的结构一眼望去更加清晰。`sass`同时提供了特殊的父选择器标识符`&`，通过它可以构造出更高效的嵌套。

你也已经学到了`sass`的另一个重要特性，样式导入。通过样式导入可以把分散在多个`sass`文件中的内容合并生成到一个`css`文件，避免了项目中有大量的`css`文件通过原生的`css` `@import`带来的性能问题。通过嵌套导入和默认变量值，导入可以构建更强有力的、可定制的样式。混合器允许用户编写语义化样式的同时避免视觉层面上样式的重复。你不仅学到了如何使用混合器减少重复，同时学习到了如何使用混合器让你的`css`变得更加可维护和语义化。最后，我们学习了与混合器相辅相成的选择器继承。继承允许你声明类之间语义化的关系，通过这些关系可以保持你的`css`的整洁和可维护性。



# 中文文档

[Sass中文网](https://www.sass.hk/)

- [首页](https://www.sass.hk/)
- [安装](https://www.sass.hk/install/)
- [快速入门](https://www.sass.hk/guide/)
- [中文文档](https://www.sass.hk/docs/)
- [常见问题](https://www.sass.hk/faq/)
- [使用技巧](https://www.sass.hk/skill/)
- [Sass在线转换](https://www.sass.hk/css2sass/)
- [关于](https://www.sass.hk/about/)
- [Language](https://www.sass.hk/docs/#)

# 中文文档



[1. 特色功能](https://www.sass.hk/docs/#t1)[2. 语法格式](https://www.sass.hk/docs/#t2)[3. 使用 Sass](https://www.sass.hk/docs/#t3)[1. Rack/Rails/Merb Plugin](https://www.sass.hk/docs/#t3-1)[2. 缓存](https://www.sass.hk/docs/#t3-2)[3. 配置选项](https://www.sass.hk/docs/#t3-3)[4. 判断语法格式](https://www.sass.hk/docs/#t3-4)[5. 编码格式](https://www.sass.hk/docs/#t3-5)[4. CSS 功能拓展](https://www.sass.hk/docs/#t4)[1. 嵌套规则](https://www.sass.hk/docs/#t4-1)[2. 父选择器 &](https://www.sass.hk/docs/#t4-2)[3. 属性嵌套](https://www.sass.hk/docs/#t4-3)[4. 占位符选择器 %foo](https://www.sass.hk/docs/#t4-4)[5. 注释 /* */ 与 //](https://www.sass.hk/docs/#t5)[6. SassScript](https://www.sass.hk/docs/#t6)[1. Interactive Shell](https://www.sass.hk/docs/#t6-1)[2. 变量 $](https://www.sass.hk/docs/#t6-2)[3. 数据类型](https://www.sass.hk/docs/#t6-3)[1. 字符串](https://www.sass.hk/docs/#t6-3-1)[2. 数组](https://www.sass.hk/docs/#t6-3-2)[3. Maps](https://www.sass.hk/docs/#t6-3-3)[4. 颜色](https://www.sass.hk/docs/#t6-3-4)[4. 运算](https://www.sass.hk/docs/#t6-4)[1. 数字运算](https://www.sass.hk/docs/#t6-4-1)[1. 除法运算 /](https://www.sass.hk/docs/#t6-4-1-1)[2. 颜色值运算](https://www.sass.hk/docs/#t6-4-2)[3. 字符串运算](https://www.sass.hk/docs/#t6-4-3)[4. 布尔运算](https://www.sass.hk/docs/#t6-4-4)[5. 数组运算](https://www.sass.hk/docs/#t6-4-5)[5. 圆括号](https://www.sass.hk/docs/#t6-5)[6. 函数](https://www.sass.hk/docs/#t6-6)[1. 关键词参数](https://www.sass.hk/docs/#t6-6-1)[7. 插值语句 #{}](https://www.sass.hk/docs/#t6-7)[8. & in SassScript](https://www.sass.hk/docs/#t6-8)[9. 变量定义 !default](https://www.sass.hk/docs/#t6-9)[7. @-Rules 与指令](https://www.sass.hk/docs/#t7)[1. @import](https://www.sass.hk/docs/#t7-1)[1. 分音](https://www.sass.hk/docs/#7-1-1)[2. 嵌套 @import](https://www.sass.hk/docs/#7-1-2)[2. @media](https://www.sass.hk/docs/#t7-2)[3. @extend](https://www.sass.hk/docs/#t7-3)[1. How it Works](https://www.sass.hk/docs/#7-3-1)[2. 延伸复杂的选择器](https://www.sass.hk/docs/#7-3-2)[3. 多重延伸](https://www.sass.hk/docs/#7-3-3)[4. 继续延伸](https://www.sass.hk/docs/#7-3-4)[5. 选择器列](https://www.sass.hk/docs/#7-3-5)[1. 合并选择器列](https://www.sass.hk/docs/#7-3-5-1)[6. @extend-Only 选择器](https://www.sass.hk/docs/#7-3-6)[7. !optional 声明](https://www.sass.hk/docs/#7-3-7)[8. 在指令中延伸](https://www.sass.hk/docs/#7-3-8)[4. @at-root](https://www.sass.hk/docs/#t7-4)[1. @at-root](https://www.sass.hk/docs/#t7-4-1)[5. @debug](https://www.sass.hk/docs/#t7-5)[6. @warn](https://www.sass.hk/docs/#t7-6)[7. @warn](https://www.sass.hk/docs/#t7-7)[8. 控制指令](https://www.sass.hk/docs/#t8)[1. if](https://www.sass.hk/docs/#t8-1)[2. @if](https://www.sass.hk/docs/#t8-2)[3. @for](https://www.sass.hk/docs/#t8-3)[4. @each](https://www.sass.hk/docs/#t8-4)[8.4.1 Multiple Assignment](https://www.sass.hk/docs/#t8-4-1)[5. @while](https://www.sass.hk/docs/#t8-5)[9. 混合指令](https://www.sass.hk/docs/#9)[1. 定义混合指令 @mixin](https://www.sass.hk/docs/#9-1)[2. 引用混合样式 @include](https://www.sass.hk/docs/#9_2)[3. 参数](https://www.sass.hk/docs/#9_3)[1. 关键词参数](https://www.sass.hk/docs/#9_3_1)[2. 参数变量](https://www.sass.hk/docs/#9_3_2)[4. 向混合样式中导入内容](https://www.sass.hk/docs/#9_4)[1. Variable Scope and Content Blocks](https://www.sass.hk/docs/#9_4_1)[10. 函数指令](https://www.sass.hk/docs/#t10)[11. 输出格式](https://www.sass.hk/docs/#t11)[1. :nested](https://www.sass.hk/docs/#t11-1)[2. :expanded](https://www.sass.hk/docs/#t11-2)[3. :compact](https://www.sass.hk/docs/#t11-3)[4. :compressed](https://www.sass.hk/docs/#t11-4)[12. 拓展 Sass](https://www.sass.hk/docs/#t12)[1. 自定义 Sass 函数](https://www.sass.hk/docs/#t12-1)[2. 存储缓存](https://www.sass.hk/docs/#t12-2)[3. 自定义导入](https://www.sass.hk/docs/#t12-3)

# [Sass (Syntactically Awesome StyleSheets)](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)

Sass 是一款强化 CSS 的辅助工具，它在 CSS 语法的基础上增加了变量 (variables)、嵌套 (nested rules)、混合 (mixins)、导入 (inline imports) 等高级功能，这些拓展令 CSS 更加强大与优雅。使用 Sass 以及 Sass 的样式库（如 [Compass](http://compass-style.org/)）有助于更好地组织管理样式文件，以及更高效地开发项目。

## 1. 特色功能 (Features)

- 完全兼容 CSS3
- 在 CSS 基础上增加变量、嵌套 (nesting)、混合 (mixins) 等功能
- 通过[函数](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html)进行颜色值与属性值的运算
- 提供[控制指令 (control directives)](https://www.sass.hk/docs/#t8)等高级功能
- 自定义输出格式

## 2. 语法格式 (Syntax)

Sass 有两种语法格式。首先是 SCSS (Sassy CSS) —— 也是本文示例所使用的格式 —— 这种格式仅在 CSS3 语法的基础上进行拓展，所有 CSS3 语法在 SCSS 中都是通用的，同时加入 Sass 的特色功能。此外，SCSS 也支持大多数 CSS hacks 写法以及浏览器前缀写法 (vendor-specific syntax)，以及早期的 IE 滤镜写法。这种格式以 `.scss` 作为拓展名。

另一种也是最早的 Sass 语法格式，被称为缩进格式 (Indented Sass) 通常简称 "Sass"，是一种简化格式。它使用 “缩进” 代替 “花括号” 表示属性属于某个选择器，用 “换行” 代替 “分号” 分隔属性，很多人认为这样做比 SCSS 更容易阅读，书写也更快速。缩进格式也可以使用 Sass 的全部功能，只是与 SCSS 相比个别地方采取了不同的表达方式，具体请查看 [the indented syntax reference](http://sass-lang.com/docs/yardoc/file.INDENTED_SYNTAX.html)。这种格式以 `.sass` 作为拓展名。

任何一种格式可以直接 [导入 (@import)](https://www.sass.hk/docs/#t7-1) 到另一种格式中使用，或者通过 `sass-convert` 命令行工具转换成另一种格式：

```
# Convert Sass to SCSS
$ sass-convert style.sass style.scss

# Convert SCSS to Sass
$ sass-convert style.scss style.sass
```

## 3. 使用 Sass (Using Sass)

Sass 可以通过以下三种方式使用：作为命令行工具；作为独立的 Ruby 模块 (Ruby module)；或者作为 Rack-enabled 框架的插件（例如 Ruby on Rails 与 Merb）。无论哪种方式都需要先安装 Sass gem （Windows 系统需要先[安装 Ruby](http://rubyinstaller.org/)）：

```
gem install sass
```

在命令行中运行 Sass：

```
sass input.scss output.css
```

监视单个 Sass 文件，每次修改并保存时自动编译：

```
sass --watch input.scss:output.css
```

监视整个文件夹：

```
sass --watch app/sass:public/stylesheets
```

更多命令的用法请通过 `sass --help` 获取帮助。

在 Ruby 中使用 Sass 也非常容易，Sass gem 安装完毕后运行 `require "sass"` 然后按照下面的方法使用 [Sass::Engine](http://sass-lang.com/docs/yardoc/Sass/Engine.html)：

```
engine = Sass::Engine.new("#main {background-color: #0000ff}", :syntax => :scss)
engine.render #=> "#main { background-color: #0000ff; }\n"
```

### 3.1. Rack/Rails/Merb Plugin

在 Rails 3 之前的版本中使用 Sass，需要在 `environment.rb` 文件中添加：

```
config.gem "sass"
```

Rails 3 则需要在 Gemfile 中添加：

```
gem "sass"
```

在 Merb 中使用 Sass，需要在 `config/dependencies.rb` 中添加：

```
dependency "merb-haml"
```

在 Rack 中使用 Sass，需要在 `config.ru` 中添加：

```
require 'sass/plugin/rack'
use Sass::Plugin::Rack
```

样式文件与 views 不同，不包含任何动态内容，因此 CSS 只需要在 Sass 文件被修改后再编译生成。默认情况下 `.sass` 与 `.scss` 文件放置在 `public/stylesheets/sass` 中（可通过 [:template_location](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#template_location-option) 修改路径），编译生成的 CSS 文件放置在 `public/stylesheets` 中。例如 `public/stylesheets/sass/main.scss` 编译生成 `public/stylesheets/main.css`。

### 3.2. 缓存 (Caching)

Sass 自动缓存编译后的模板与 [partials](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#partials)，这样做能够显著提升重新编译的速度，尤其在处理由 `@import` 导入多个子文件的大型项目时。

单独使用 Sass，缓存内容保存在 `.sass-cache` 文件夹中。在 Rails 和 Merb 项目中缓存文件保存在 `tmp/sass-cache` 文件夹中（可通过 [`:cache_location`](https://www.sass.hk/docs/) 修改路径）。禁用缓存可将 `:cache` 设为 `false`。

### 3.3. 配置选项 (Options)

[暂未翻译](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#options)

### 3.4. 判断语法格式 (Syntax Selection)

Sass 命令行工具根据文件的拓展名判断所使用的语法格式，没有文件名时 `sass` 命令默认编译 `.sass` 文件，添加 `--scss` 选项或者使用 `scss` 命令编译 SCSS 文件。

### 3.5. 编码格式 (Encodings)

在 Ruby 1.9 及以上环境中运行 Sass 时，Sass 对文件的编码格式比较敏感，首先会根据 [CSS spec](http://www.w3.org/TR/2013/WD-css-syntax-3-20130919/#determine-the-fallback-encoding) 判断样式文件的编码格式，如果失败则检测 Ruby string encoding。也就是说，Sass 首先检查 Unicode byte order mark，然后是 `@charset` 声明，最后是 Ruby string encoding，假如都没有检测到，默认使用 UTF-8 编码。

与 CSS 相同，使用 `@charset` 可以声明特定的编码格式。在样式文件的起始位置（前面没有任何空白与注释）插入 `@charset "encoding-name"`， Sass 将会按照给出的编码格式编译文件。注意所使用的编码格式必须可转换为 Unicode 字符集。

Sass 以 UTF-8 编码输出 CSS 文件，当且仅当编译后的文件中包含非 ASCII 字符时，才会在输出文件中添加 `@charset` 声明，而在压缩模式下 (compressed mode) 使用 UTF-8 byte order mark 代替 `@charset` 声明语句。

## 4. CSS 功能拓展 (CSS Extensions)

### 4.1. 嵌套规则 (Nested Rules)

Sass 允许将一套 CSS 样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器，例如：

```scss
#main p {
  color: #00ff00;
  width: 97%;

  .redbox {
    background-color: #ff0000;
    color: #000000;
  }
}
```

编译为

```css
#main p {
  color: #00ff00;
  width: 97%; }
  #main p .redbox {
    background-color: #ff0000;
    color: #000000; }
```

嵌套功能避免了重复输入父选择器，而且令复杂的 CSS 结构更易于管理：

```scss
#main {
  width: 97%;

  p, div {
    font-size: 2em;
    a { font-weight: bold; }
  }

  pre { font-size: 3em; }
}
```

编译为

```css
#main {
  width: 97%; }
  #main p, #main div {
    font-size: 2em; }
    #main p a, #main div a {
      font-weight: bold; }
  #main pre {
    font-size: 3em; }
```

### 4.2. 父选择器 `&` (Referencing Parent Selectors: `&`)

在嵌套 CSS 规则时，有时也需要直接使用嵌套外层的父选择器，例如，当给某个元素设定 `hover` 样式时，或者当 `body` 元素有某个 classname 时，可以用 `&` 代表嵌套规则外层的父选择器。

```scss
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```

编译为

```css
a {
  font-weight: bold;
  text-decoration: none; }
  a:hover {
    text-decoration: underline; }
  body.firefox a {
    font-weight: normal; }
```

编译后的 CSS 文件中 `&` 将被替换成嵌套外层的父选择器，如果含有多层嵌套，最外层的父选择器会一层一层向下传递：

```scss
#main {
  color: black;
  a {
    font-weight: bold;
    &:hover { color: red; }
  }
}
```

编译为

```css
#main {
  color: black; }
  #main a {
    font-weight: bold; }
    #main a:hover {
      color: red; }
```

`&` 必须作为选择器的第一个字符，其后可以跟随后缀生成复合的选择器，例如

```scss
#main {
  color: black;
  &-sidebar { border: 1px solid; }
}
```

编译为

```css
#main {
  color: black; }
  #main-sidebar {
    border: 1px solid; }
```

当父选择器含有不合适的后缀时，Sass 将会报错。

### 4.3. 属性嵌套 (Nested Properties)

有些 CSS 属性遵循相同的命名空间 (namespace)，比如 `font-family, font-size, font-weight` 都以 `font` 作为属性的命名空间。为了便于管理这样的属性，同时也为了避免了重复输入，Sass 允许将属性嵌套在命名空间中，例如：

```scss
.funky {
  font: {
    family: fantasy;
    size: 30em;
    weight: bold;
  }
}
```

编译为

```css
.funky {
  font-family: fantasy;
  font-size: 30em;
  font-weight: bold; }
```

命名空间也可以包含自己的属性值，例如：

```scss
.funky {
  font: 20px/24px {
    family: fantasy;
    weight: bold;
  }
}
```

编译为

```css
.funky {
  font: 20px/24px;
    font-family: fantasy;
    font-weight: bold; }
```

### 4.4. 占位符选择器 `%foo` (Placeholder Selectors: `%foo`)

Sass 额外提供了一种特殊类型的选择器：占位符选择器 (placeholder selector)。与常用的 id 与 class 选择器写法相似，只是 `#` 或 `.` 替换成了 `%`。必须通过 [@extend](https://www.sass.hk/docs/#t7-3) 指令调用，更多介绍请查阅 [@extend-Only Selectors](https://www.sass.hk/docs/#t7-3-6)。

当占位符选择器单独使用时（未通过 `@extend` 调用），不会编译到 CSS 文件中。

## 5. 注释 `/* */` 与 `//` (Comments: `/* */` and `//`)

Sass 支持标准的 CSS 多行注释 `/* */`，以及单行注释 `//`，前者会 被完整输出到编译后的 CSS 文件中，而后者则不会，例如：

```scss
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body { color: black; }

// These comments are only one line long each.
// They won't appear in the CSS output,
// since they use the single-line comment syntax.
a { color: green; }
```

编译为

```css
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body {
  color: black; }

a {
  color: green; }
```

将 `!` 作为多行注释的第一个字符表示在压缩输出模式下保留这条注释并输出到 CSS 文件中，通常用于添加版权信息。

插值语句 (interpolation) 也可写进多行注释中输出变量值：

```scss
$version: "1.2.3";
/* This CSS is generated by My Snazzy Framework version #{$version}. */
```

编译为

```css
/* This CSS is generated by My Snazzy Framework version 1.2.3. */
```

## 6. SassScript

在 CSS 属性的基础上 Sass 提供了一些名为 SassScript 的新功能。 SassScript 可作用于任何属性，允许属性使用变量、算数运算等额外功能。

通过 interpolation，SassScript 甚至可以生成选择器或属性名，这一点对编写 mixin 有很大帮助。

### 6.1. Interactive Shell

Interactive Shell 可以在命令行中测试 SassScript 的功能。在命令行中输入 `sass -i`，然后输入想要测试的 SassScript 查看输出结果：

```
$ sass -i
>> "Hello, Sassy World!"
"Hello, Sassy World!"
>> 1px + 1px + 1px
3px
>> #777 + #777
#eeeeee
>> #777 + #888
white
```

### 6.2. 变量 `$` (Variables: `$`)

SassScript 最普遍的用法就是变量，变量以美元符号开头，赋值方法与 CSS 属性的写法一样：

```scss
$width: 5em;
```

直接使用即调用变量：

```css
#main {
  width: $width;
}
```

变量支持块级作用域，嵌套规则内定义的变量只能在嵌套规则内使用（局部变量），不在嵌套规则内定义的变量则可在任何地方使用（全局变量）。将局部变量转换为全局变量可以添加 `!global` 声明：

```scss
#main {
  $width: 5em !global;
  width: $width;
}

#sidebar {
  width: $width;
}
```

编译为

```css
#main {
  width: 5em;
}

#sidebar {
  width: 5em;
}
```

### 6.3. 数据类型 (Data Types)

SassScript 支持 6 种主要的数据类型：

- 数字，`1, 2, 13, 10px`
- 字符串，有引号字符串与无引号字符串，`"foo", 'bar', baz`
- 颜色，`blue, #04a3f9, rgba(255,0,0,0.5)`
- 布尔型，`true, false`
- 空值，`null`
- 数组 (list)，用空格或逗号作分隔符，`1.5em 1em 0 2em, Helvetica, Arial, sans-serif`
- maps, 相当于 JavaScript 的 object，`(key1: value1, key2: value2)`

SassScript 也支持其他 CSS 属性值，比如 Unicode 字符集，或 `!important` 声明。然而Sass 不会特殊对待这些属性值，一律视为无引号字符串。

#### 6.3.1. 字符串 (Strings)

SassScript 支持 CSS 的两种字符串类型：有引号字符串 (quoted strings)，如 `"Lucida Grande"` `'http://sass-lang.com'`；与无引号字符串 (unquoted strings)，如 `sans-serif` `bold`，在编译 CSS 文件时不会改变其类型。只有一种情况例外，使用 `#{}` (interpolation) 时，有引号字符串将被编译为无引号字符串，这样便于在 mixin 中引用选择器名：

```scss
@mixin firefox-message($selector) {
  body.firefox #{$selector}:before {
    content: "Hi, Firefox users!";
  }
}
@include firefox-message(".header");
```

编译为

```css
body.firefox .header:before {
  content: "Hi, Firefox users!"; }
```

#### 6.3.2. 数组 (Lists)

数组 (lists) 指 Sass 如何处理 CSS 中 `margin: 10px 15px 0 0` 或者 `font-face: Helvetica, Arial, sans-serif` 这样通过空格或者逗号分隔的一系列的值。事实上，独立的值也被视为数组 —— 只包含一个值的数组。

数组本身没有太多功能，但 [Sass list functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#list-functions) 赋予了数组更多新功能：`nth` 函数可以直接访问数组中的某一项；`join` 函数可以将多个数组连接在一起；`append` 函数可以在数组中添加新值；而 `@each` 指令能够遍历数组中的每一项。

数组中可以包含子数组，比如 `1px 2px, 5px 6px` 是包含 `1px 2px` 与 `5px 6px` 两个数组的数组。如果内外两层数组使用相同的分隔方式，需要用圆括号包裹内层，所以也可以写成 `(1px 2px) (5px 6px)`。变化是，之前的 `1px 2px, 5px 6px` 使用逗号分割了两个子数组 (comma-separated)，而 `(1px 2px) (5px 6px)` 则使用空格分割(space-separated)。

当数组被编译为 CSS 时，Sass 不会添加任何圆括号（CSS 中没有这种写法），所以 `(1px 2px) (5px 6px)` 与 `1px 2px, 5px 6px` 在编译后的 CSS 文件中是完全一样的，但是它们在 Sass 文件中却有不同的意义，前者是包含两个数组的数组，而后者是包含四个值的数组。

用 `()` 表示不包含任何值的空数组（在 Sass 3.3 版之后也视为空的 map）。空数组不可以直接编译成 CSS，比如编译 `font-family: ()` Sass 将会报错。如果数组中包含空数组或空值，编译时将被清除，比如 `1px 2px () 3px` 或 `1px 2px null 3px`。

基于逗号分隔的数组允许保留结尾的逗号，这样做的意义是强调数组的结构关系，尤其是需要声明只包含单个值的数组时。例如 `(1,)` 表示只包含 `1` 的数组，而 `(1 2 3,)` 表示包含 `1 2 3` 这个以空格分隔的数组的数组。

#### 6.3.3. Maps

Maps represent an association between keys and values, where keys are used to look up values. They make it easy to collect values into named groups and access those groups dynamically. They have no direct parallel in CSS, although they’re syntactically similar to media query expressions: 



#### 6.3.4. 颜色 (Colors)

Any CSS color expression returns a SassScript Color value. This includes a large number of named colors which are indistinguishable from unquoted strings. In compressed output mode, Sass will output the smallest CSS representation of a color. For example, #FF0000 will output as red in compressed mode, but blanchedalmond will output as #FFEBCD. A common issue users encounter with named colors is that since Sass prefers the same output format as was typed in other output modes, a color interpolated into a selector becomes invalid syntax when compressed. To avoid this, always quote named colors if they are meant to be used in the construction of a selector.

### 6.4. 运算 (Operations)

所有数据类型均支持相等运算  ，此外，每种数据类型也有其各自支持的运算方式。

SassScript 支持数字的加减乘除、取整等运算 (`+, -, *, /, %`)，如果必要会在不同单位间转换值。

```scss
p {
  width: 1in + 8pt;
}
```

编译为

```css
p {
  width: 1.111in; }
```

关系运算 `<, >, <=, >=` 也可用于数字运算，相等运算 `==, !=` 可用于所有数据类型。

##### 6.4.1.1. 除法运算 `/` (Division and `/`)

`/` 在 CSS 中通常起到分隔数字的用途，SassScript 作为 CSS 语言的拓展当然也支持这个功能，同时也赋予了 `/` 除法运算的功能。也就是说，如果 `/` 在 SassScript 中把两个数字分隔，编译后的 CSS 文件中也是同样的作用。

以下三种情况 `/` 将被视为除法运算符号：

- 如果值，或值的一部分，是变量或者函数的返回值
- 如果值被圆括号包裹
- 如果值是算数表达式的一部分

```scss
p {
  font: 10px/8px;             // Plain CSS, no division
  $width: 1000px;
  width: $width/2;            // Uses a variable, does division
  width: round(1.5)/2;        // Uses a function, does division
  height: (500px/2);          // Uses parentheses, does division
  margin-left: 5px + 8px/2px; // Uses +, does division
}
```

编译为

```css
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; }
```

如果需要使用变量，同时又要确保 `/` 不做除法运算而是完整地编译到 CSS 文件中，只需要用 `#{}` 插值语句将变量包裹。

```scss
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```

编译为

```css
p {
  font: 12px/30px; }
```

#### 6.4.2. 颜色值运算 (Color Operations)

颜色值的运算是分段计算进行的，也就是分别计算红色，绿色，以及蓝色的值：

```scss
p {
  color: #010203 + #040506;
}
```

计算 `01 + 04 = 05` `02 + 05 = 07` `03 + 06 = 09`，然后编译为

```css
p {
  color: #050709; }
```

使用 [color functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html) 比计算颜色值更方便一些。

数字与颜色值之间也可以进行算数运算，同样也是分段计算的，比如

```scss
p {
  color: #010203 * 2;
}
```

计算 `01 * 2 = 02` `02 * 2 = 04` `03 * 2 = 06`，然后编译为

```css
p {
  color: #020406; }
```

需要注意的是，如果颜色值包含 alpha channel（rgba 或 hsla 两种颜色值），必须拥有相等的 alpha 值才能进行运算，因为算术运算不会作用于 alpha 值。

```scss
p {
  color: rgba(255, 0, 0, 0.75) + rgba(0, 255, 0, 0.75);
}
```

编译为

```css
p {
  color: rgba(255, 255, 0, 0.75); }
```

颜色值的 alpha channel 可以通过 [opacify](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#opacify-instance_method) 或 [transparentize](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#transparentize-instance_method) 两个函数进行调整。

```scss
$translucent-red: rgba(255, 0, 0, 0.5);
p {
  color: opacify($translucent-red, 0.3);
  background-color: transparentize($translucent-red, 0.25);
}
```

编译为

```css
p {
  color: rgba(255, 0, 0, 0.8);
  background-color: rgba(255, 0, 0, 0.25); }
```

IE 滤镜要求所有的颜色值包含 alpha 层，而且格式必须固定 `#AABBCCDD`，使用 `ie_hex_str` 函数可以很容易地将颜色转化为 IE 滤镜要求的格式。

```scss
$translucent-red: rgba(255, 0, 0, 0.5);
$green: #00ff00;
div {
  filter: progid:DXImageTransform.Microsoft.gradient(enabled='false', startColorstr='#{ie-hex-str($green)}', endColorstr='#{ie-hex-str($translucent-red)}');
}
```

编译为

```css
div {
  filter: progid:DXImageTransform.Microsoft.gradient(enabled='false', startColorstr=#FF00FF00, endColorstr=#80FF0000);
}
```

#### 6.4.3. 字符串运算 (String Operations)

`+` 可用于连接字符串

```scss
p {
  cursor: e + -resize;
}
```

编译为

```css
p {
  cursor: e-resize; }
```

注意，如果有引号字符串（位于 `+` 左侧）连接无引号字符串，运算结果是有引号的，相反，无引号字符串（位于 `+` 左侧）连接有引号字符串，运算结果则没有引号。

```scss
p:before {
  content: "Foo " + Bar;
  font-family: sans- + "serif";
}
```

编译为

```css
p:before {
  content: "Foo Bar";
  font-family: sans-serif; }
```

运算表达式与其他值连用时，用空格做连接符：

```scss
p {
  margin: 3px + 4px auto;
}
```

编译为

```css
p {
  margin: 7px auto; }
```

在有引号的文本字符串中使用 `#{}` 插值语句可以添加动态的值：

```scss
p:before {
  content: "I ate #{5 + 10} pies!";
}
```

编译为

```css
p:before {
  content: "I ate 15 pies!"; }
```

空的值被视作插入了空字符串：

```scss
$value: null;
p:before {
  content: "I ate #{$value} pies!";
}
```

编译为

```css
p:before {
  content: "I ate pies!"; }
```

#### 6.4.4. 布尔运算 (Boolean Operations)

SassScript 支持布尔型的 `and` `or` 以及 `not` 运算。

#### 6.4.5. 数组运算 (List Operations)

数组不支持任何运算方式，只能使用 [list functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#list-functions) 控制。

### 6.5. 圆括号 (Parentheses)

圆括号可以用来影响运算的顺序：

```scss
p {
  width: 1em + (2em * 3);
}
```

编译为

```css
p {
  width: 7em; }
```

### 6.6. 函数 (Functions)

SassScript 定义了多种函数，有些甚至可以通过普通的 CSS 语句调用：

```scss
p {
  color: hsl(0, 100%, 50%);
}
```

编译为

```css
p {
  color: #ff0000; }
```

#### 6.6.1. 关键词参数 (Keyword Arguments)

Sass 函数允许使用关键词参数 (keyword arguments)，上面的例子也可以写成：

```scss
p {
  color: hsl($hue: 0, $saturation: 100%, $lightness: 50%);
}
```

虽然不够简明，但是阅读起来会更方便。关键词参数给函数提供了更灵活的接口，以及容易调用的参数。关键词参数可以打乱顺序使用，如果使用默认值也可以省缺，另外，参数名被视为变量名，下划线、短横线可以互换使用。

通过 [Sass::Script::Functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html) 查看完整的 Sass 函数列表，参数名，以及如何自定义函数。

### 6.7. 插值语句 `#{}` (Interpolation: `#{}`)

通过 `#{}` 插值语句可以在选择器或属性名中使用变量：

```scss
$name: foo;
$attr: border;
p.#{$name} {
  #{$attr}-color: blue;
}
```

编译为

```css
p.foo {
  border-color: blue; }
```

`#{}` 插值语句也可以在属性值中插入 SassScript，大多数情况下，这样可能还不如使用变量方便，但是使用 `#{}` 可以避免 Sass 运行运算表达式，直接编译 CSS。

```scss
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```

编译为

```css
p {
  font: 12px/30px; }
```

### 6.8. `&` in SassScript

Just like when it’s used in selectors, & in SassScript refers to the current parent selector. It’s a comma-separated list of space-separated lists. For example:

```scss
.foo.bar .baz.bang, .bip.qux {
  $selector: &;
}
```

The value of $selector is now ((".foo.bar" ".baz.bang"), ".bip.qux"). The compound selectors are quoted here to indicate that they’re strings, but in reality they would be unquoted. Even if the parent selector doesn’t contain a comma or a space, & will always have two levels of nesting, so it can be accessed consistently.

If there is no parent selector, the value of & will be null. This means you can use it in a mixin to detect whether a parent selector exists:

```scss
@mixin does-parent-exist {
  @if & {
    &:hover {
      color: red;
    }
  } @else {
    a {
      color: red;
    }
  }
}
```

### 6.9. 变量定义 `!default` (Variable Defaults: `!default`)

可以在变量的结尾添加 `!default` 给一个未通过 `!default` 声明赋值的变量赋值，此时，如果变量已经被赋值，不会再被重新赋值，但是如果变量还没有被赋值，则会被赋予新的值。

```scss
$content: "First content";
$content: "Second content?" !default;
$new_content: "First time reference" !default;

#main {
  content: $content;
  new-content: $new_content;
}
```

编译为

```css
#main {
  content: "First content";
  new-content: "First time reference"; }
```

变量是 null 空值时将视为未被 `!default` 赋值。

```scss
$content: null;
$content: "Non-null content" !default;

#main {
  content: $content;
}
```

编译为

```css
#main {
  content: "Non-null content"; }
```

## 7. @-Rules 与指令 (@-Rules and Directives)

Sass 支持所有的 CSS3 @-Rules，以及 Sass 特有的 “指令”（directives）。这一节会详细解释，更多资料请查看 [控制指令 (control directives)](https://www.sass.hk/docs/#8) 与 [混合指令 (mixin directives)](https://www.sass.hk/docs/#9) 两个部分。

### 7.1. @import

Sass 拓展了 `@import` 的功能，允许其导入 SCSS 或 Sass 文件。被导入的文件将合并编译到同一个 CSS 文件中，另外，被导入的文件中所包含的变量或者混合指令 (mixin) 都可以在导入的文件中使用。

Sass 在当前地址，或 Rack, Rails, Merb 的 Sass 文件地址寻找 Sass 文件，如果需要设定其他地址，可以用 `:load_paths` 选项，或者在命令行中输入 `--load-path` 命令。

通常，`@import` 寻找 Sass 文件并将其导入，但在以下情况下，`@import` 仅作为普通的 CSS 语句，不会导入任何 Sass 文件。

- 文件拓展名是 `.css`；
- 文件名以 `http://` 开头；
- 文件名是 `url()`；
- `@import` 包含 media queries。

如果不在上述情况内，文件的拓展名是 `.scss` 或 `.sass`，则导入成功。没有指定拓展名，Sass 将会试着寻找文件名相同，拓展名为 `.scss` 或 `.sass` 的文件并将其导入。

```scss
@import "foo.scss";
```

或

```scss
@import "foo";
```

都会导入文件 foo.scss，但是

```scss
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

编译为

```css
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

Sass 允许同时导入多个文件，例如同时导入 rounded-corners 与 text-shadow 两个文件：

```scss
@import "rounded-corners", "text-shadow";
```

导入文件也可以使用 `#{ }` 插值语句，但不是通过变量动态导入 Sass 文件，只能作用于 CSS 的 `url()` 导入方式：

```scss
$family: unquote("Droid+Sans");
@import url("http://fonts.googleapis.com/css?family=\#{$family}");
```

编译为

```css
@import url("http://fonts.googleapis.com/css?family=Droid+Sans");
```

#### 7.1.1. 分音 (Partials)

如果需要导入 SCSS 或者 Sass 文件，但又不希望将其编译为 CSS，只需要在文件名前添加下划线，这样会告诉 Sass 不要编译这些文件，但导入语句中却不需要添加下划线。

例如，将文件命名为 `_colors.scss`，便不会编译 `_colours.css` 文件。

```scss
@import "colors";
```

上面的例子，导入的其实是 `_colors.scss` 文件

注意，不可以同时存在添加下划线与未添加下划线的同名文件，添加下划线的文件将会被忽略。

#### 7.1.2. 嵌套 @import

大多数情况下，一般在文件的最外层（不在嵌套规则内）使用 `@import`，其实，也可以将 `@import` 嵌套进 CSS 样式或者 `@media` 中，与平时的用法效果相同，只是这样导入的样式只能出现在嵌套的层中。

假设 example.scss 文件包含以下样式：

```scss
.example {
  color: red;
}
```

然后导入到 `#main` 样式内

```scss
#main {
  @import "example";
}
```

将会被编译为

```css
#main .example {
  color: red;
}
```

> Directives that are only allowed at the base level of a document, like @mixin or @charset, are not allowed in files that are @imported in a nested context. 这一句不理解

不可以在混合指令 (mixin) 或控制指令 (control directives) 中嵌套 `@import`。

### 7.2. @media

Sass 中 `@media` 指令与 CSS 中用法一样，只是增加了一点额外的功能：允许其在 CSS 规则中嵌套。如果 `@media` 嵌套在 CSS 规则内，编译时，`@media` 将被编译到文件的最外层，包含嵌套的父选择器。这个功能让 `@media` 用起来更方便，不需要重复使用选择器，也不会打乱 CSS 的书写流程。

```scss
.sidebar {
  width: 300px;
  @media screen and (orientation: landscape) {
    width: 500px;
  }
}
```

编译为

```css
.sidebar {
  width: 300px; }
  @media screen and (orientation: landscape) {
    .sidebar {
      width: 500px; } }
@media` 的 queries 允许互相嵌套使用，编译时，Sass 自动添加 `and
@media screen {
  .sidebar {
    @media (orientation: landscape) {
      width: 500px;
    }
  }
}
```

编译为

```css
@media screen and (orientation: landscape) {
  .sidebar {
    width: 500px; } }
```

`@media` 甚至可以使用 SassScript（比如变量，函数，以及运算符）代替条件的名称或者值：

```scss
$media: screen;
$feature: -webkit-min-device-pixel-ratio;
$value: 1.5;

@media #{$media} and ($feature: $value) {
  .sidebar {
    width: 500px;
  }
}
```

编译为

```css
@media screen and (-webkit-min-device-pixel-ratio: 1.5) {
  .sidebar {
    width: 500px; } }
```

### 7.3. @extend

在设计网页的时候常常遇到这种情况：一个元素使用的样式与另一个元素完全相同，但又添加了额外的样式。通常会在 HTML 中给元素定义两个 class，一个通用样式，一个特殊样式。假设现在要设计一个普通错误样式与一个严重错误样式，一般会这样写：

```markup
<div class="error seriousError">
  Oh no! You've been hacked!
</div>
```

样式如下

```css
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  border-width: 3px;
}
```

麻烦的是，这样做必须时刻记住使用 `.seriousError` 时需要参考 `.error` 的样式，带来了很多不变：智能比如加重维护负担，导致 bug，或者给 HTML 添加无语意的样式。使用 `@extend` 可以避免上述情况，告诉 Sass 将一个选择器下的所有样式继承给另一个选择器。

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

上面代码的意思是将 `.error` 下的所有样式继承给 `.seriousError`，`border-width: 3px;` 是单独给 `.seriousError` 设定特殊样式，这样，使用 `.seriousError` 的地方可以不再使用 `.error`。

其他使用到 `.error` 的样式也会同样继承给 `.seriousError`，例如，另一个样式 `.error.intrusion` 使用了 `hacked.png` 做背景，`` 也同样会使用 `hacked.png` 背景。

```css
.error.intrusion {
  background-image: url("/image/hacked.png");
}
```

#### 7.3.1. How it Works

`@extend` 的作用是将重复使用的样式 (`.error`) 延伸 (extend) 给需要包含这个样式的特殊样式（`.seriousError`），刚刚的例子：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.error.intrusion {
  background-image: url("/image/hacked.png");
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

编译为

```css
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd; }

.error.intrusion, .seriousError.intrusion {
  background-image: url("/image/hacked.png"); }

.seriousError {
  border-width: 3px; }
```

当合并选择器时，`@extend` 会很聪明地避免无谓的重复，`.seriousError.seriousError` 将编译为 `.seriousError`，不能匹配任何元素的选择器（比如 `#main#footer` ）也会删除。

#### 7.3.2. 延伸复杂的选择器 (Extending Complex Selectors)

Class 选择器并不是唯一可以被延伸 (extend) 的，Sass 允许延伸任何定义给单个元素的选择器，比如 `.special.cool`，`a:hover` 或者 `a.user[href^="http://"]` 等，例如：

```scss
.hoverlink {
  @extend a:hover;
}
```

同 class 元素一样，`a:hover` 的样式将继承给 `.hoverlink`。

```scss
.hoverlink {
  @extend a:hover;
}
a:hover {
  text-decoration: underline;
}
```

编译为

```css
a:hover, .hoverlink {
  text-decoration: underline; }
```

与上面 `.error.intrusion` 的例子一样，所有 `a:hover` 的样式将继承给 `.hoverlink`，包括其他使用到 `a:hover` 的样式，例如：

```scss
.hoverlink {
  @extend a:hover;
}
.comment a.user:hover {
  font-weight: bold;
}
```

编译为

```css
.comment a.user:hover, .comment .user.hoverlink {
  font-weight: bold; }
```

#### 7.3.3. 多重延伸 (Multiple Extends)

同一个选择器可以延伸给多个选择器，它所包含的属性将继承给所有被延伸的选择器：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.attention {
  font-size: 3em;
  background-color: #ff0;
}
.seriousError {
  @extend .error;
  @extend .attention;
  border-width: 3px;
}
```

编译为

```css
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd; }

.attention, .seriousError {
  font-size: 3em;
  background-color: #ff0; }

.seriousError {
  border-width: 3px; }
```

每个 `.seriousError` 将包含 `.error` 与 `.attention` 下的所有样式，这时，后定义的样式享有优先权：`.seriousError` 的背景颜色是 `#ff0` 而不是 `#fdd`，因为 `.attention` 在 `.error` 之后定义。

多重延伸可以使用逗号分隔选择器名，比如 `@extend .error, .attention;` 与 `@extend .error;` `@extend.attention` 有相同的效果。

#### 7.3.4. 继续延伸 (Chaining Extends)

当一个选择器延伸给第二个后，可以继续将第二个选择器延伸给第三个，例如：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
.criticalError {
  @extend .seriousError;
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%;
}
```

现在，每个 `.seriousError` 选择器将包含 `.error` 的样式，而 `.criticalError` 不仅包含 `.seriousError` 的样式也会同时包含 `.error` 的所有样式，上面的代码编译为：

```css
.error, .seriousError, .criticalError {
  border: 1px #f00;
  background-color: #fdd; }

.seriousError, .criticalError {
  border-width: 3px; }

.criticalError {
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%; }
```

#### 7.3.5. 选择器列 (Selector Sequences)

暂时不可以将选择器列 (Selector Sequences)，比如 `.foo .bar` 或 `.foo + .bar`，延伸给其他元素，但是，却可以将其他元素延伸给选择器列：

```scss
#fake-links .link {
  @extend a;
}

a {
  color: blue;
  &:hover {
    text-decoration: underline;
  }
}
```

编译为

```css
a, #fake-links .link {
  color: blue; }
  a:hover, #fake-links .link:hover {
    text-decoration: underline; }
```

##### 7.3.5.1. 合并选择器列 (Merging Selector Sequences)

有时会遇到复杂的情况，比如选择器列中的某个元素需要延伸给另一个选择器列，这种情况下，两个选择器列需要合并，比如：

```scss
#admin .tabbar a {
  font-weight: bold;
}
#demo .overview .fakelink {
  @extend a;
}
```

技术上讲能够生成所有匹配条件的结果，但是这样生成的样式表太复杂了，上面这个简单的例子就可能有 10 种结果。所以，Sass 只会编译输出有用的选择器。

当两个列 (sequence) 合并时，如果没有包含相同的选择器，将生成两个新选择器：第一列出现在第二列之前，或者第二列出现在第一列之前：

```scss
#admin .tabbar a {
  font-weight: bold;
}
#demo .overview .fakelink {
  @extend a;
}
```

编译为

```css
#admin .tabbar a,
#admin .tabbar #demo .overview .fakelink,
#demo .overview #admin .tabbar .fakelink {
  font-weight: bold; }
```

如果两个列 (sequence) 包含了相同的选择器，相同部分将会合并在一起，其他部分交替输出。在下面的例子里，两个列都包含 `#admin`，输出结果中它们合并在了一起：

```scss
#admin .tabbar a {
  font-weight: bold;
}
#admin .overview .fakelink {
  @extend a;
}
```

编译为

```css
#admin .tabbar a,
#admin .tabbar .overview .fakelink,
#admin .overview .tabbar .fakelink {
  font-weight: bold; }
```

#### 7.3.6. @extend-Only 选择器 (@extend-Only Selectors)

有时，需要定义一套样式并不是给某个元素用，而是只通过 `@extend` 指令使用，尤其是在制作 Sass 样式库的时候，希望 Sass 能够忽略用不到的样式。

如果使用普通的 CSS 规则，最后会编译出很多用不到的样式，也容易与其他样式名冲突，所以，Sass 引入了“占位符选择器” (placeholder selectors)，看起来很像普通的 `id` 或 `class` 选择器，只是 `#` 或 `.` 被替换成了 `%`。可以像 class 或者 id 选择器那样使用，当它们单独使用时，不会被编译到 CSS 文件中。

```scss
// This ruleset won't be rendered on its own.
#context a%extreme {
  color: blue;
  font-weight: bold;
  font-size: 2em;
}
```

占位符选择器需要通过延伸指令使用，用法与 class 或者 id 选择器一样，被延伸后，占位符选择器本身不会被编译。

```scss
.notice {
  @extend %extreme;
}
```

编译为

```css
#context a.notice {
  color: blue;
  font-weight: bold;
  font-size: 2em; }
```

#### 7.3.7. `!optional` 声明 (The `!optional` Flag)

如果 `@extend` 失败会收到错误提示，比如，这样写 `a.important {@extend .notice}`，当没有 `.notice` 选择器时，将会报错，只有 `h1.notice` 包含 `.notice` 时也会报错，因为 `h1` 与 `a` 冲突，会生成新的选择器。

如果要求 `@extend` 不生成新选择器，可以通过 `!optional` 声明达到这个目的，例如：

```scss
a.important {
  @extend .notice !optional;
}
```

#### 7.3.8. 在指令中延伸 (@extend in Directives)

在指令中使用 `@extend` 时（比如在 `@media` 中）有一些限制：Sass 不可以将 `@media` 层外的 CSS 规则延伸给指令层内的 CSS，这样会生成大量的无用代码。也就是说，如果在 `@media` （或者其他 CSS 指令）中使用 `@extend`，必须延伸给相同指令层中的选择器。

下面的例子是可行的：

```scss
@media print {
  .error {
    border: 1px #f00;
    background-color: #fdd;
  }
  .seriousError {
    @extend .error;
    border-width: 3px;
  }
}
```

但不可以这样：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}

@media print {
  .seriousError {
    // INVALID EXTEND: .error is used outside of the "@media print" directive
    @extend .error;
    border-width: 3px;
  }
}
```

希望有一天，浏览器可以原生支持 `@extend` 指令，这样就可以在任何指令中使用延伸功能，不再受限制了。

### 7.4. @at-root

The @at-root directive causes one or more rules to be emitted at the root of the document, rather than being nested beneath their parent selectors. It can either be used with a single inline selector:

```scss
.parent {
  ...
  @at-root .child { ... }
}
```

Which would produce:

```css
.parent { ... }
.child { ... }
```

Or it can be used with a block containing multiple selectors:

```scss
.parent {
  ...
  @at-root {
    .child1 { ... }
    .child2 { ... }
  }
  .step-child { ... }
}
```

Which would output the following:

```css
.parent { ... }
.child1 { ... }
.child2 { ... }
.parent .step-child { ... }
```

#### 7.4.1. @at-root (without: ...) and @at-root (with: ...)

By default, @at-root just excludes selectors. However, it’s also possible to use @at-root to move outside of nested directives such as @media as well. For example:

```scss
@media print {
  .page {
    width: 8in;
    @at-root (without: media) {
      color: red;
    }
  }
}
```

produces:

```css
@media print {
  .page {
    width: 8in;
  }
}
.page {
  color: red;
}
```

You can use @at-root (without: ...) to move outside of any directive. You can also do it with multiple directives separated by a space: @at-root (without: media supports) moves outside of both @media and @supports queries.

There are two special values you can pass to @at-root. “rule” refers to normal CSS rules; @at-root (without: rule) is the same as @at-root with no query. @at-root (without: all) means that the styles should be moved outside of all directives and CSS rules.

If you want to specify which directives or rules to include, rather than listing which ones should be excluded, you can use with instead of without. For example, @at-root (with: rule) will move outside of all directives, but will preserve any CSS rules.

### 7.5. @debug

The @debug directive prints the value of a SassScript expression to the standard error output stream. It’s useful for debugging Sass files that have complicated SassScript going on. For example:

```scss
@debug 10em + 12em;
```

编译为

```
Line 1 DEBUG: 22em
```

### 7.6. @warn

The @warn directive prints the value of a SassScript expression to the standard error output stream. It’s useful for libraries that need to warn users of deprecations or recovering from minor mixin usage mistakes. There are two major distinctions between @warn and @debug:

1. You can turn warnings off with the --quiet command-line option or the :quiet Sass option.
2. A stylesheet trace will be printed out along with the message so that the user being warned can see where their styles caused the warning.

Usage Example:

```scss
@mixin adjust-location($x, $y) {
  @if unitless($x) {
    @warn "Assuming #{$x} to be in pixels";
    $x: 1px * $x;
  }
  @if unitless($y) {
    @warn "Assuming #{$y} to be in pixels";
    $y: 1px * $y;
  }
  position: relative; left: $x; top: $y;
}
```

### 7.7. @warn

The @error directive throws the value of a SassScript expression as a fatal error, including a nice stack trace. It’s useful for validating arguments to mixins and functions. For example:

```scss
@mixin adjust-location($x, $y) {
  @if unitless($x) {
    @error "$x may not be unitless, was #{$x}.";
  }
  @if unitless($y) {
    @error "$y may not be unitless, was #{$y}.";
  }
  position: relative; left: $x; top: $y;
}
```

There is currently no way to catch errors.

## 8. 控制指令 (Control Directives)

SassScript 提供了一些基础的控制指令，比如在满足一定条件时引用样式，或者设定范围重复输出格式。控制指令是一种高级功能，日常编写过程中并不常用到，主要与混合指令 (mixin) 配合使用，尤其是用在 [Compass](http://compass-style.org/) 等样式库中。

### 8.1. if()

The built-in if() function allows you to branch on a condition and returns only one of two possible outcomes. It can be used in any script context. The if function only evaluates the argument corresponding to the one that it will return – this allows you to refer to variables that may not be defined or to have calculations that would otherwise cause an error (E.g. divide by zero).

### 8.2. @if

当 `@if` 的表达式返回值不是 `false` 或者 `null` 时，条件成立，输出 `{}` 内的代码：

```scss
p {
  @if 1 + 1 == 2 { border: 1px solid; }
  @if 5 < 3 { border: 2px dotted; }
  @if null  { border: 3px double; }
}
```

编译为

```css
p {
  border: 1px solid; }
```

`@if` 声明后面可以跟多个 `@else if` 声明，或者一个 `@else` 声明。如果 `@if` 声明失败，Sass 将逐条执行 `@else if` 声明，如果全部失败，最后执行 `@else` 声明，例如：

```scss
$type: monster;
p {
  @if $type == ocean {
    color: blue;
  } @else if $type == matador {
    color: red;
  } @else if $type == monster {
    color: green;
  } @else {
    color: black;
  }
}
```

编译为

```css
p {
  color: green; }
```

### 8.3. @for

`@for` 指令可以在限制的范围内重复输出格式，每次按要求（变量的值）对输出结果做出变动。这个指令包含两种格式：`@for $var from  through `，或者 `@for $var from  to `，区别在于 `through` 与 `to` 的含义：*当使用 `through` 时，条件范围包含 `` 与 `` 的值，而使用 `to` 时条件范围只包含 `` 的值不包含 `` 的值*。另外，`$var` 可以是任何变量，比如 `$i`；`` 和 `` 必须是整数值。

```scss
@for $i from 1 through 3 {
  .item-#{$i} { width: 2em * $i; }
}
```

编译为

```css
.item-1 {
  width: 2em; }
.item-2 {
  width: 4em; }
.item-3 {
  width: 6em; }
```

### 8.4. @each

`@each` 指令的格式是 `$var in `, `$var` 可以是任何变量名，比如 `$length` 或者 `$name`，而 `` 是一连串的值，也就是值列表。

`@each` 将变量 `$var` 作用于值列表中的每一个项目，然后输出结果，例如：

```scss
@each $animal in puma, sea-slug, egret, salamander {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}
```

编译为

```css
.puma-icon {
  background-image: url('/images/puma.png'); }
.sea-slug-icon {
  background-image: url('/images/sea-slug.png'); }
.egret-icon {
  background-image: url('/images/egret.png'); }
.salamander-icon {
  background-image: url('/images/salamander.png'); }
```

#### 8.4.1 Multiple Assignment

The @each directive can also use multiple variables, as in @each $var1, $var2, ... in . If is a list of lists, each element of the sub-lists is assigned to the respective variable. For example:

```scss
@each $animal, $color, $cursor in (puma, black, default),
                                  (sea-slug, blue, pointer),
                                  (egret, white, move) {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
    border: 2px solid $color;
    cursor: $cursor;
  }
}
```

is compiled to:

```css
.puma-icon {
  background-image: url('/images/puma.png');
  border: 2px solid black;
  cursor: default; }
.sea-slug-icon {
  background-image: url('/images/sea-slug.png');
  border: 2px solid blue;
  cursor: pointer; }
.egret-icon {
  background-image: url('/images/egret.png');
  border: 2px solid white;
  cursor: move; }
```

Since maps are treated as lists of pairs, multiple assignment works with them as well. For example:

```scss
@each $header, $size in (h1: 2em, h2: 1.5em, h3: 1.2em) {
  #{$header} {
    font-size: $size;
  }
}
```

is compiled to:

```css
h1 {
  font-size: 2em; }
h2 {
  font-size: 1.5em; }
h3 {
  font-size: 1.2em; }
```

### 8.5. @while

`@while` 指令重复输出格式直到表达式返回结果为 `false`。这样可以实现比 `@for` 更复杂的循环，只是很少会用到。例如：

```scss
$i: 6;
@while $i > 0 {
  .item-#{$i} { width: 2em * $i; }
  $i: $i - 2;
}
.item-6 {
  width: 12em; }

.item-4 {
  width: 8em; }

.item-2 {
  width: 4em; }
```

## 9. 混合指令 (Mixin Directives)

混合指令（Mixin）用于定义可重复使用的样式，避免了使用无语意的 class，比如 `.float-left`。混合指令可以包含所有的 CSS 规则，绝大部分 Sass 规则，甚至通过参数功能引入变量，输出多样化的样式。

### 9.1. 定义混合指令 `@mixin` (Defining a Mixin: `@mixin`)

混合指令的用法是在 `@mixin` 后添加名称与样式，比如名为 `large-text` 的混合通过下面的代码定义：

```scss
@mixin large-text {
  font: {
    family: Arial;
    size: 20px;
    weight: bold;
  }
  color: #ff0000;
}
```

混合也需要包含选择器和属性，甚至可以用 `&` 引用父选择器：

```scss
@mixin clearfix {
  display: inline-block;
  &:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
  }
  * html & { height: 1px }
}
```

### 9.2. 引用混合样式 `@include` (Including a Mixin: `@include`)

使用 `@include` 指令引用混合样式，格式是在其后添加混合名称，以及需要的参数（可选）：

```scss
.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}
```

编译为

```css
.page-title {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: #ff0000;
  padding: 4px;
  margin-top: 10px; }
```

也可以在最外层引用混合样式，不会直接定义属性，也不可以使用父选择器。

```scss
@mixin silly-links {
  a {
    color: blue;
    background-color: red;
  }
}
@include silly-links;
```

编译为

```css
a {
  color: blue;
  background-color: red; }
```

混合样式中也可以包含其他混合样式，比如

```scss
@mixin compound {
  @include highlighted-background;
  @include header-text;
}
@mixin highlighted-background { background-color: #fc0; }
@mixin header-text { font-size: 20px; }
```

混合样式中应该只定义后代选择器，这样可以安全的导入到文件的任何位置。

### 9.3. 参数 (Arguments)

参数用于给混合指令中的样式设定变量，并且赋值使用。在定义混合指令的时候，按照变量的格式，通过逗号分隔，将参数写进圆括号里。引用指令时，按照参数的顺序，再将所赋的值对应写进括号：

```scss
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue, 1in); }
```

编译为

```css
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }
```

混合指令也可以使用给变量赋值的方法给参数设定默认值，然后，当这个指令被引用的时候，如果没有给参数赋值，则自动使用默认值：

```scss
@mixin sexy-border($color, $width: 1in) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue); }
h1 { @include sexy-border(blue, 2in); }
```

编译为

```css
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }

h1 {
  border-color: blue;
  border-width: 2in;
  border-style: dashed; }
```

#### 9.3.1. 关键词参数 (Keyword Arguments)

混合指令也可以使用关键词参数，上面的例子也可以写成：

```scss
p { @include sexy-border($color: blue); }
h1 { @include sexy-border($color: blue, $width: 2in); }
```

虽然不够简明，但是阅读起来会更方便。关键词参数给函数提供了更灵活的接口，以及容易调用的参数。关键词参数可以打乱顺序使用，如果使用默认值也可以省缺，另外，参数名被视为变量名，下划线、短横线可以互换使用。

#### 9.3.2. 参数变量 (Variable Arguments)

有时，不能确定混合指令需要使用多少个参数，比如一个关于 `box-shadow` 的混合指令不能确定有多少个 'shadow' 会被用到。这时，可以使用参数变量 `…` 声明（写在参数的最后方）告诉 Sass 将这些参数视为值列表处理：

```scss
@mixin box-shadow($shadows...) {
  -moz-box-shadow: $shadows;
  -webkit-box-shadow: $shadows;
  box-shadow: $shadows;
}
.shadows {
  @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999);
}
```

编译为

```css
.shadowed {
  -moz-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  -webkit-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
}
```

参数变量也可以用在引用混合指令的时候 (`@include`)，与平时用法一样，将一串值列表中的值逐条作为参数引用：

```scss
@mixin colors($text, $background, $border) {
  color: $text;
  background-color: $background;
  border-color: $border;
}
$values: #ff0000, #00ff00, #0000ff;
.primary {
  @include colors($values...);
}
```

编译为

```css
.primary {
  color: #ff0000;
  background-color: #00ff00;
  border-color: #0000ff;
}
```

> You can use variable arguments to wrap a mixin and add additional styles without changing the argument signature of the mixin. If you do so, even keyword arguments will get passed through to the wrapped mixin. For example:

```scss
@mixin wrapped-stylish-mixin($args...) {
  font-weight: bold;[![img](https://www.sass.hk/images/hengfu.jpg)￼
  @include stylish-mixin($args...);
}
.stylish {
  // The $width argument will get passed on to "stylish-mixin" as a keyword
  @include wrapped-stylish-mixin(#00ff00, $width: 100px);
}
```

上面注释内的意思是：`$width` 参数将会传递给 `stylish-mixin` 作为关键词。

### 9.4. 向混合样式中导入内容 (Passing Content Blocks to a Mixin)

在引用混合样式的时候，可以先将一段代码导入到混合指令中，然后再输出混合样式，额外导入的部分将出现在 `@content` 标志的地方：

```scss
@mixin apply-to-ie6-only {
  * html {
    @content;
  }
}
@include apply-to-ie6-only {
  #logo {
    background-image: url(/logo.gif);
  }
}
```

编译为

```css
* html #logo {
  background-image: url(/logo.gif);
}
```

**为便于书写，`@mixin` 可以用 `=` 表示，而 `@include` 可以用 `+` 表示**，所以上面的例子可以写成：

```sass
=apply-to-ie6-only
  * html
    @content

+apply-to-ie6-only
  #logo
    background-image: url(/logo.gif)
```

**注意：** 当 `@content` 在指令中出现过多次或者出现在循环中时，额外的代码将被导入到每一个地方。

#### 9.4.1. Variable Scope and Content Blocks

> The block of content passed to a mixin are evaluated in the scope where the block is defined, not in the scope of the mixin. This means that variables local to the mixin cannot be used within the passed style block and variables will resolve to the global value:

```scss
$color: white;
@mixin colors($color: blue) {
  background-color: $color;
  @content;
  border-color: $color;
}
.colors {
  @include colors { color: $color; }
}
```

编译为

```css
.colors {
  background-color: blue;
  color: white;
  border-color: blue;
}
```

> Additionally, this makes it clear that the variables and mixins that are used within the passed block are related to the other styles around where the block is defined. For example:

```scss
#sidebar {
  $sidebar-width: 300px;
  width: $sidebar-width;
  @include smartphone {
    width: $sidebar-width / 3;
  }
}
```

## 10. 函数指令 (Function Directives)

Sass 支持自定义函数，并能在任何属性值或 Sass script 中使用：

```scss
$grid-width: 40px;
$gutter-width: 10px;

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { width: grid-width(5); }
```

编译为

```css
#sidebar {
  width: 240px; }
```

与 mixin 相同，也可以传递若干个全局变量给函数作为参数。一个函数可以含有多条语句，需要调用 `@return` 输出结果。

自定义的函数也可以使用关键词参数，上面的例子还可以这样写：

```scss
#sidebar { width: grid-width($n: 5); }
```

建议在自定义函数前添加前缀避免命名冲突，其他人阅读代码时也会知道这不是 Sass 或者 CSS 的自带功能。

自定义函数与 mixin 相同，都支持 variable arguments

## 11. 输出格式 (Output Style)

Sass 默认的 CSS 输出格式很美观也能清晰反映文档结构，为满足其他需求 Sass 也提供了多种输出格式。

Sass 提供了四种输出格式，可以通过 `:style option` 选项设定，或者在命令行中使用 `--style` 选项。

### 11.1. `:nested`

Nested （嵌套）样式是 Sass 默认的输出格式，能够清晰反映 CSS 与 HTML 的结构关系。选择器与属性等单独占用一行，缩进量与 Sass 文件中一致，每行的缩进量反映了其在嵌套规则内的层数。当阅读大型 CSS 文件时，这种样式可以很容易地分析文件的主要结构。

```css
#main {
  color: #fff;
  background-color: #000; }
  #main p {
    width: 10em; }

.huge {
  font-size: 10em;
  font-weight: bold;
  text-decoration: underline; }
```

### 11.2. `:expanded`

Expanded 输出更像是手写的样式，选择器、属性等各占用一行，属性根据选择器缩进，而选择器不做任何缩进。

```css
#main {
  color: #fff;
  background-color: #000;
}
#main p {
  width: 10em;
}

.huge {
  font-size: 10em;
  font-weight: bold;
  text-decoration: underline;
}
```

### 11.3. `:compact`

Compact 输出方式比起上面两种占用的空间更少，每条 CSS 规则只占一行，包含其下的所有属性。嵌套过的选择器在输出时没有空行，不嵌套的选择器会输出空白行作为分隔符。

```css
#main { color: #fff; background-color: #000; }
#main p { width: 10em; }

.huge { font-size: 10em; font-weight: bold; text-decoration: underline; }
```

### 11.4. `:compressed`

Compressed 输出方式删除所有无意义的空格、空白行、以及注释，力求将文件体积压缩到最小，同时也会做出其他调整，比如会自动替换占用空间最小的颜色表达方式。

```css
#main{color:#fff;background-color:#000}#main p{width:10em}.huge{font-size:10em;font-weight:bold;text-decoration:underline}
```

## 12. 拓展 Sass (Extending Sass)

Sass 提供了很多高级自定义功能，使用这些功能需要有良好的 Ruby 基础。

### 12.1. 自定义 Sass 函数 (Defining Custom Sass Functions)

通过 Ruby API 可以自定义 Sass 函数，具体请查看 [source documentation](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#adding_custom_functions)。

### 12.2. 存储缓存 (Cache Stores)

Sass caches parsed documents so that they can be reused without parsing them again unless they have changed. By default, Sass will write these cache files to a location on the filesystem indicated by :cache_location. If you cannot write to the filesystem or need to share cache across ruby processes or machines, then you can define your own cache store and set the:cache_store option. For details on creating your own cache store, please see the source documentation.

### 12.3. 自定义导入 (Custom Importers)

Sass importers are in charge of taking paths passed to @import and finding the appropriate Sass code for those paths. By default, this code is loaded from the filesystem, but importers could be added to load from a database, over HTTP, or use a different file naming scheme than what Sass expects.

Each importer is in charge of a single load path (or whatever the corresponding notion is for the backend). Importers can be placed in the :load_paths array alongside normal filesystem paths.

When resolving an @import, Sass will go through the load paths looking for an importer that successfully imports the path. Once one is found, the imported file is used.

User-created importers must inherit from Sass::Importers::Base.

