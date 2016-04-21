# Web前端规范

##目录
###大界面
- frames
- common
- center
	- gamelibrary
	- gift
	- privilege
	- toolbox
	- sociality
###助手
- pallas
- cf
- dnf

目录与上报路径统一
- [] /gamelibrary/mmog.html
- [] \center\plat\gamelibrary\MMOG.html

##文件名
小写、下划线
*  web_game.html
*  web_game.css
*  web_game.js
*  StaticSlider.js 模块化

##通用
*  缩进使用soft tab（4个空格），可使用编辑器自动转换

##HTML
###HTML5 doctype
```
<!DOCTYPE html>
<html>
	...
</html>
```

##javascript
- [x] 单行长度不要超过80

- [x] 以下几种情况后需加分号：变量声明、表达式、return、throw、break、continue、do-while

- [x] 以下几种情况需要空格：
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

- [x] 以下几种情况需要空行：
  - 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
  - 注释前（当注释在代码块的第一行时，则无需空行）
  - 代码块后（在函数调用、数组、对象中则无需空行）
  - 文件最后保留一个空行

- [x] 换行的地方，行末必须有','或者运算符；
  - 以下几种情况不需要换行：
    - 下列关键字后：else, catch, finally
    - 代码块'{'前
  - 以下几种情况需要换行：
    - 代码块'{'后和'}'前
    - 变量赋值后

- [x] 单行注释
  - 双斜线后，必须跟一个空格；
  - 缩进与下一行代码保持一致；
  - 可位于一个代码行的末尾，与代码间隔一个空格。
  
- [x] 引号
  - 最外层统一使用单引号。

- [x] 变量命名
  - 标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
  - 'ID'在变量名中全大写
  - 'URL'在变量名中全大写
  - 'Android'在变量名中大写第一个字母
  - 'iOS'在变量名中小写第一个，大写后两个字母
  - 常量全大写，用下划线连接
  - 构造函数，大写第一个字母
  - jquery对象必须以'$'开头命名
  
- [x] 括号
  - 下列关键字后必须有大括号（即使代码块的内容只有一行）：if, else, for, while, do, switch, try, catch, finally, with。

- [x] undefined
  - 永远不要直接使用undefined进行变量判断；
  - 使用typeof和字符串'undefined'对变量进行判断。

- [x] 杂项
  - 不要混用tab和space；
  - 不要在一处使用多个tab或space；
  - 对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；
  - 行尾不要有空白字符；
  - switch的falling through和no default的情况一定要有注释特别说明；
  - 不允许有空的代码块。
