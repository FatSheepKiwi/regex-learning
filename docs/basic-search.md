# 1. 基本匹配

在这种情况下，正则表达式其实就是在执行搜索`搜索内容`的格式，它由一些字母和数字组合而成。
例如：一个正则表达式 `the`，它表示一个规则或者模式（pattern）：从左到右，由字母`t`开始，接着是`h`，再接着是`e`。

<pre>
"the" => The fat cat sat on <a><strong>the</strong></a> mat.
</pre>

[在线练习](https://regex101.com/r/dmRygT/1)

正则表达式`the`匹配字符串`the`。它逐个字符的与输入的正则表达式做比较。

正则表达式是**大小写敏感**的，所以`The`不会匹配`the`。

<pre>
"The" => <a><strong>The</strong></a> fat cat sat on the mat.
</pre>

[在线练习](https://regex101.com/r/1paXsy/1)