# 5. 标志

标志也叫修正符，因为它可以用来修改表达式的搜索结果。这些标志可以任意打乱顺序的组合使用，它也是整个正则表达式的一部分。

|标志|描述|
|:----:|----|
|i|忽略大小写。|
|g|全局搜索。|
|m|多行修饰符：锚点元字符 `^` `$` 工作范围在每行的起始。|

## 5.1 忽略大小写 (Case Insensitive)

修饰语 `i` 用于忽略大小写。

例如，表达式 `/The/gi` 表示在全局搜索 `The`，但最后的 `i` 将其条件修改为忽略大小写，等价于 `(t|T)he\g`，`g` 表示全局搜索。

<pre>
"The" => <a href="#"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[在线练习](https://regex101.com/r/dpQyf9/1)

<pre>
"/The/gi" => <a href="#"><strong>The</strong></a> fat cat sat on <a href="#"><strong>the</strong></a> mat.
</pre>

[在线练习](https://regex101.com/r/ahfiuh/1)

## 5.2 全局搜索 (Global search)

修饰符 `g` 常用于执行一个全局搜索匹配，它不会在遇到第一个匹配的时候就停止返回匹配，而是返回文本中的全部匹配。

例如，表达式 `/.(at)/g` 表示搜索 任意字符（除了换行）+ `at`，并返回全部结果。

<pre>
"/.(at)/" => The <a href="#"><strong>fat</strong></a> cat sat on the mat.
</pre>

[在线练习](https://regex101.com/r/jnk6gM/1)

<pre>
"/.(at)/g" => The <a href="#"><strong>fat</strong></a> <a href="#"><strong>cat</strong></a> <a href="#"><strong>sat</strong></a> on the <a href="#"><strong>mat</strong></a>.
</pre>

[在线练习](https://regex101.com/r/dO1nef/1)

## 5.3 多行修饰符 (Multiline)

多行修饰符 `m` 常用于执行一个多行匹配。

像之前介绍的 `(^,$)` 用于检查格式是否是在待检测字符串的开头或结尾。但我们如果想要它在每行的开头和结尾都生效，我们需要用到多行修饰符 `m`。

例如，表达式 `/at(.)?$/gm` 表示小写字符 `a` 后跟小写字符 `t` ，末尾可选除换行符外任意字符。根据 `m` 修饰符，现在表达式匹配每行的结尾。

<pre>
"/.at(.)?$/" => The fat
                cat sat
                on the <a href="#"><strong>mat.</strong></a>
</pre>

[在线练习](https://regex101.com/r/hoGMkP/1)

<pre>
"/.at(.)?$/gm" => The <a href="#"><strong>fat</strong></a>
                  cat <a href="#"><strong>sat</strong></a>
                  on the <a href="#"><strong>mat.</strong></a>
</pre>

[在线练习](https://regex101.com/r/E88WE2/1)