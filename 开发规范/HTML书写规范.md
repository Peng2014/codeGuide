<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# HTML书写规范


## 样式结构行为分离

* 不要用行内样式或脚本;
* 不要用在元素上使用`style`属性;
* 不使用表象元素:`<b>,<u>,<center>,<font>`;
* 不使用表象class名:`red`,`center`,`left`,`right`;
* HTML结构内容至上,装饰性图片或图标等都可尽量通过`:before`或`:after`添加;
* 对于内容为全部大写字母的情况，请通过CSS`text-transform:uppercase`设定;

## 标记结构良好

* 段落分隔符要使用实际对应的`<p>`元素，而不是用多个`<br>`标签;
* 列表中的条目`<li>`必须总是放置于`<ul>`、`<ol>`或`<dl>` 中;
* 推荐使用 `button` 代替 input，但必须声明 `type`,不过必须明确效果图上是否为按钮，还是只是一个样式为按钮的a链接;
* 表单元素的 name 不能设定为 action, enctype, method, novalidate, target, submit 会导致表单提交混乱;
* 表单元素,必须为含有描述性表单元素(input, textarea)添加label;

    ```html
        <!-- bad -->
        <p>姓 名: <input type="text" id="name" name="name" /></p>

        <!-- good -->
        <!-- 如:text、select、textarea 使用 for id 形式, radio、checkbox 用 for 包含的形式 -->
        <p><label for="name">姓 名: </label><input type="text" id="name" /></p>
    ```
* 不必为disabled, checked, selected 等 Boolean 属性添加属性值。

    ```html
    <!-- bad -->
    <input type="text" disabled="disabled"/>
    <!-- good -->
    <input type="text" disabled/>

    ```
* 重要图片必须加上alt属性,视频，canvas动画等也要确保有替代的接入接口;
* 给重要的元素和截断的元素加上title;

    ```html
        <!-- bad  -->
        <span class="text-box">
          <span class="square"></span>
          See the square next to me?
        </span>
        
        .text-box > .square {
          display: inline-block;
          width: 1rem;
          height: 1rem;
          background-color: red;
        }
        
        <!-- good -->
        <span class="text-box">
          See the square next to me?
        </span>
        
        .text-box:before {
          content: "";
          display: inline-block;
          width: 1rem;
          height: 1rem;
          background-color: red;
        }
    ```

## 书写链接地址时, 必须避免重定向





## HTML文档头部

* 注意文档类型：`<!DOCTYPE html>`

* html标签属性：`lang="zh-Hans"`

* `title` 每个页面必须有且仅有一个 title 元素;

* `base` 可用场景：首页、频道等大部分链接都为新窗口打开的页面;

* 不要使用古老的 <!– //–> 这种`hack脚本`, 它用于阻止第一代浏览器（Netscape 1和Mosaic）将脚本显示成文字;

* noscript 在用户代理不支持 JavaScript 的情况下提供说明;

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



## 标签属性

* 对于`属性`的定义，确保全部使用`"双引号"`，绝不要使用单引号；

* 属性名全小写，用中划线做分隔符,例如 `rel="apple-touch-icon"`;

* 省略style,script的type属性;

* 不要省略可选的结束标签,如：`</li>`,`</body>`;

* 属性最好能够按照特定的顺序出现以保证易读性;

    * 高复用性: `class`
    * 唯一性id,(少用): `id`
    * 属性类型角色: `name`，`data-*`，`type`
    * 链接相关信息: `src`,`href`,`for`
    * 信息补充说明: `value`,`title`,`alt`,`placeholder`
    * 限制样式相关: `max-length`,`max`,`min`,`pattern`,`disabled`
    
    ``` HTML
        `<a class="..." id="..." data-modal="toggle" href="#">Example link</a>`
    ```
    
* boolean属性存在就为ture,不需要申明取值

    ``` HTML
        <input type="text" disabled>
        <input type="checkbox" value="1" checked>
        <select>
            <option value="1" selected>1</option>
        </select>
    ```

