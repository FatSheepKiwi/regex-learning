# 2. 元字符

元字符可以说是正则表达式的基石。它不代表他们本身的“表面”意思，而是具有特殊的含义。同时，使用方括号`[]`包围的一些元字符可以表达特殊的含义。

我们经常使用的一些元字符的介绍：

|元字符|描述|
|:----:|----|
|`.`|句号匹配任意单个字符除了换行符`\n`。|
|`[ ]`|字符种类。匹配方括号内的任意字符。|
|`[^ ]`|否定的字符种类。匹配**除了**方括号里的任意字符|
|`*`|匹配 >= 0个重复的在 `*` 号之前的字符。|
|`+`|匹配 >= 1个重复的 `+` 号前的字符。
|`?`|标记 `?` 之前的字符为可选，也就是0次或1次。|
|`{n,m}`|有`n <= num <= m`, 匹配num次大括号之前的字符或字符集。|
|`(xyz)`|字符集，匹配与 `xyz` 完全相等的字符串。|
|&#124;|或运算符，匹配符号前或后的字符。|
|&#92;|转义字符，用于匹配一些保留的字符 <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|
|`^`|从行开始开始匹配。|
|`$`|匹配到行末端。|

## 2.1 点运算符 `.`

`.`是元字符中最简单的例子。

`.`匹配任意单个字符，但不匹配换行符。

例如，表达式`.ar`匹配任意一个字符，且它的后面跟着的是`a`再是`r`的字符串。

<pre>
".ar" => The <a href="#"><strong>car</strong></a> <a href="#"><strong>par</strong></a>ked in the <a href="#"><strong>gar</strong></a>age.
</pre>

