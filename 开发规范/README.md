<a id="top"></a>

 <a href="#top" target="_self" style="position:fixed;bottom:60px;right:100px;z-index:10;display:block;text-decoration=none;background:#999;color:#fff;width:30px;height:30px;border-radius:5px;line-height:30px;text-align:center">top</a>

# 通用开发规范
> 列举了一些可应用在 HTML, JavaScript 和 CSS/SCSS 上的通用规则。 
> 其他较为重要的规范，例如图片格式;

## 前端开发核心思想

* 表现、内容和行为的分离
* [标记应该是结构良好、语义正确](http://www.bbc.co.uk/guidelines/futuremedia/technical/semantic_markup.shtml)
* JavaScript应起到渐进式增强用户体验的作用

## 代码工程化思想

1. 保持代码易于维护
2. 保持代码清晰易懂
3. 保持代码可拓展性

## 合理的HTML结构

* 了解页面的层次组织和阅读效果，在无样式的情况下，能够展示合理的HTML结构文档。

* 标题必须有层次，能表明从大到小不同级别的重要性，h1具有最大的字体大小。

## 文件和目录命名

* 只能出现`小写英文字母`，`数字`和`横杠( - )`，以英语单词优先，多个单词以横杠 ( - ) 接;
* 确保最好`小写英文字母`开头命名;
* 尽量避免采用以下词汇来命名： ad、ads、adv、banner、sponsor、gg、guangg、guanggao;
* 该规范适用于所有前端维护的内容和相关目录。(smarty, html, less, css, js, png, gif, jpg);
* `资源的字母名称`必须全为`小写`，避免某些操作系统对大写敏感易出错;

例如：
>* 项目命名：my-project-name ;
>* 目录命名，静态资源名称都统一，例如：img,ui,widget;
>* HTML文件命名 : error-report.html
>* CSS,LESS文件命名:retina-sprites.less;
>* js文件命名 : account-model.js; my-file.min.css

不推荐以下命名：
>* MyScript.js
>* myCamelCaseName.css
>* i_love_underscores.html
>* 1001-scripts.js
>* my-file-min.css


## 协议

不要制定引入资源所带的具体协议(`http:`或`https:`),不指定协议使得URL从绝对路径转为相对。

```html
    <!-- bad -->
    <script src="http://cdn.com/foundation.min.js"></script>
    
    .example {
      background: url(http://static.example.com/images/bg.jpg);
    }
    
    <!-- good -->
    <script src="//cdn.com/foundation.min.js"></script>
    
    .example {
      background: url(//static.example.com/images/bg.jpg);
    }
    
```

## 缩进

使用soft tab（4个空格）


## 注释

注释是你自己与你的小伙伴们了解代码写法和目的的唯一途径。

当你写注释时一定要注意：不要写你的代码都干了些什么，而要写你的代码为什么要这么写，背后的考量是什么。

当然也可以加入所思考问题或是解决方案的链接地址。

```javascript
    //bad
    var offset = 0;
     
    if(includeLabels) {
      // Add offset of 20
      offset = 20;
    }
    
    //good
    var offset = 0;
     
    if(includeLabels) {
      // If the labels are included we need to have a minimum offset of 20 pixels
      // We need to set it explicitly because of the following bug: http://somebrowservendor.com/issue-tracker/ISSUE-1
      offset = 20;
    }
```

可以使用注释工具自动生成文档。例如JavaScript方面有[JSDoc](http://usejsdoc.org/)或[YUIDoc](http://yui.github.io/yuidoc/)。

## 代码检查

遵循规范固然很好，但是有自动化流程来确保其执行情况，岂不更佳。

对于JavaScript，建议使用[JSLint](http://www.jslint.com/)或[JSHint](http://www.jshint.com/).


## 图片

* 永远不要把颜色配置嵌入到图片里,从Photoshop保存图片时，务必去掉"Embed Color Profile"选项的勾选;

