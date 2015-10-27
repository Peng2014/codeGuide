# JS书写规范


## 缩进
<a id="indent"></a>

* 使用soft tab（4个空格）。

```JavaScript
    var x = 1,
        y = 1;
    
    if (x < y) {
        x += 10;
    } else {
        x += 1;
    }
```

## 空格

以下几种情况不需要空格：

* 对象的属性名后
* 前缀一元运算符后
* 后缀一元运算符前
* 函数调用括号前
* 无论是函数声明还是函数表达式，'('前不要空格
* 数组的'['后和']'前
* 对象的'{'后和'}'前
* 运算符'('后和')'前

以下几种情况需要空格：

* 二元运算符前后
* 三元运算符'?:'前后
* 代码块'{'前
* 下列关键字前：else, while, catch, finally
* 下列关键字后：if, else, for, while, do, switch, case, try, catch, finally, with, return, typeof
* 单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后
* 对象的属性值前
* for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
* 无论是函数声明还是函数表达式，'{'前一定要有空格
* 函数的参数之间

```JavaScript
    // not good
    var a = {
        b :1
    };
    
    ++ x;
    y ++;
    z = x?1:2;
    
    var a = [ 1, 2 ];
    
    var a = ( 1+2 )*3;
    
    // good
    var a = {
        b: 1
    };
    
    ++x;
    y++;
    z = x ? 1 : 2;
    
    var a = [1, 2];
    
    var a = (1 + 2) * 3;
    
    // no space before '(', one space before '{', one space between function parameters
    var doSomething = function(a, b, c) {
        // do something
    };
    
    // no space before '('
    doSomething(item);
    
    // not good
    for(i=0;i<6;i++){
        x++;
    }
    
    // good
    for (i = 0; i < 6; i++) {
        x++;
    }
```

## 空行

以下几种情况需要空行：

* 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
* 注释前（当注释在代码块的第一行时，则无需空行）
* 代码块后（在函数调用、数组、对象中则无需空行）
* 文件最后保留一个空行

```javascript
    // need blank line after variable declaration
    var x = 1;
    
    // not need blank line when variable declaration is last expression in the current block
    if (x >= 1) {
        var y = x + 1;
    }
    
    var a = 2;
    
    // need blank line before line comment
    a++;
    
    function b() {
        // not need blank line when comment is first line of block
        return a;
    }
    
    // need blank line after blocks
    for (var i = 0; i < 2; i++) {
        if (true) {
            return false;
        }
    
        continue;
    }
    
    var obj = {
        foo: function() {
            return 1;
        },
    
        bar: function() {
            return 2;
        }
    };
    
    // not need blank line when in argument list, array, object
    func(
        2,
        function() {
            a++;
        },
        3
    );
    
    var foo = [
        2,
        function() {
            a++;
        },
        3
    ];
    
    
    var foo = {
        a: 2,
        b: function() {
            a++;
        },
        c: 3
    };
```

## 换行

换行的地方，行末必须有','或者运算符；

以下几种情况不需要换行：

* 下列关键字后：else, catch, finally
* 代码块'{'前

以下几种情况需要换行：

* 代码块'{'后和'}'前
* 变量赋值后


```javascript
    // not good
    var a = {
        b: 1
        , c: 2
    };
    
    x = y
        ? 1 : 2;
    
    // good
    var a = {
        b: 1,
        c: 2
    };
    
    x = y ? 1 : 2;
    x = y ?
        1 : 2;
    
    // no need line break with 'else', 'catch', 'finally'
    if (condition) {
        ...
    } else {
        ...
    }
    
    try {
        ...
    } catch (e) {
        ...
    } finally {
        ...
    }
    
    // not good
    function test()
    {
        ...
    }
    
    // good
    function test() {
        ...
    }
    
    // not good
    var a, foo = 7, b,
        c, bar = 8;
    
    // good
    var a,
        foo = 7,
        b, c, bar = 8;
        
```

## 注释

### 单行注释
双斜线后，必须跟一个空格；

缩进与下一行代码保持一致；

可位于一个代码行的末尾，与代码间隔一个空格。


### 多行注释
最少三行, '*'后跟一个空格，具体参照下边的写法；

建议在以下情况下使用：

