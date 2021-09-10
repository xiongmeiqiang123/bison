## 安装 lex bison gcc
mac 上自带

## 词法分析器
需先上手flex，不分析词法，则分析语法没有意义。

lex：词法分析器生成器
将输入分隔成有意义的单元，然后找出这些单元之间的关系
使用lex/flex制作词法分析器
lex将正则表达式转变为词法分析程序能够用来极快地扫描输入文本的形式，而且速度不依赖于词法分析程序尝试匹配的表达式的数量。
速度远于手写的词法分析器


test.l -> 【flex】-> lex.yy.c -> 【gcc】 -> a.out（可执行文件）

### 介绍flex的代码结构
```
定义(definations)
%%
规则(rules)
%%
代码(user code)
```
flex的代码分为三个部分，由%%分割

* 新手框架
```
%{
    

%}

%%

%%
int main(int argc, char **argv)
{
    
  yylex()
  return 0;
}
int yywrap()
{
    
	return 1;
}
```
** 第一部分：%{%} 
在这个部分可以使用C语言代码进行预处理，例如使用#include<stdio.h>，或是定义宏、常量等


** 第二部分
是重点

** 第三部分
添加了两个函数
main函数，为了编译为C语言
yylex函数调用：其实会由第二部分我们写入的匹配规则自动生成，其实就是由lex产生的词法分析程序
yywarp函数：约束函数，返回1代表扫描结束


## 2.3【第二部分的编写】
# bison
