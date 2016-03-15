# ydiff - 结构化的程序比较
[ydiff](https://github.com/yinwang0/ydiff) 是我的一个开源项目，用以探索一种全新的程序比较以及版本控制系统。

也许我根本不应该给它起名叫“ydiff”，让人感觉它只不过是对 diff 的微小改进。然而，ydiff 跟 diff 是有本质区别的。它们的区别在于，diff 只是对程序进行基于“文本”的对比，它根本不对程序进行 parse。而 ydiff 含有完整的针对程序语言的 parser，在得到了 AST 之后，才对 AST 进行“结构化的比较”。

这种结构化的程序比较，不但可以避免文件里的“空白字符”引起的肤浅区别，而且可以根据程序的结构，进行更加有意义的对比。比如，ydiff 不会认为字符串 "1000" 和数字 1000 的区别只是多了一对引号。ydiff 在比较函数的时候，首先寻找名字相同的函数，而不只是对相同位置的函数进行无谓的对比。

ydiff 含有 C++, JavaScript 和 Lisp 的 parser。这些 parser，包括用于支持这些 parser 的库代码，都是我自己完成的。ydiff 不含有任何第三方代码。ydiff 的 parser 技术不依赖于任何第三方工具（比如 ANTLR 或者 YACC）。

### 界面

跟普通 diff 程序的输出不一样，ydiff 生成美观的含有 JavaScript 的 HTML 文件，可以直接使用浏览器浏览，并且可以嵌入其它网页，比如像下面这样：


<html>
<frameset cols="100%">
  <frame src="http://www.yinwang.org/resources/mk1-mk2.html">
</frameset>
</html>
