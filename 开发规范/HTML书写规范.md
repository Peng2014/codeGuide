<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# HTML书写规范

* [基本语法](#note)
* [HTML文档头部](#head)

* [简洁的标签结构](#dom)




## 基本语法
<a id="note"></a>

## 标签属性

1. 对于`属性`的定义，确保全部使用`"双引号"`，绝不要使用单引号；

2. 属性名全小写，用中划线做分隔符,例如 `rel="apple-touch-icon"`;

3. 不要省略可选的结束标签，如：`</li>`,`</body>`；

4. 属性最好能够按照特定的顺序出现以保证易读性；
    * 高复用性: `class`
    * 唯一性id,(少用): `id`
    * 属性类型角色: `name`，`data-*`，`type`
    * 链接相关信息: `src`,`href`,`for`
    * 信息补充说明: `value`,`title`,`alt`,`placeholder`
    * 限制样式相关: `max-length`,`max`,`min`,`pattern`,`disabled`
    
    ``` HTML
        `<a class="..." id="..." data-modal="toggle" href="#">Example link</a>`
    ```
    
5. boolean属性存在就为ture,不需要申明取值

    ``` HTML
        <input type="text" disabled>
        <input type="checkbox" value="1" checked>
        <select>
            <option value="1" selected>1</option>
        </select>
    ```
    
6. 习惯性书写注释，方便日后维护, 模块结构如下

7. 空标签要在标签内用注释的方式注明用途

    ``` HTML
        <!-- 注释写于dom结点外部，空标签要在标签内用注释的方式注明用途 -->
        <div class="ui-yyy">
            <div class="ui-yyy-hd"><span class="icon"><!--icon --></span></div>
            <div class="ui-yyy-bd">模块主体</div>
            <div class="ui-yyy-ft">模块底部</div>
        </div>
    ```


## HTML文档头部
<a id="head"></a>

``` html
    <!DOCTYPE HTML>
    <html lang="zh-Hans" dir="ltr">
    <head>
      <meta charset="UTF-8" />
      <meta content="width=device-width" name="viewport" />
      <title>cool-head</title>
      <meta name="keywords" content="" />
      <meta name="description" content="" />
      <meta name="robots" content="noindex,nofollow" />
      <meta name="apple-mobile-web-app-capable" content="no" />
      <meta name="Rating" content="Safe For Kids" />
      <meta name="revisit-after" content="1 days" />
      <meta name="author" content="" />
      <meta name="generator" content="" />
      <link rel="shortcut icon" href="/favicon.ico" />
      <link rel="apple-touch-icon" sizes="57x57" href="/apple-touch-icon-57x57.png" />
      <link rel="apple-touch-icon" sizes="72x72" href="/apple-touch-icon-72x72.png" />
      <link rel="apple-touch-icon" sizes="114x114" href="/apple-touch-icon-114x114.png" />
      <link href="style.css" media="all" type="text/css" rel="stylesheet" />
      <link rel="alternate" type="application/rss+xml" title="RSS Feed" href="" />
      <link rel="canonical" href="" />
      <link rel="prev" href="" />
      <link rel="next" href="" />
      <!--[if lt IE 9]>
      <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js" type="text/javascript"></script>
      <![endif]-->
      <script type="text/javascript">
      // here the pre-load JS starts.
      var Hello = 'World!';
      // Google analytics code
      var _gaq = _gaq || [];
      _gaq.push(['_setAccount', 'UA-00000000-0']);
      _gaq.push(['_trackPageview']);
      (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
      })();
      </script>
    </head>
    <body>
      <header>
       header
      </header>
      <article>
        <p>cool-head for HTML 5</p>
      </article>
      <footer>
       footer
      </footer>
      <script type="text/javascript">
        // here the post-load JS starts.
      </script>
    </body>
    </html>
```
  [更多(手机，微信）HTML文档头部信息参考](https://github.com/hzlzh/cool-head)






## 简洁的标签结构
<a id="dom"></a>

在编写HTML代码时，需要尽量避免多余的父节点,很多时候，需要通过迭代和重构来使HTML变得更少。

``` html
    <!-- Not well -->
    <span class="avatar">
        <img src="...">
    </span>

    <!-- Better -->
    <img class="avatar" src="...">
```



## JS生成标签

在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。


## 实用高于完美

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；

任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## HTML结构- 类命名
`BEM`命名规则
* Block —— 块 （代表了更高级别的抽象、模块或组件）
* Element —— 元素 （可选，代表block的后代，用于形成一个完整的Block）
* Modifier —— 修饰（可选，代表block不同的版本、状态）

尽量做到`“三无原则”`

* NO ID! 
* NO 辈分层级！ 
* NO 标签!