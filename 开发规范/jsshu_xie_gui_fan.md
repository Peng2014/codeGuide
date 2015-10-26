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