# Web开发代码风格规范

* 文件名
* 通用
* jshint检查配置项
	- https://github.com/seektan/jsstyle/blob/master/.jshintrc 
* javascript代码书写风格
	* 分号
	* 空格
	* 空行
	* 换行
	* 注释
	* 引号
	* 变量命名
	* 函数
	* 数组、对象
	* 括号
	* undefined
	* 其他

##文件名
小写、下划线
*  web_game.html
*  web_game.css
*  web_game.js
*  StaticSlider.js 模块化根据具体情况特殊处理

##通用
*  缩进使用soft tab（4个空格），可使用编辑器自动转换
*  HTML5 doctype
```
<!DOCTYPE html>
<html>
	...
</html>
```

###jshint配置
* 个人配置编辑器的jshint插件，应用以下参数
* 配置文件地址：https://github.com/seektan/jsstyle/blob/master/.jshintrc 
```
{
    //强制选项 不符合就报错
    "curly": true, // 循环和条件判断的代码块中总是使用大括号包围
    "freeze": true, // 禁止重写原生对象的原型
    "indent": true, // 代码缩进，jshint后续版本建废弃，现有版本不会告警
    "latedef": "nofunc", // 禁止定义之前使用变量，忽略 function 函数声明
    "unused": true, // 定义的变量未使用
    "newcap": true, // 构造器函数首字母大写
    "maxlen": 100, // 一行的最大长度
    
    //宽松选项 不符合也不报错
    "shadow": "inner", // 在不同作用域重复定义变量
    "expr": true, // 应该出现赋值或函数调用的地方使用表达式 比如 a === "test" ? func1() : func2();
    "proto": true, // __proto__属性的使用
    "scripturl": true, // 允许href="javascript:xxx"
    "sub": true, // 兼容obj.prop和obj["prop"]

    //预定义的全局变量
    "browser": true, // 预定义全局变量 document，navigator，FileReader
    "devel": true, // 定义用于调试的全局变量：console，alert
    "jquery": true, // jquery
    "nonstandard": true, // 非标准的escape 、 unescape
    "typed": true, // Int8Array 、ArrayBuffer等类型数字
    "worker": true, // Web Workers

    "globals": { // 业务相关
        "define": true,
        "require": true,
        "exports": true,
        "module": true,
        "TGP": true
    }
}

```
###参考地址
- http://jshint.com/docs/options/
- http://bubkoo.com/2014/02/22/JSHint-options/

##javascript代码书写风格

### 以下几种情况后需加分号：变量声明、表达式、return、throw、break、continue、do-while
```
/* var declaration */
var x = 1;

/* expression statement */
x++;

/* do-while */
do {
    x++;
} while (x < 10);
```

### 以下几种情况需要空格：
  - 二元运算符前后
  - 三元运算符'?:'前后
  - 代码块'{'前
  - 下列关键字前：else, while, catch, finally
  - 下列关键字后：if, else, for, while, do, switch, case, try, catch, finally, with, return, typeof
  - 单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后
  - 对象的属性值前
  - for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
  - 无论是函数声明还是函数表达式，'{'前一定要有空格
  - 函数的参数之间
```
// not good
var a = {
    b :1
};

// good
var a = {
    b: 1
};

// not good
++ x;
y ++;
z = x?1:2;

// good
++x;
y++;
z = x ? 1 : 2;

// not good
var a = [ 1, 2 ];

// good
var a = [1, 2];

// not good
var a = ( 1+2 )*3;

// good
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

### 以下几种情况需要空行：
  - 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
  - 注释前（当注释在代码块的第一行时，则无需空行）
  - 代码块后（在函数调用、数组、对象中则无需空行）
  - 文件最后保留一个空行
```
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
### 换行的地方，行末必须有','或者运算符；
  - 以下几种情况不需要换行：
    - 下列关键字后：else, catch, finally
    - 代码块'{'前
  - 以下几种情况需要换行：
    - 代码块'{'后和'}'前
    - 变量赋值后
```
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

### 单行注释
  - 双斜线后，必须跟一个空格；
  - 缩进与下一行代码保持一致；
  - 可位于一个代码行的末尾，与代码间隔一个空格。
```
if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

var zhangsan = 'zhangsan'; // one space after code

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

### 引号
  - 最外层统一使用单引号。
```
// not good
var x = "test";

// good
var y = 'foo',
    z = '<div id="test"></div>';
```

### 变量命名
  - 标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
  - 'ID'在变量名中全大写
  - 'URL'在变量名中全大写
  - 'Android'在变量名中大写第一个字母
  - 'iOS'在变量名中小写第一个，大写后两个字母
  - 常量全大写，用下划线连接
  - 构造函数，大写第一个字母
  - jquery对象必须以'$'开头命名
```
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

### 函数
	- 无论是函数声明还是函数表达式，'('前不要空格，但'{'前一定要有空格；
	- 函数调用括号前不需要空格；
	- 立即执行函数外必须包一层括号；
	- 不要给inline function命名；
	- 参数之间用', '分隔，注意逗号后有一个空格。
```
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

### 数组、对象
	- 对象属性名不需要加引号；
	- 对象以缩进的形式书写，不要写在一行；
	- 数组、对象最后不要有逗号。
```
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

### 括号
  - 下列关键字后必须有大括号（即使代码块的内容只有一行）：if, else, for, while, do, switch, try, catch, finally, with。
```
// not good
if (condition)
    doSomething();

// good
if (condition) {
    doSomething();
}
```

### undefined
  - 永远不要直接使用undefined进行变量判断；
  - 使用typeof和字符串'undefined'对变量进行判断。
```
// not good
if (person === undefined) {
    ...
}

// good
if (typeof person === 'undefined') {
    ...
}
```

### 其他
  - 不要混用tab和space；
  - 不要在一处使用多个tab或space；
  - 对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；
  - 行尾不要有空白字符；
  - switch的falling through和no default的情况一定要有注释特别说明；
  - 不允许有空的代码块。
```
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
```

###参考阅读
- Github上的统计数据 http://sideeffect.kr/popularconvention#javascript
- Code Guide by @AlloyTeam  http://alloyteam.github.io/CodeGuide/#javascript
- Airbnb JavaScript Style Guide() { https://github.com/airbnb/javascript
- 书写具备一致风格、通俗易懂 JavaScript 的原则 https://github.com/rwaldron/idiomatic.js/tree/master/translations/zh_CN
- Google JavaScript Style Guide https://google.github.io/styleguide/javascriptguide.xml
- JavaScript coding standards https://www.drupal.org/node/172169
- JavaScript Style Guides And Beautifiers https://addyosmani.com/blog/javascript-style-guides-and-beautifiers/
- Code Conventions for the JavaScript Programming Language http://javascript.crockford.com/code.html
- Coding style https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Coding_Style