* 空标签要在标签内用注释的方式注明用途

    ``` HTML
        <!-- 注释写于dom结点外部，空标签要在标签内用注释的方式注明用途 -->
        <div class="ui-yyy">
            <div class="ui-yyy-hd"><span class="icon"><!--icon --></span></div>
            <div class="ui-yyy-bd">模块主体</div>
            <div class="ui-yyy-ft">模块底部</div>
        </div>
    ```

* 省略样式表与脚本上的type属性。
    
    ```html
        <!-- good -->
        <link rel="stylesheet" href="main.css">
        <script src="main.js"></script>
    ```
    
* 链接属性最后添加`/`,避免重定向:`href="http://task.zhubajie.com/"`, 即须在URL地址后面加上`“/”`;




## 简洁的标签结构

在编写HTML代码时，需要尽量避免多余的父节点,很多时候，需要通过迭代和重构来使HTML变得更少。

``` html
    <!-- Not well -->
    <span class="avatar">
        <img src="...">
    </span>

    <!-- Better -->
    <img class="avatar" src="...">
```



## HTML结构- 类命名

### `BEM`命名规则
* Block —— 块 （代表了更高级别的抽象、模块或组件）
* Element —— 元素 （可选，代表block的后代，用于形成一个完整的Block）
* Modifier —— 修饰（可选，代表block不同的版本、状态）

### 尽量做到`“三无原则”`

* NO ID 
* NO 辈分层级
* NO 标签

```html
    <!-- Good -->
    <ul class="nav">
        <li class="nav-item">
            <a href="#">Tab1</a>
        </li>
        <li class="nav-item">
            <a href="#">Tab2</a>
        </li>
        <li class="nav-item nav-item-active">
            <a href="#">Tab3</a>
        </li>
        <li class="nav-item">
            <a href="#">Tab4</a>
        </li>
    <ul>
    
    .block {}
    .block-element {}
    .block-modifier {}
    .block-element-modifier {}
```
### 模块的扩展和继承

* 基础模块：nav
* 扩展模块：nav nav-inline，扩展模块继承了基础模块所有的特性并加上自己的一些新特性
* 私有模块：nav nav-inline menu-nav，私有模块-基础模块名


### class命名约定

class 对于选中命名`.active`; 对于hover，支持伪类使用`:hover`，不支持的使用 `.hover`，隐藏使用`.hide` 。

id 和 class 的选择，如果`只使用一次`，使用`id`,如果使用多次使用class，如果需要和`js交互`，`使用id`,如果需要交互并且页面中有大量重复，请参见下一条。

对于作为`js钩子`的 class 命名规则为以`"J-"开头`(J,象形钩子的形状)，后面加上原应有的命名，在使用class的时候需要放在最前面。如:class="J-tabContent"。（注意：`钩子`，不允许在css中定义任何的样式效果）


## 文件引用

样式文件必须外链至`<head>...</head>`之间;

页面级别的 JavaScript 文件必须外链至页面底部;

引入JS库文件, 文件名须包含库名称及`版本号`及是否为`压缩版`, 
* 比如jquery-1.4.1.min.js; 
* 引入插件, 文件名格式为库名称+插件名称, 比如jQuery.cookie.js;
* 脚本引用带上async属性`<script src="main.js" async></script>`

## 在合适的条件下，利用 <thead>、<tbody>和<th>标签 (以及Scope属性）

```html
    <table summary="This is a chart of year-end returns for 2005.">
        <thead>
            <tr>
                <th scope="col">Table header 1</th>
                <th scope="col">Table header 2</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Table data 1</td>
                <td>Table data 2</td>
            </tr>
        </tbody>
    </table>
```

## 特殊符号使用

尽可能使用代码替代: 比如 <( &lt; ) & >( &gt; )& 空格( &nbsp; )等等

特殊符号详见


## JS生成标签

在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。

## 实用高于完美

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；

任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## HTML验证

可以最好使用[W3C HTML validator ](https://validator.w3.org/)对页面进行测试，并且有时候很多细节问题不太容易被发现。
