<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# CSS 书写规范

* [缩进](#indent)





## 缩进
<a id="indent"></a>

* 使用soft tab（4个空格）。

* 子级DOM结构可整体缩进提高可读性。

* 同个属性不同前缀的写法需要在`垂直方向保持对齐`，具体参照下边的写法；

* `无前缀`的标准属性应该写在有前缀的属性`后面`；

```css
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

## 其它

* 不允许有`空的规则`；

* 元素选择器用`小写字母`；

* 去掉`小数点`前面的0；

* 去掉数字中不必要的`小数点`和末尾的0；

* 属性值'0'后面不要加`单位`；

* 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

* 不要在一个文件里出现两个相同的规则；

* 用 `border: 0;` 代替 border: none;；

* 选择器不要超过`4层`（在scss中如果超过4层应该考虑用嵌套的方式来写）；

* 发布的代码中不要有 @import；

* 尽量少用'*'选择器。
