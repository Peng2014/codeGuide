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

## 空格

以下几种情况不需要空格：

* 属性名后
* 多个规则的分隔符','前
* !important '!'后
* 属性值中'('后和')'前
* 行末不要有多余的空格

以下几种情况需要空格：

* 属性值前
* 选择器'>', '+', '~'前后
* '{'前
* !important '!'前
* 属性值中的','后
* 注释'/\*'后和'\*/'前

``` CSS
    /* not good */
    .element {
        color :red! important;
        background-color: rgba(0,0,0,.5);
    }
    
    /* not good */
    .element ,
    .dialog{
        color :red! important;
        background-color: rgba(0,0,0,.5);
    }
    
    /* not good */
    .element>.dialog{
        ...
    }
    
    
    /* not good */
    .element{
        ...
    }
    
    /* good */
    .element {
        ...
    }
```