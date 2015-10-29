<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# CSS 书写规范

## CSS编码总体原则

* 从外部文件加载CSS，尽可能减少文件数。加载标签必须放在文件的 HEAD 部分。

* 用 LINK 标签加载，永远不要用@import。

* 使用[normalize.css](http://necolas.github.com/normalize.css/)让渲染效果在不同浏览器中更一致。

* 使用类似[YUI fonts.css](http://developer.yahoo.com/yui/fonts/) 的字体规格化文件。

* 定义样式的时候，对样式在页面只出现一次的元素用id，其他的用class,(尽可能用class)

* 不允许有`空的规则`；

* 去掉数字中不必要的`小数点`和末尾的0, 属性值'0'后面不要加`单位`；

* 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

* 不要在一个文件里出现两个相同的规则；

* 用 `border: 0;` 代替 border: none;；







## 缩进

* 使用soft tab（4个空格）。

* 子级DOM结构可整体缩进提高可读性。

* 同个属性不同前缀的写法需要在`垂直方向保持对齐`，具体参照下边的写法；

* `无前缀`的标准属性应该写在有前缀的属性`后面`；

```css
    /* good */
    .element {
    position: absolute;
    top: 10px;
    left: 10px;
    }
        .sub-element {
        border-radius: 10px;
        width: 50px;
        height: 50px;
        }
    
    
     /* not good */
    .element {
        height:0px;
        width: 50.0px;
        color: rgba(0, 0, 0, 0.5);
        
        border-radius: 3px;
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;
    
        background: linear-gradient(to bottom, #fff 0, #eee 100%);
        background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
        background: -moz-linear-gradient(top, #fff 0, #eee 100%);
    }
    
    /* good */
    .element {
        height:0;
        width: 50px;
        color: rgba(0, 0, 0, .5);
        
        -webkit-border-radius: 3px;
           -moz-border-radius: 3px;
                border-radius: 3px;
    
        background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
        background:    -moz-linear-gradient(top, #fff 0, #eee 100%);
        background:         linear-gradient(to bottom, #fff 0, #eee 100%);
    }
    
```

## 空格与换行

以下几种情况不需要空格：

* 属性名后
* 多个规则的分隔符','前
* !important '!'后
* 属性值中'('后和')'前
* 行末不要有多余的空格

以下几种情况需要`空格`：

* 属性值前
* 选择器'>', '+', '~'前后
* '{'前
* !important '!'前
* 属性值中的','后
* 注释'/\*'后和'\*/'前

以下几种情况需要`换行`：

* '{'后和'}'前
* 每个属性独占一行
* 多个规则的分隔符','后

```css
    /* not good */
    .element>.dialog ,
    .dialog{
        color :red! important;
        background-color: rgba(0,0,0,.5);
    }
    
    /* good */
    .element > .dialog,
    .dialog {
        color :red !important;
        background-color: rgba(0, 0, 0, .5);
    }
    
```

## 空行

以下几种情况需要空行：

* 文件最后保留一个空行
* '}'后最好跟一个空行，包括scss中嵌套的规则
* 属性之间需要适当的空行，具体见属性声明顺序

```less
    /* not good */
    .element {
        border-radius: 10px;
    }
    .dialog {
        color: red;
        &:after {
            border-radius: 10px;
        }
    }
    
    /* good */
    .element {
        border-radius: 10px;
    }
    
    .dialog {
        color: red;
    
        &:after {
            border-radius: 10px;
        }
    }
```

## 注释

* 注释统一用'/\* \*/'（less中也不要用'//'），具体参照下边的写法；

* 缩进与`下一行代码`保持一致；

* 可位于一个代码行的`末尾`，与代码间隔一个`空格`。


```css
    /* Modal header */
    .modal-header {
        color:black;
    }
    
    /*
     * Modal header
     */
    .modal-header {
        color:black;
    }
    
    .modal-header {
        /* 50px */
        width: 50px;
    
        color: red; /* color red */
    }
```

## 引号

* 最外层统一使用双引号；

* url的内容要用引号；

* 属性选择器中的属性值需要引号。

```css
    .element:after {
        content: "";
        background-image: url("logo.png");
    }
    
    li[data-type="single"] {
        color:red;
    }
```

##属性简写

属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；

margin 和 padding 相反，需要使用简写；

常见的属性简写包括：

* font
* background
* transition
* animation

```css
    /* not good */
    .element {
        transition: opacity 1s linear 2s;
    }
    
    /* good */
    .element {
        transition-delay: 2s;
        transition-timing-function: linear;
        transition-duration: 1s;
        transition-property: opacity;
    }
```

## 媒体查询

尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

```css
    .element {
        width:1200px
    }
    
    .element-avatar{
        width:1200px
    }
    
    @media (min-width: 480px) {
        .element {
            width:480px;
        }
    
        .element-avatar {
            width:480px;
        }
    }
```

## 高效选择器 
> [参考文章-编写高效CSS](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Writing_efficient_CSS)

四种关键选择器

1. ID 规则
2. Class 规则
3. 标签规则
4. 通用规则

匹配规则：(从右到左边)

样式系统从关键选择器开始匹配规则，然后左移(查找规则选择器的任何祖先元素)。

只要选择器的子树(substree)一直在检查，样式系统就会持续左移，直到和规则匹配，或者是因为不匹配而放弃。

高性能匹配关键：对于一个给定的元素，需要匹配的规则越少，样式的解析就会越快。

高效CSS指南:

* 避免通配`'*'选择器`;

* 不要叠加限定条件到 ID 选择器（`div#myid`)或 class 选择器(`table.results`)

* 尽量避免后代选择器(后代选择器是 CSS 中耗费最昂贵的);  

* 依赖继承;



## 属性声明顺序

相关的属性声明按下边的顺序做分组处理，组之间需要有一个空行。



```css
    .declaration-order {
        display: block;
        float: right;
    
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        z-index: 100;
    
        border: 1px solid #e5e5e5;
        border-radius: 3px;
        width: 100px;
        height: 100px;
    
        font: normal 13px "Helvetica Neue", sans-serif;
        line-height: 1.5;
        text-align: center;
    
        color: #333;
        background-color: #f5f5f5;
    
        opacity: 1;
    }
```

```css
// 下面是推荐的属性的顺序
[
    [
        "display",
        "visibility",
        "float",
        "clear",
        "overflow",
        "overflow-x",
        "overflow-y",
        "clip",
        "zoom"
    ],
    [
        "table-layout",
        "empty-cells",
        "caption-side",
        "border-spacing",
        "border-collapse",
        "list-style",
        "list-style-position",
        "list-style-type",
        "list-style-image"
    ],
    [
        "-webkit-box-orient",
        "-webkit-box-direction",
        "-webkit-box-decoration-break",
        "-webkit-box-pack",
        "-webkit-box-align",
        "-webkit-box-flex"
    ],
    [
        "position",
        "top",
        "right",
        "bottom",
        "left",
        "z-index"
    ],
    [
        "margin",
        "margin-top",
        "margin-right",
        "margin-bottom",
        "margin-left",
        "-webkit-box-sizing",
        "-moz-box-sizing",
        "box-sizing",
        "border",
        "border-width",
        "border-style",
        "border-color",
        "border-top",
        "border-top-width",
        "border-top-style",
        "border-top-color",
        "border-right",
        "border-right-width",
        "border-right-style",
        "border-right-color",
        "border-bottom",
        "border-bottom-width",
        "border-bottom-style",
        "border-bottom-color",
        "border-left",
        "border-left-width",
        "border-left-style",
        "border-left-color",
        "-webkit-border-radius",
        "-moz-border-radius",
        "border-radius",
        "-webkit-border-top-left-radius",
        "-moz-border-radius-topleft",
        "border-top-left-radius",
        "-webkit-border-top-right-radius",
        "-moz-border-radius-topright",
        "border-top-right-radius",
        "-webkit-border-bottom-right-radius",
        "-moz-border-radius-bottomright",
        "border-bottom-right-radius",
        "-webkit-border-bottom-left-radius",
        "-moz-border-radius-bottomleft",
        "border-bottom-left-radius",
        "-webkit-border-image",
        "-moz-border-image",
        "-o-border-image",
        "border-image",
        "-webkit-border-image-source",
        "-moz-border-image-source",
        "-o-border-image-source",
        "border-image-source",
        "-webkit-border-image-slice",
        "-moz-border-image-slice",
        "-o-border-image-slice",
        "border-image-slice",
        "-webkit-border-image-width",
        "-moz-border-image-width",
        "-o-border-image-width",
        "border-image-width",
        "-webkit-border-image-outset",
        "-moz-border-image-outset",
        "-o-border-image-outset",
        "border-image-outset",
        "-webkit-border-image-repeat",
        "-moz-border-image-repeat",
        "-o-border-image-repeat",
        "border-image-repeat",
        "padding",
        "padding-top",
        "padding-right",
        "padding-bottom",
        "padding-left",
        "width",
        "min-width",
        "max-width",
        "height",
        "min-height",
        "max-height"
    ],
    [
        "font",
        "font-family",
        "font-size",
        "font-weight",
        "font-style",
        "font-variant",
        "font-size-adjust",
        "font-stretch",
        "font-effect",
        "font-emphasize",
        "font-emphasize-position",
        "font-emphasize-style",
        "font-smooth",
        "line-height",
        "text-align",
        "-webkit-text-align-last",
        "-moz-text-align-last",
        "-ms-text-align-last",
        "text-align-last",
        "vertical-align",
        "white-space",
        "text-decoration",
        "text-emphasis",
        "text-emphasis-color",
        "text-emphasis-style",
        "text-emphasis-position",
        "text-indent",
        "-ms-text-justify",
        "text-justify",
        "letter-spacing",
        "word-spacing",
        "-ms-writing-mode",
        "text-outline",
        "text-transform",
        "text-wrap",
        "-ms-text-overflow",
        "text-overflow",
        "text-overflow-ellipsis",
        "text-overflow-mode",
        "-ms-word-wrap",
        "word-wrap",
        "-ms-word-break",
        "word-break"
    ],
    [
        "color",
        "background",
        "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
        "background-color",
        "background-image",
        "background-repeat",
        "background-attachment",
        "background-position",
        "-ms-background-position-x",
        "background-position-x",
        "-ms-background-position-y",
        "background-position-y",
        "-webkit-background-clip",
        "-moz-background-clip",
        "background-clip",
        "background-origin",
        "-webkit-background-size",
        "-moz-background-size",
        "-o-background-size",
        "background-size"
    ],
    [
        "outline",
        "outline-width",
        "outline-style",
        "outline-color",
        "outline-offset",
        "opacity",
        "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
        "-ms-interpolation-mode",
        "-webkit-box-shadow",
        "-moz-box-shadow",
        "box-shadow",
        "filter:progid:DXImageTransform.Microsoft.gradient",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
        "text-shadow"
    ],
    [
        "-webkit-transition",
        "-moz-transition",
        "-ms-transition",
        "-o-transition",
        "transition",
        "-webkit-transition-delay",
        "-moz-transition-delay",
        "-ms-transition-delay",
        "-o-transition-delay",
        "transition-delay",
        "-webkit-transition-timing-function",
        "-moz-transition-timing-function",
        "-ms-transition-timing-function",
        "-o-transition-timing-function",
        "transition-timing-function",
        "-webkit-transition-duration",
        "-moz-transition-duration",
        "-ms-transition-duration",
        "-o-transition-duration",
        "transition-duration",
        "-webkit-transition-property",
        "-moz-transition-property",
        "-ms-transition-property",
        "-o-transition-property",
        "transition-property",
        "-webkit-transform",
        "-moz-transform",
        "-ms-transform",
        "-o-transform",
        "transform",
        "-webkit-transform-origin",
        "-moz-transform-origin",
        "-ms-transform-origin",
        "-o-transform-origin",
        "transform-origin",
        "-webkit-animation",
        "-moz-animation",
        "-ms-animation",
        "-o-animation",
        "animation",
        "-webkit-animation-name",
        "-moz-animation-name",
        "-ms-animation-name",
        "-o-animation-name",
        "animation-name",
        "-webkit-animation-duration",
        "-moz-animation-duration",
        "-ms-animation-duration",
        "-o-animation-duration",
        "animation-duration",
        "-webkit-animation-play-state",
        "-moz-animation-play-state",
        "-ms-animation-play-state",
        "-o-animation-play-state",
        "animation-play-state",
        "-webkit-animation-timing-function",
        "-moz-animation-timing-function",
        "-ms-animation-timing-function",
        "-o-animation-timing-function",
        "animation-timing-function",
        "-webkit-animation-delay",
        "-moz-animation-delay",
        "-ms-animation-delay",
        "-o-animation-delay",
        "animation-delay",
        "-webkit-animation-iteration-count",
        "-moz-animation-iteration-count",
        "-ms-animation-iteration-count",
        "-o-animation-iteration-count",
        "animation-iteration-count",
        "-webkit-animation-direction",
        "-moz-animation-direction",
        "-ms-animation-direction",
        "-o-animation-direction",
        "animation-direction"
    ],
    [
        "content",
        "quotes",
        "counter-reset",
        "counter-increment",
        "resize",
        "cursor",
        "-webkit-user-select",
        "-moz-user-select",
        "-ms-user-select",
        "user-select",
        "nav-index",
        "nav-up",
        "nav-right",
        "nav-down",
        "nav-left",
        "-moz-tab-size",
        "-o-tab-size",
        "tab-size",
        "-webkit-hyphens",
        "-moz-hyphens",
        "hyphens",
        "pointer-events"
    ]
]
<<<<<<< HEAD
```

## 雪碧图sprite

小图片（必须）sprite 合并

## 避免使用通配规则

除了传统意义的通配选择符之外还包括相邻兄弟选择符, 子选择符, 后代选择符和属性选择符。推荐id、class和标签选择符。

## 不要限定类选择器

不要用具体的标签限定类选择符，而是根据实际情况对类名进行扩展。

例如： ul.recommend ，改成  .recommend-list 或者 .list-recommend 。

## 避免使用后代选择符

通常处理后代选择符开销最高，使用字选择符更高效，最好使用下一条代替。

## 避免使用标签子选择符

如果有如： #header > li > a  这样基于子标签的自选择符，那么应该使用一个class来关联每个元素如：  .header-anchor 尽量使用`具体的类代替子选择符`。

注： IE浏览器中的单个样式表文件最多只能有4095个选择器，超过的会不被执行。

## 使用英文字体名称

不要用中文字体，全部用英文，英文有空格需用引号包含 常用：

黑体  SimHei 、宋体  SimSun 、楷体  KaiTi 、微软雅黑  'Microsoft YaHei'

## 避免非必要的 less 嵌套

只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

## 避免滥用 z-index 层级

最高级（遮罩级：990-1000）

百位级(组件级别：100、210、3YZ，XYZ)

十位级（普通区块：10、22、1Z、YZ）

个位级（业务级：1-9，Z）


## 伪类

[学习深度使用伪类](http://www.smashingmagazine.com/2011/03/how-to-use-css3-pseudo-classes/)