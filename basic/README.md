# 基本原则

#### 结构、样式、行为分离
尽量确保文档和模板只包含 `HTML` 结构，样式都放到样式表里，行为都放到脚本里。

#### 缩进
统一**Tab**缩进（总之缩进统一即可），不要使用 空格 或者 `Tab` 、空格混搭。

#### 文件编码

新的项目尽量采用 **utf-8** 编码。 

使用方法：
* 在 HTML中指定编码 `<meta charset="utf-8">` ；
* 无需使用 `@charset` 指定样式表的编码，它默认为 `UTF-8` （参考 [@charset](https://developer.mozilla.org/en-US/docs/Web/CSS/@charset)）；



#### 一律使用小写字母
```html
<!-- Recommended -->
<img src="google.png" alt="Google">

<!-- Not recommended -->
<A HREF="/">Home</A>
```

```css
/* Recommended */
color: #e5e5e5;

/* Not recommended */
color: #E5E5E5;
```

#### 省略外链资源 URL 协议部分（可参考执行）
省略外链资源（图片及其它媒体资源）URL 中的 `http` / `https` 协议，使 URL 成为相对地址，避免 [Mixed Content](https://developer.mozilla.org/en-US/docs/Security/MixedContent) 问题，减小文件字节数。

**其它协议（`ftp` 等）的 URL 不省略。**
```html
<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Not recommended -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
```

```css
/* Recommended */
.example {background: url(//www.google.com/images/example);}

/* Not recommended */
.example {background: url(http://www.google.com/images/example);}
```

#### 统一注释
良好的注释能大大减少开发和维护的沟通成本。通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

###### HTML 注释

- 模块注释  

>  ** HTML** 注释尽量有始有终，因为很容易导致由于div闭合标签``</div>``丢失而出现的页面混乱问题【页面层级嵌套错误】。

```html
<!-- 文章列表列表模块 --> // 注释开始
<div class="article-list">
...
</div>
<!-- // 文章列表列表模块 --> //注释结束
``` 

###### CSS 注释

样式表总体注释 -- 声明样式表的相关信息（主要包括样式表的** 描述 ** 、** 作者 **、** 创建/更新时间** 、** 版本号 **）

``` CSS
/**  
 * @Description: the stylesheet of XXX 
 * @authors: xxx (xxx@fengniao.com)
 * @date:    2015-10-12 10:57:15
 * @version: 1.0
 */ 

```

组件块和子组件块以及声明块之间使用一空行分隔，注意不要留有多于的空格；
```css
/* selector */ 
.selector {padding: 15px; margin-bottom: 15px;}

/* selector-secondary */
.selector-secondary {display: block; /* 注释*/}
.selector-three {display: span;}

```

######JavaScript 注释
- 单行注释

`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。

```javascript 
function foo(p1, p2, p3) { 
    var p3 = p3 || 10;
    
    // 我是注释
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

- 多行注释

避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

- 函数/方法注释
1. 需要说明函数的描述、作者、创建/修改时间、版本号
2. 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。；
3. 参数和返回值注释必须包含类型信息和说明；
4. 当函数是内部函数，外部不可访问时，可以使用 @inner 标识；

```javascript
/**
 * @description: the script xxx
 * @author: xxxx (xxx@xxx.com)
 * @date:  xx-xx-xx
 * @version:  xx
  
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

- 文件注释

文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 应该提供文件的大体内容, 它的作者, 依赖关系和兼容性信息。如下:

```javascript
/**
 * @fileoverview Description of file, its uses and information
 * about its dependencies.
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2015 Meizu Inc. All Rights Reserved.
 */
```

#### 代码验证 （可根据具体情况斟酌采用）
* 使用 [W3C HTML Validator](http://validator.w3.org/) 来验证你的HTML代码有效性；
* 使用 [W3C CSS Validator](http://jigsaw.w3.org/css-validator/validator.html.zh-cn) 来验证你的CSS代码有效性；

代码验证不是最终目的，真的目的在于让开发者在经过多次的这种验证过程后，能够深刻理解到怎样的语法或写法是非标准和不推荐的，即使在某些场景下被迫要使用非标准写法，也可以做到心中有数。
