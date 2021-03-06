## sass

[toc]  

[scss总结](https://github.com/zhangwen0424/sass-test/blob/master/single/test.scss)

```
* 
 *  * 编译为css目标文件
 *
 *  * 编译方式：
 *      1.命令行
 *      2.GUI工具编译
 *      3.自动化编译, Grunt 和 Gulp
 *
 *  * 命令行编译
 *      sass --watch  single/test.scss:single/nested/test.css --style nested
 *      sass --watch  single/test.scss:single/expanded/test.css --style expanded
 *      sass --watch  single/test.scss:single/compact/test.css --style compact
 *      sass --watch  single/test.scss:single/compressed/test.css --style compressed
 *
 *  * 命令行编译
 *    # 将 Sass 转换为 SCSS
 *    $ sass-convert style.sass style.scss
 *
 *    # 将 SCSS 转换为 Sass
 *    $ sass-convert single/test.scss single/test.sass
 *
 *  * 嵌套方式
 *      选择器嵌套，属性嵌套，伪类嵌套
 *
 *  * 混合宏 vs 继承 vs 占位符
 *             混合宏                   继承                              占位符
 *      声明    @mixin                  .class                           %placeholder
 *      调用    @inclued                @extend                          @extend
 *      使用    相同代码块使用不同值       无需传不同值，将调用相同基类代码合并   和继承类似，但不调用不产生基类代码，合并相同代码
 *      不足    多次调用混合宏，代码冗余    即使不调用也会生成基类
 *  
 *  * 插值运算 
 *      用于变量和属性中
 *
 *  * 控制命令
 *      if else
 *      while
 *      for (i) form (start) to (end)  
 *      for (i) form (start) through (end)  
 *      while
 *      each in
 *
 *  * 函数
 *      字符串函数
 *        unquote：去掉引号
 *        quote：增加引号(处理字符串中不可有空格)
 *        To-upper-case: 转化为大写字母
 *        To-lower-case: 转化为小写字母
 *
 *
 *      数字函数
 *        percentage($value) 将一个不带单位的数转换成百分比值（数字不可有单位）
 *        round($value) 将数值四舍五入，转换成一个最接近的整数
 *        ceil($value) 将大于自己的小数转换成下一位整数
 *        floor($value) 将一个数去除他的小数部分
 *        abs($value) 返回一个数的绝对值
 *        min($numbers…) 找出几个数值之间的最小值
 *        max($numbers…) 找出几个数值之间的最大值
 *        random() 获取随机
 *
 *      introspection 函数
 *        type-of($value) 返回一个值的类型 number，string，color，bool
 *        unit($number) 返回一个值的单位 单位
 *        unitless($number) 判断一个值是否带有带位 true/false
 *        comparable($number-1, $number-2) 判断两个值是否可以做加、减和合并 true/false
```

### 简述一下 Sass 和 Less？
答：它们都是CSS预处理器，用一种专门的编程语言，进行网页样式设计，然后再编译成正常的CSS文件。 
SASS是一种CSS的开发工具，提供了许多便利的写法，大大节省了设计者的时间，使得CSS的开发，变得简单和可维护。  
Less 是一门 CSS 预处理语言，它扩展了 CSS 语言，增加了变量、Mixin、函数等特性，使 CSS 更易维护和扩展。 
Less 可以运行在 Node 或浏览器端。  

### Sass 和 Less的区别是？
答：LESS和Sass之间的主要区别是他们的实现方式不同，LESS是基于JavaScript运行,所以LESS是在客户端处理  
Sass是基于Ruby的，是在服务器端处理的。很多开发者不选择LESS是因为LESS输出修改过的CSS到浏览器需要依赖于Javascript引擎，而Javascript引擎需要额外的时间来处理代码  

### 什么是SASS？
SASS（Syntactically Awesome Stylesheet）是一个CSS预处理器，有助于减少CSS的重复，节省时间。 它是更稳定和强大的CSS扩展语言，描述文档的样式干净和结构。

### 为什么要使用SASS？
它是预处理语言，它为CSS提供缩进语法（它自己的语法）。  
它允许更有效地编写代码和易于维护。  
它是包含CSS的所有功能的CSS的超集，是一个开源的预处理器，以 Ruby 编码。  
它提供了比平面CSS好的结构格式的文档样式。
它使用可重复使用的方法，逻辑语句和一些内置函数，如颜色操作，数学和参数列表。  

### 列出SASS的一些功能？
它是更稳定，强大，与CSS的版本兼容。  
它是超集的CSS和基于JavaScript。  
它被称为CSS的语法糖，这意味着它使用户更容易阅读或表达的东西更清楚。  
它使用自己的语法并编译为可读的CSS。  
你可以在更少的时间内轻松地编写CSS代码。  
它是一个开源的预处理器，被解释为CSS。  

### SASS的优点是什么？
它允许在编程结构中编写干净的CSS。  
它有助于编写CSS更快。  
它是CSS的超集，帮助设计师和开发人员更有效率和快速地工作。  
由于Sass兼容所有版本的CSS，我们可以使用任何可用的CSS库。  
可以使用嵌套语法和有用的函数，如颜色操作，数学和其他值。  

### SASS的缺点是什么？
开发人员需要时间了解此预处理器中存在的新功能。  
如果更多的人在同一个网站上工作，那么将使用相同的预处理器。 有些人使用Sass，有些人使用CSS直接编辑文件。 因此，它将变得难以与现场工作。  
有机会失去浏览器的内置元素检查器的好处。  

### 列出SASS支持的两种语法？
SASS支持两种语法，即 SCSS 和缩进语法。  
SCSS（Sassy CSS）是CSS语法的扩展，可以更容易地维护大型样式表，并且可以识别供应商特定的语法和许多CSS。 SCSS文件使用扩展名 .scss 。  
缩进是较旧的语法，有时仅称为 Sass 。 使用这种形式的语法，可以简洁地编写CSS。 SASS文件使用扩展名 .sass 。 

### 有多少种方法可以使用SASS？
您可以使用三种不同的方式使用SASS:  
作为命令行工具  
作为一个Ruby模块  
作为Rack启用框架的插件  

### SASS中的嵌套规则是什么？
嵌套是不同逻辑结构的组合。 使用SASS，我们可以将多个CSS规则相互组合。 如果使用多个选择器，则可以在另一个选择器中使用一个选择器来创建复合选择器。

### 如何在SASS中引用父选择器？
您可以使用＆amp; 字符选择父级选择器。 它告诉父选择器应该插入的位置。

### 如何在SASS中写入占位符选择器？
SASS使用 class 或 id 选择器支持占位符选择器。 在正常CSS中，这些用“＃"或“。"指定，但在SASS中，它们替换为“％"。

### 列出SASS上的不同类型的运算符？
有5种类型的运算符:  
数字运算符  
颜色运算符  
字符串运算符  
布尔运算符  
列表运算符  

### 什么是数字运算？
它允许诸如加法，减法，乘法和除法的数学运算。

### 什么是彩色运算？
它允许使用颜色分量和算术运算。

### 什么是列表运算？
列表表示使用逗号或空格分隔的一系列值。

### 什么是布尔运算？
您可以使用and、or和not（与或非）对Sass脚本执行布尔运算。

### SASS中的括号是什么？
括号是一对标记，通常用圆括号（）或方括号[]来标记，这提供了影响操作顺序的符号逻辑。

### 什么是SASS中的插值？
它使用＃{} 语法提供选择器和属性名称中的SassScript变量。 您可以在花括号中指定变量或属性名称。

### 什么是可变默认值？
您可以通过向变量值的结尾添加！default 标志来设置变量的默认值。如果值已经分配给变量，则不会重新分配该值。

### 什么是导入指令？
它直接采用文件名导入，所有导入的文件将合并到一个单一的CSS文件。

### 什么是媒体指令？
它将样式规则设置为不同的媒体类型。

### 什么是扩展指令？
它用于共享选择器之间的规则和关系。 它可以在一个类中扩展所有其他类样式，也可以应用自己的特定样式。

### 什么是根指令？
它是一个嵌套规则的集合，它能够在文档的根节点创建样式块。

### 什么是@if指令？
它用于基于表达式求值的结果选择性地执行代码语句。

### 什么是@else if指令？
@else if语句与@if指令一起使用，每当@if语句失败，则尝试@else if语句，如果它们也失败，则执行@else。

### 什么是@for指令？
它允许您在循环中生成样式。 计数器变量用于设置每次迭代的输出。

### 什么是@each指令？
在@each指令中，定义了一个包含列表中每个项目的值的变量。

### 什么是@mixin指令？
它用于定义mixin，其中包含可选的mixin名称之后的变量和参数。

### 什么是@include指令？
它用于在文档中包含mixin，由mixin定义的样式可以包含在当前规则中。

### 什么是mixin 参数?
SassScript值可以作为mixin中的参数，当mixin包含并在mixin中作为变量使用时，可以将其作为参数。

### 列出两种类型的mixin参数？
有两种类型的mixin参数:

关键字参数

可变参数

### 什么是关键字参数？
它用于在mixin中包含参数。 命名的参数可以按任何顺序传递，参数的默认值可以省略。

### 什么是可变参数？
变量参数用于将任意数量的参数传递给mixin。 它包含传递给函数或mixin的关键字参数。

### 什么是函数指令？
使用函数指令，可以创建自己的函数，并在脚本上下文中使用它们，或者可以使用任何值。

### 什么是SASS输出样式？
SASS生成的CSS文件由反映文档结构的默认CSS样式组成。 默认的CSS样式很好，但可能不适合所有情况。

### 什么是嵌套CSS样式？
嵌套样式是SASS的默认样式。 这种方式的样式在处理大型CSS文件时非常有用。

### 什么是扩展CSS样式？
在扩展输出样式中，每个属性和规则都有自己的线。 与嵌套CSS样式相比，它需要更多的空间。

### 什么是紧凑的CSS样式？
紧凑的CSS风格竞争力比Expanded和Nested占用更少的空间。 它主要关注选择器而不是其属性。

### 什么是压缩CSS样式？
与所有其他样式相比，压缩的CSS样式占用最少的空间。 它仅提供空格，以在文件末尾分隔选择器和换行符。  

### SASS缩进语法的主要特点是什么？
它使用缩进而不是 {和} 来分隔块。  
要分隔语句，它使用换行符而不是分号（;）。  
属性声明和选择器必须放在自己的行上， {和} 中的语句必须放在 >和缩进。  

### 有多少种方法可以声明CSS属性？
CSS属性可以通过两种方式声明:  
属性可以声明为类似于CSS但没有分号（;）。  
colon（:）将以每个属性名称为前缀。  

### 什么是写@mixin和@include指令的速记？
您可以使用= for @mixin指令和+ for @include指令，这需要更少的键入，使您的代码更简单，更容易阅读。

### 每当SASS文件更改时，使用哪个命令来观察文件并更新CSS？
sass --watch C:\\ ruby \\ lib \\ sass \\ style.scss:style.css

### 什么是SASS的注释？
注释占用整行并包围嵌套在它们下面的所有文本，它们是基于行的缩进语法。

### 哪个命令用于从命令行运行SASS代码？
sass input.scss output.css

### 样式表的字符编码的CSS规范是什么？
首先它检查Unicode字节，下一个 @charset 声明，然后检查Ruby字符串编码。  
接下来，如果未设置任何内容，则会将字符集编码视为。  
使用 @charset 声明显式地确定字符编码。 只需在样式表的开头使用“@charset encoding name"，SASS将假设这是给定的字符编码。  
如果SASS的输出文件包含非ASCII字符，那么它将使用 @charset 声明。  

### 有多少种注释类型？
Sass支持两种类型的注释:  
多行注释 - 使用/ *和* /写入。 多行注释保存在CSS输出中。  
单行注释 - 这些是使用 // 和注释写成的。 单行注释不会保留在CSS输出中。  

### 什么是交互式shell？
它使用命令行评估SassScript表达式。 您可以使用sass命令行和 - i 选项运行shell。

### 什么是@debug指令？
它检测错误并将SassScript表达式值显示到标准错误输出流。

### 什么是@error指令？
它将SassScript表达式值显示为致命错误