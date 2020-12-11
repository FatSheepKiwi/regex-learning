
# 6. 匹配规则

正则表达式有贪婪匹配(Greedy matching)与惰性匹配(azy matching)的区别。

正则表达式默认采用贪婪匹配模式，在该模式下正则引擎会尽可能匹配长的子串。我们可以使用 `?` 将贪婪匹配模式转化为惰性匹配模式。

<pre>
"/(.*at)/" => <a href="#"><strong>The fat cat sat on the mat</strong></a>. </pre>

[在线练习](https://regex101.com/r/AyAdgJ/1)

<pre>
"/(.*?at)/" => <a href="#"><strong>The fat</strong></a> cat sat on the mat. </pre>

[在线练习](https://regex101.com/r/AyAdgJ/2)