[在线练习](https://regex101.com/r/xc9GkU/1)

## 2.2 字符集 `[]`

字符集也叫做字符类。

方括号用来划定一个字符集，在方括号中使用连字符 `-` 来指定字符集的范围。

在方括号中的字符集不关心顺序。例如，表达式`[Tt]he` 匹配 `the` 和 `The`，与 `[tT]he` 有相同的效果。

<pre>
"[Tt]he" => <a href="#"><strong>The</strong></a> car parked in <a href="#"><strong>the</strong></a> garage.
</pre>

[在线练习](https://regex101.com/r/2ITLQ4/1)

方括号的句号就表示句号，不再是元字符 `.` ，其他元字符的情况也类似。表达式 `ar[.]` 就是匹配 `ar.`字符串。

<pre>
"ar[.]" => A garage is a good place to park a c<a href="#"><strong>ar.</strong></a>
</pre>

[在线练习](https://regex101.com/r/wL3xtE/1)

### 2.2.1 否定字符集

一般来说 `^` 表示一个字符串的开头，但它用在一个方括号的开头的时候，它表示这个字符集是否定的，也就是匹配的时候不需要这个字符集中的字符。

例如，表达式 `[^c]ar` 匹配一个后两位是 `ar` 但是开头是除了 `c` 的任意字符串。

<pre>
"[^c]ar" => The car <a href="#"><strong>par</strong></a>ked in the <a href="#"><strong>gar</strong></a>age.
</pre>

[在线练习](https://regex101.com/r/nNNlq3/1)

## 2.3 重复 `+`，`*` and `?`

元字符 `+`，`*` 以及 `?` 的，用来指定匹配它们之前子模式的次数。这些元字符在不同的情况下有着不同的意思。

### 2.3.1 `*` 号

`*` 号匹配在 `*` 之前的字符出现**大于等于0次**，即可以没有，可以只有一次，多次也可以。

例如，表达式 `a*` 匹配0或更多个以 `a` 开头的字符。表达式 `[a-z]*` 则可以匹配一个行中所有以小写字母开头的字符串。

<pre>
"[a-z]*" => T<a href="#"><strong>he</strong></a> <a href="#"><strong>car</strong></a> <a href="#"><strong>parked</strong></a> <a href="#"><strong>in</strong></a> <a href="#"><strong>the</strong></a> <a href="#"><strong>garage</strong></a> #21.
</pre>

[在线练习](https://regex101.com/r/7m8me5/1)

`*`字符和`.`字符搭配使用时，即 `.*` ，可以匹配所有的字符。

`*`和表示匹配空格的符号`\s`连起来用，如表达式`\s*cat\s*`匹配0或更多个空格开头和0或更多个空格结尾的cat字符串。

<pre>
"\s*cat\s*" => The fat<a href="#"><strong> cat </strong></a>sat on the con<a href="#"><strong>cat</strong></a>enation.
</pre>

[在线练习](https://regex101.com/r/gGrwuz/1)

### 2.3.2 `+` 号

`+` 号匹配 `+` 号之前的字符出现 >=1 次，也就是至少得有1次。

例如表达式 `c.+t` 匹配以首字母 `c` 开头以 `t` 结尾，中间跟着至少一个字符的字符串。

<pre>
"c.+t" => The fat <a href="#"><strong>cat sat on the mat</strong></a>.
</pre>

[在线练习](https://regex101.com/r/Dzf9Aa/1)

### 2.3.3 `?` 号

在正则表达式中元字符 `?` 标记在符号前面的字符为可选，即出现0或1次。

例如，表达式 `[T]?he` 匹配字符串 `he` 和 `The`。

<pre>
"[T]he" => <a href="#"><strong>The</strong></a> car is parked in the garage.
</pre>

[在线练习](https://regex101.com/r/cIg9zm/1)

<pre>
"[T]?he" => <a href="#"><strong>The</strong></a> car is parked in t<a href="#"><strong>he</strong></a> garage.
</pre>

[在线练习](https://regex101.com/r/kPpO2x/1)

## 2.4 `{}` 号

在正则表达式中 `{}` 是一个量词，常用来限定一个或一组字符可以重复出现的次数。

例如， 表达式 `[0-9]{2,3}` 匹配最少2位最多3位 `0~9` 之间的数字。

<pre>
"[0-9]{2,3}" => The number was 9.<a href="#"><strong>999</strong></a>7 but we rounded it off to <a href="#"><strong>10</strong></a>.0.
</pre>

[在线练习](https://regex101.com/r/juM86s/1)

我们可以省略第二个参数，此时表示没有上限。例如，`[0-9]{2,}` 匹配至少两位 0~9 的数字。

<pre>
"[0-9]{2,}" => The number was 9.<a href="#"><strong>9997</strong></a> but we rounded it off to <a href="#"><strong>10</strong></a>.0.
</pre>

[在线练习](https://regex101.com/r/Gdy4w5/1)

如果逗号也省略掉则表示重复固定的次数。例如，`[0-9]{3}` 匹配3位数字

<pre>
"[0-9]{3}" => The number was 9.<a href="#"><strong>999</strong></a>7 but we rounded it off to 10.0.
</pre>

[在线练习](https://regex101.com/r/Sivu30/1)

## 2.5 `(...)` 特征标群

特征标群，又称为捕获组。是一组写在 `(...)` 中的子模式。`(...)` 中包含的内容将会被看成一个整体，和数学中小括号 `()` 的作用是相同的。

例如, 表达式 `(ab)*` 匹配连续出现 0 或更多个 `ab`。如果没有使用 `(...)` ，那么表达式 `ab*` 将匹配连续出现 0 或更多个 `b` 。再比如之前说的 `{}` 是用来表示前面一个字符出现指定次数。但如果在 `{}` 前加上特征标群 `(...)` 则表示整个组内的字符重复N次。

<pre>
"(co)*" => The <a href="#"><strong>coco</strong></a>nut <a href="#"><strong>co</strong></a>mes from palm tree.
</pre>
[在线练习](https://regex101.com/r/G1Jtj3/1)


我们还可以在 `()` 中用或字符 `|` 表示或。例如，`(c|g|p)ar` 匹配 `car` 或 `gar` 或 `par`.

<pre>
"(c|g|p)ar" => The <a href="#"><strong>car</strong></a> is <a href="#"><strong>par</strong></a>ked in the <a href="#"><strong>gar</strong></a>age.
</pre>

[在线练习](https://regex101.com/r/tUxrBG/1)

## 2.6 `|` 或运算符

或运算符就表示或，用在判断条件中。

例如 `(T|t)he|car` 匹配 `(T|t)he` 或 `car`。

<pre>
"(T|t)he|car" => <a href="#"><strong>The</strong></a> <a href="#"><strong>car</strong></a> is parked in <a href="#"><strong>the</strong></a> garage.
</pre>

[在线练习](https://regex101.com/r/fBXyX0/1)

## 2.7 转码特殊字符 `\`

反斜线 `\` 在表达式中用于转码紧随其后的字符。比如 `{ } [ ] / \ + * . $ ^ | ?` 这些特殊字符，如果想要匹配这些特殊字符则要在其前面加上反斜线 `\`。

例如 `.` 是用来匹配除换行符外的所有字符的。如果想要匹配句子中的 `.` 则要写成 `\.` 以下这个例子 `\.?`是选择性匹配`.`

<pre>
"(f|c|m)at\.?" => The <a href="#"><strong>fat</strong></a> <a href="#"><strong>cat</strong></a> sat on the <a href="#"><strong>mat.</strong></a>
</pre>

[在线练习](https://regex101.com/r/DOc5Nu/1)

## 2.8 锚点 `^` `$`

在正则表达式中，想要匹配每一行中，处于开头或结尾的字符串就要使用到锚点。`^` 指定开头，`$` 指定结尾。

### 2.8.1 `^` 号

`^` 用来检查匹配的字符串是否在所匹配字符串的开头。

例如，在 `abc` 中使用表达式 `^a` 会得到结果 `a`。但如果使用 `^b` 将匹配不到任何结果。因为在字符串 `abc` 中并不是以 `b` 开头。

例如，`^(T|t)he` 匹配以 `The` 或 `the` 开头的字符串。

<pre>
"(T|t)he" => <a href="#"><strong>The</strong></a> car is parked in <a href="#"><strong>the</strong></a> garage.
</pre>

[在线练习](https://regex101.com/r/5ljjgB/1)

<pre>
"^(T|t)he" => <a href="#"><strong>The</strong></a> car is parked in the garage.
</pre>

[在线练习](https://regex101.com/r/jXrKne/1)

### 2.8.2 `$` 号

同理于 `^` 号，`$` 号用来匹配字符是否是要匹配的字符串中的最后一个。

例如，`(at\.)$` 匹配以 `at.` 结尾的字符串。

<pre>
"(at\.)" => The fat c<a href="#"><strong>at.</strong></a> s<a href="#"><strong>at.</strong></a> on the m<a href="#"><strong>at.</strong></a>
</pre>

[在线练习](https://regex101.com/r/y4Au4D/1)

<pre>
"(at\.)$" => The fat cat. sat. on the m<a href="#"><strong>at.</strong></a>
</pre>

[在线练习](https://regex101.com/r/t0AkOd/1)