难于理解的代码段
* 可能存在错误的代码段
* 浏览器特殊的HACK代码
* 业务逻辑强相关的代码

### 文档注释
各类标签@param, @method等请参考usejsdoc和JSDoc Guide；

建议在以下情况下使用：

* 所有常量
* 所有函数
* 所有类

```JavaScript
    if (condition) {
        // if you made it here, then all security checks passed
        allowed();
    }
    
    var zhangsan = 'zhangsan'; // one space after code
    
    
    /*
     * one space after '*'
     */
    var x = 1;

    /**
     * @func
     * @desc 一个带参数的函数
     * @param {string} a - 参数a
     * @param {number} b=1 - 参数b默认值为1
     * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
     * @param {object} d - 参数d为一个对象
     * @param {string} d.e - 参数d的e属性
     * @param {string} d.f - 参数d的f属性
     * @param {object[]} g - 参数g为一个对象数组
     * @param {string} g.h - 参数g数组中一项的h属性
     * @param {string} g.i - 参数g数组中一项的i属性
     * @param {string} [j] - 参数j是一个可选参数
     */
    function foo(a, b, c, d, g, j) {
        ...
    }
```

##变量命名

标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
* 'ID'在变量名中全大写
* 'URL'在变量名中全大写
* 'Android'在变量名中大写第一个字母
* 'iOS'在变量名中小写第一个，大写后两个字母
* 常量全大写，用下划线连接
* 构造函数，大写第一个字母
* jquery对象必须以'$'开头命名

```javascript
    var thisIsMyName;
    
    var goodID;
    
    var reportURL;
    
    var AndroidVersion;
    
    var iOSVersion;
    
    var MAX_COUNT = 10;
    
    function Person(name) {
        this.name = name;
    }
    
    // not good
    var body = $('body');
    
    // good
    var $body = $('body');
```

## 变量声明

一个函数作用域中所有的变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明。

```javascript
    function doSomethingWithItems(items) {
        // use one var
        var value = 10,
            result = value + 10,
            i,
            len;
    
        for (i = 0, len = items.length; i < len; i++) {
            result += 10;
        }
    }
```

## 函数

无论是函数声明还是函数表达式，'('前不要空格，但'{'前一定要有空格；

函数调用括号前不需要空格；

立即执行函数外必须包一层括号；

不要给inline function命名；

参数之间用', '分隔，注意逗号后有一个空格。

```javascript
    // no space before '(', but one space before'{'
    var doSomething = function(item) {
        // do something
    };
    
    function doSomething(item) {
        // do something
    }
    
    // not good
    doSomething (item);
    
    // good
    doSomething(item);
    
    // requires parentheses around immediately invoked function expressions
    (function() {
        return 1;
    })();
    
    // not good
    [1, 2].forEach(function x() {
        ...
    });
    
    // good
    [1, 2].forEach(function() {
        ...
    });
    
    // not good
    var a = [1, 2, function a() {
        ...
    }];
    
    // good
    var a = [1, 2, function() {
        ...
    }];
    
    // use ', ' between function parameters
    var doSomething = function(a, b, c) {
        // do something
    };
```

## 数组、对象

对象属性名不需要加引号；

对象以缩进的形式书写，不要写在一行；

数组、对象最后不要有逗号。

```javascript
    // not good
    var a = {
        'b': 1
    };
    
    var a = {b: 1};
    
    var a = {
        b: 1,
        c: 2,
    };
    
    // good
    var a = {
        b: 1,
        c: 2
    };
```

## 括号

下列关键字后必须有大括号（即使代码块的内容只有一行）：

if, else, for, while, do, switch, try, catch, finally, with。

```javascript
    // not good
    if (condition)
        doSomething();
    
    // good
    if (condition) {
        doSomething();
    }
```

## null

适用场景：

* 初始化一个将来可能被赋值为对象的变量
* 与已经初始化的变量做比较
* 作为一个参数为对象的函数的调用传参
* 作为一个返回对象的函数的返回值

不适用场景：

* 不要用null来判断函数调用时有无传参
* 不要与未初始化的变量做比较

