# 南京大学ACM/ICPC代码库

如果任何人有好的代码，请与我们分享，并向我发起pull request！

## 重要注意事项及已知的bug

* 由于listings宏包和XeCJK之间衔接的问题，代码注释的中英文混排可能会出现一些非预期的问题，例如
        /* 将x赋值为1 */

    可能会显示为

        /* 将赋值为x1 */

    为解决这个问题，可以在英文单词后加一个空格: /* 将x 赋值为1就可以了 */
    
* 希望贡献代码的同学可以使用git标准的合作开发方法，在添加了代码后向该项目发起pull request。如果你只是简单地发现bug或者想在库中添加一些代码，可以将相关的内容直接在issue中写出来。希望通过我们的合作，能让代码库越来越完善。

## 代码库结构

所有代码都应当使用UTF-8编码。

代码库整理在src目录下，每个大分类建一个目录，目录的名称就是显示在最终排版代码库中的名称(可以使用中文，也可以包含空格等字符)，例如“数据结构”，“图论”等等。如果需要对这些项目人工制定顺序，可以在目录的名称最前面添加数字，数字后有一个空格，例如“1 数据结构”。排版时会按照这个数字顺序排序(数字允许重复，当数字重复时按照字典顺序排序)，数字不会被显示在代码库中。有数字的目录在排版时，会排在没有数字代码的前面。每一个目录都是LaTeX里的section，例如

    "其他", "1 图论", "2 数据结构"
    
排版后将会生成

    "图论", "数据结构", "其他"。

每个目录(大分类)中都包含一些具体的代码，例如“最小费用最大流.cpp”，“最小费用最大流(dinic).cpp”等，文件名将作为代码库章节的标题。同样也可以用数字来决定每一个代码安排的顺序。每一个代码都是LaTeX里的一个subsection。

简单地说，只要将代码的简单描述作为文件名，放在src下的每一个子目录中，然后make编译就能得到pdf版的代码库。

## 代码库规范

我们推荐使用Google的编程规范，使代码库有一致的风格。英文原版的[链接](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml)供参考。具体与我们比较直接相关的是命名的规范：

* 变量名应使用小写，并能推断出名称的含义，例如prime_count, current等。使用缩写时应避免歧义。
* 结构体、类名应用混合大小写单词拼接，其中单词首字母大写，例如Node, WeightedGraph。
* 函数的名称应该混合大小写，例如AddEntry, SolveLP。
* 因为我们的程序相对独立，命名规范不用太过严格，只要在同程序中保持一致即可。

代码风格规范：

* 每行不能超过80个字符。过长的行应该想办法断成多行，避免过多层循环、条件的嵌套。如何断行请参考英文版的资料，其中有定义、表达式等断行规则的详细说明。
* 不要使用tab，统一使用2个空格作为缩进。在我们的代码库中，tab长度为2。
* 所有左大括号都不新起一行。
* 在二元运算符的左右都有空格；逗号分隔符右边有一个空格，程序中不应用多余的空格。例如a += f(b, c);。为了排版的美观，可以对这个规则做适当的变通，例如以下的写法都是可以的：

        x = -5;
        ++x;
        if (x && !y)
        v = w * x + y / z;
        v = w*x + y/z; 

还有一些基本原则：

* 变量尽量只在局部起作用(减少作用域)，这避免了引用错变量的麻烦，变量应该在定义时初始化。
* 警惕使用自增和自减运算符。
* 多使用const修饰变量，减少错误的可能。
* 在不同的场合使用0, 0.0, NULL, '\0'减少程序的歧义。
* 使用sizeof(变量)而不是sizeof(类型)。

为了代码库的精确、好用，我们还有一些额外的要求，在整理代码库时可做参考：

* 在每一个程序的头部都应该以注释的方式描述程序的行为：参数如何输入、对输入有什么特别的要求、输出什么。如果有可能，应该大致描述算法的实现，以及中间结果有哪些可能可以利用。
* 说明每一个函数依赖其他哪些函数、类或结构体，这样就可以避免在很大的代码库中录入多余的代码。

## 代码库编译方法

* 编译环境: Linux, texlive xelatex (windows未测试)
* 编译方法: 使用make工具编译。由于每一行代码的fingerprint使用了label，在添加新的代码后需要编译两次(Makefile中默认编译两次)
* 依赖: xelatex, 在Linux系统中安装字体: 华文细黑、楷体、Liberation Mono

