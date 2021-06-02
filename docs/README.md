# 正则表达式笔记

> 用一次，学一次，忘一次。

为了能够扎实的学会使用正则表达式，系统性的整理知识，梳理笔记非常有必要。这也是这份Doc的目的。

## 什么是正则表达式？

> 正则表达式是一组由字母和符号组成的特殊文本，它可以用来从文本中找出满足你想要的格式的句子。

一个正则表达式是一种从左到右匹配主体字符串的模式。
“Regular expression”这个词比较拗口，我们常使用缩写的术语“regex”或“regexp”。
正则表达式可以从一个基础字符串中根据一定的匹配模式替换文本中的字符串、验证表单、提取字符串等等。

想象你正在写一个应用，然后你想设定一个用户命名的规则，让用户名包含字符、数字、下划线和连字符，以及限制字符的个数，好让名字看起来没那么丑。
我们使用以下正则表达式来验证一个用户名：

<br/><br/>

<p align="center">
  <img src="./img/regexp-cn.png" alt="Regular expression">
</p>

以上的正则表达式可以接受 `john_doe`、`jo-hn_doe`、`john12_as`。
但不匹配`Jo`，因为它包含了大写的字母而且太短了。

## 正则的历史

虽然现在正则表达式在前端、爬虫等领域大放异彩，被无数程序员奉为神器，但是在最早的时候，正则并不是为了满足搜索功能而被发明的，它的想法并非起源于计算机科学领域，而是从神经科学中起源的。

1940年，Warren McCulloch和Walter Pitts将神经系统中的神经元描述成小而简单的自动控制元，用于解释人类神经系统工作原理。他们两位也是人工神经网络的提出者。在1951 年,一位名叫Stephen Kleene的数学科学家，他在McCulloch和Pitts早期工作的基础之上，发表了一篇题目是《神经网事件的表示法》的论文，利用称之为正则集合的数学符号来描述此模型，引入了正则表达式的概念。

再后来，1968年，数学家并且也是Unix的主要开发人员之一的肯·汤普森（是真的大佬，他还发明了Golang）在Unix系统中实现了在文本编辑器中的正则表达式功能。这是regex进入计算机世界的起点。自此以后，正则表达式被广泛地应用于各种 Unix 或类 Unix 系统的工具中。

Unix的正则表达式在经过时间的检验后，形成了`POSIX 规范的正则表达式`。后来又出现了`Perl 正则表达式`。Henry Spencer于1986年1月19日发布的Perl版本中也实现了正则。1997年夏天，由Philip Hazel用C语言对它进行了加强，成为了一个广为使用的正则库，也就演化成了PCRE（Perl 兼容正则表达式，Perl Compatible Regular Expressions）。`PCRE`的语法比`POSIX`正则表达式和许多其他正则表达式库都强大和灵活。许多著名的开源程序（例如 Apache 和 Nginx HTTP 服务器以及 PHP 和 R 脚本语言）都包含 PCRE 库。

## Playground

一个非常Fancy的验证正则的网站：[Regex101](https://regex101.com/)。笔记中的在线练习也是跑在这个网站上的。

## Reference

1. [Learn Regex](https://github.com/ziishaned/learn-regex)
2. [翻译 Learn Regex the easy way](https://github.com/cdoco/learn-regex-zh)
3. [常用正则表达式](https://github.com/cdoco/common-regex)
4. [Regex tutorial — A quick cheatsheet by examples](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
5. [history of Regular Expression](https://medium.com/@minisha.mit/regular-expression-part-1-8d75128f6274)
6. [正则表达式30分钟入门教程](https://deerchao.cn/tutorials/regex/regex.htm)
