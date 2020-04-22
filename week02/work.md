## s随堂练习 ##

* 编写带括号的四则运算产生式
```

// 可递归
<Number> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

<DecimalNumber> ::= "0" |  (("1" | "2" | ..... | "9") <Number>* )
<DecimalNumber> ::= /0|[1-9][0-9]*/ // 正则文法

<PrimaryExpression> ::= <DecimalNumber> |
    "(" <LogicalExpression> ")"

<MultiplicativeExpression> ::= <PrimaryExpression> |
    <MultiplicativeExpression> "*" <PrimaryExpression> |
    <MultiplicativeExpression> "/" <PrimaryExpression>

<AdditiveExpression> ::= <MultiplicativeExpression> |
    <AdditiveExpression> "+" <MultiplicativeExpression> |
    <AdditiveExpression> "-" <MultiplicativeExpression>

<LogicalExpression> ::= <AdditiveExpression> |
    <LogicalExpression> "||" <AdditiveExpression> |
    <LogicalExpression> "&&" <AdditiveExpression>

```

* 尽可能寻找你知道的计算机语言，尝试把它们分类
```

类型划分|强|弱
:-:|:-:|:-:
动态|Python|js、PHP
静态|Java|(C、C++)

```

## 课后作业 ##

* 写一个正则表达式 匹配所有 Number 直接量
```

/^-?\d+$|^(-?\d+)(\.\d+)?$|^0[bB][01]+$|^0[oO][0-7]+$|^0[xX][0-9a-fA-F]+$/g

```

* 写一个 UTF-8 Encoding 的函数
```

function encodeUtf8(str)
{
    return str.split('').map(char => `\\u${char.charCodeAt().toString(16)}`).join('')
}

```

* 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号
```

/(?:[^'\n\\\r\u2028\u2029]|\\(?:['"\\bfnrtv\n\r\u2028\u2029]|\r\n)|\\x[0-9a-fA-F]{2}|\\u[0-9a-fA-F]{4}|\\[^0-9ux'"\\bfnrtv\n\\\r\u2028\u2029])*/

```