```javascript
    // not good
    function test(a, b) {
        if (b === null) {
            // not mean b is not supply
            ...
        }
    }
    
    var a;
    
    if (a === null) {
        ...
    }
    
    // good
    var a = null;
    
    if (a === null) {
        ...
    }
```

undefined

永远不要直接使用undefined进行变量判断；

使用typeof和字符串'undefined'对变量进行判断。


```javascript
    // not good
    if (person === undefined) {
        ...
    }
    
    // good
    if (typeof person === 'undefined') {
        ...
    }
```

## 杂项

* 不要混用tab和space；

* 不要在一处使用多个tab或space；

* 换行符统一用'LF'；

* 对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；

* 行尾不要有空白字符；

* switch的falling through和no default的情况一定要有注释特别说明；

* 不允许有空的代码块。

```javascript
    // not good
    var a   = 1;
    
    function Person() {
        // not good
        var me = this;
    
        // good
        var _this = this;
    
        // good
        var that = this;
    
        // good
        var self = this;
    }
    
    // good
    switch (condition) {
        case 1:
        case 2:
            ...
            break;
        case 3:
            ...
        // why fall through
        case 4
            ...
            break;
        // why no default
    }
    
    // not good with empty block
    if (condition) {
    
    }
    
<<<<<<< HEAD
```

## 命名规范

    文件命名可读性强、文件夹、文件的命名与命名空间应能代表代码功能，可读性强。

### 函数命名

小驼峰命名方式，首字母小写:

    `function funName() {}`

### 类命名

驼峰命名，首字母大写： function ClassName() {}

常量大写，单词之间用下划线分隔（_）,便于阅读

    `var VARIABLE_NAME = 1024;`

## 变量

### 驼峰命名

    var variableName = {};

## 编码规则

### 排版缩进

采用统一的缩进方式排版代码。缩进为4个空格

```javascript
    if (condition1 || condition2) {
    action1;
} else if (condition3 && condition4) {
    action2;
} else if (condition5
           && condition6
           && condition7
           && condition8) {
    action2;
} else {
    default action;
}
```

* 关键词、条件括弧后面使用空格；

* 运算操作符号两侧使用空格；

* 语句分割符‘,’后面使用空格

    var name[空格]=[空格]value;
    if[空格](a,[空格]b) {
    }


    左大括号"{"居行尾, 右大括号"}"单独占一行，居行首

    if (a && b) {

    }


    句末必须用分号结尾

var fn = function () {
};//这里没有分号的话，脚本解析器会报错！！！
(function () {
   alert(1);
})();


单行过长应在适当位置予以换行,增强可读性

if 语句括号中的条件若过多过长，应予以折行；折行后，||、&& 等符号应与 “(” 后的第一个字母纵向对齐
```javascript
    if (condition1
    && condition2
    || condition3) {
}
```

if、while、for、do语句的执行体总是用"{"和"}"括起来，即使在其结构体内只有一条语句
```javascript
    if (s==100) {
    alert('shit!');
}
```

语法意义相互独立的代码将用空行分隔

    a++; b++; //避免同一行书写两个表达式if (a > b) {
    value = a;  //行间不用空行间隔
}

var variableName = value;   //与上一代码行使用空行间隔

##注释规范

###文件注释

文件注释要标明作者、文件版本、创建/修改时间、重大版本修改记录

/**
 * @file Image.js
 * @description 功能详细描述
 */

函数描述

函数或者类等都要添加头描述

/**
 * 简述
 *
 * 功能详细描述
 *
 * @param <String> arg1 参数1
 * @param <Number> arg2 参数2，默认为0
 * @return <Boolean> 看xxx是否成功
 */
 function fooFunction (arg1, arg2) {
 }


操作注释

单行注释,写在代码上面

多行注释

/*
* 注释操作说明
*/for( var i = 0; i < obj.lenght; i++) {
}


注释标签参考

    @addon把一个函数标记为另一个函数的扩张，另一个函数的定义不在源文件中。
    @argument用大括号中的自变量类型描述一个自变量。
    @author函数/类作者的姓名。
    @base如果类是继承得来，定义提供的类名称。
    @constructor描述一个类的构造器。
    @extends表示派生出当前类的另一个类。
    @link类似于@link标签，用于连接许多其它页面。
    @param用大括号中的参数类型描述一个参数。
    @private表示函数/类为私有，不应包含在生成的文档中。
    @requires表示需要另一个函数/类。
    @return描述一个函数的返回值。
    @type指定函数/成员的返回类型。
    @version函数/类的版本号。

