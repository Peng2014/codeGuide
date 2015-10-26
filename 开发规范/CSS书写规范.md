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
