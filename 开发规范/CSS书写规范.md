<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# CSS 书写规范

* [缩进](#indent)





## 缩进
<a id="indent"></a>

使用soft tab（4个空格）。

子级DOM结构可整体缩进提高可读性。

``` CSS
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

``` CSS
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

``` less
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

``` css
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
        ...
    }
```