jQuery代码规范与最佳实践


1 所有使用或缓存jQuery对象的变量应该以 $ 开头

2 始终将jQuery选择器返回的对象缓存到本地变量中以复用。

  var $myDiv = $("#myDiv");
  $myDiv.click(function(){....});


选择器

1 ID选择器可用时就使用ID选择。

2 当使用类/伪类选择器时，总是给选择器附上元素类型来避免扫描整个DOM树。

// BAD 在整个DOM树中扫描"products"类名var $products = $(".products");

// GOOD 只在DIV元素中扫描"products"类名var $products = $("div.products");


3 在ID > 子节点层级选择器中使用 find() 方法。

    // BAD, Sizzle选择器引擎查找层级
    var $productIds = $("#products div.id");

    // GOOD, 只有div.id走Sizzle选择器引擎
    var $productIds = $("#products").find("div.id");


4 选择器后半部分比前半部分明确。

    // 未优化
    $("div.data .gonzalez");

    // 优化
    $(".data td.gonzalez");


5 避免冗余选择器。

    $(".data table.attendees td.gonzalez");

    // Better: 有必要时要去掉中间不必要的内容
    $(".data td.gonzalez");


6 给选择器添加上下文。

// 要扫描整个DOM树寻找
$('.class');

// 只在#class-container里扫描
$('.class', '#class-container');


7 避免使用通配符选择器。

$('div.container > *'); // BAD
$('div.container').children(); // BETTER

8 避免使用隐式通配选择器。当省略下面的input时，会隐式的使用通配符选择器。

$('div.someclass :radio'); // BAD
$('div.someclass input:radio'); // GOOD

9 ID选择器使用的是 document.getElementById() ，ID选择器无需嵌套ID。

$('#outer #inner'); // BAD
$('div#inner'); // BAD
$('.outer-container #inner'); // BAD
$('#inner'); // GOOD

事件

1 每个页面只使用一个Document Ready函数。利于调试。

2 不要使用匿名函数绑定事件。匿名函数不利于调试、维护、测试和复用。

$("#myLink").on("click", function(){...}); // BAD

// GOODfunction myLinkClickHandler(){...}

$("#myLink").on("click", myLinkClickHandler);

3 Document ready函数不应该是匿名函数。匿名函数不能复用也无法对其测试。

$(function(){ .. }); // BAD: 不容易复用也不利于测试

// GOOD
$(initPage); // or $(document).ready(initPage);function initPage(){
// Document ready里可以初始化变量和调用其他初始化函数
}


4 不要在HTML文件里（行内JS）

5 如有需要，对事件使用自定义命名空间，这有利于去解绑某DOM元素上特定的事件而不会影响到该DOM元素上的其他事件。

$("#myLink").on("click.mySpecialClick", myEventHandler); // GOOD// 后面会很容易的解绑这个特定的点击事件
$("#myLink").unbind("click.mySpecialClick");


Ajax

1 避免使用 .getJSON() 和 .get() ，只使用 $.ajax() ，前两者都是在内部使用的后者。

2 明确设置数据的类型 dataType ，这样很容易知道当前正在处理什么样的数据。

链式写法

1 尽量使用链式写法而不是用变量缓存或者多次调用选择器方法。

$("#myDiv").addClass("error").show();

2 当链式写法超过三次或者因为事件绑定变得复杂后，使用换行和缩进保持代码可读性。

    $("#myLink")
    .addClass("bold")
    .on("click", myClickHandler)
    .on("mouseover", myMouseOverHandler)
    .show();

3 对于更长的链式调用，可接受用变量缓存一个中间对象。
其他原则

1 参数尽量使用对象字面量

$myLink.attr("href", "#").attr("title", "my link").attr("rel", "external"); // BAD// GOOD
$myList.attr({
    href: "#",
    title: "my link",
    rel: "external"
});

2 不要把CSS混进jQuery

$("#mydiv").css({'color':red, 'font-weight':'bold'}); // BAD

