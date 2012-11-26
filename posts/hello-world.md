---
title: Hello, World!
date: '2012-11-26'
description: Getting started with ruhoh
categories: Life
tagline: The world of ruhoh
tags: [abc, defg, hijkl]
---
# 第0课：导论

本系列教程面向没有计算机语言学习经验的初学者。本教程不是一本**专业的C++书籍**，也不是一本**C++快速入门手册**，而是一本杂文：我们不会讨论全部的C++语法（这种东西可以考虑C++之父*Bjarne Stroustrup*的*The C++ Programming Language*），我们只讨论一些基础但是十分**有意思**的东西;我们还会讨论一些**编程相关但是却和C++无关**的东西，非常重要，相信这个星球上没有几本关于C++的书会讨论这些东西的。

>你可以把本教程当作一个科普读物，只不过内容比之高深一点

我们的目标是：当你阅读完本教程并完成相关的练习之后，你能初步掌握少部分C++知识（相比于复杂到恐怖的C++来说）。你可以深入学习一些**产品向**的东西/开始研究ACM之类的题目。所以，如果你想通过本教程应付考试，或者开发点小作品，还是趁早离开吧。

在开始第1课之前，您应当准备好以下的一些东西:

1. 一个可以使用的C++工作环境。[**请按本教程配置**](cpp-tools-configure.html)以确保你的工作环境能跟上时代潮流。C++是一门不断更新的语言，使用古老的产品如1998年的*Visual C++ 6.0*来学习本教程只会让你浪费很多时间。同时，[*AcceptNoob.com*](http://acceptnoob.com)也不欢迎古老的技术。
2. 一本专业的C++书籍。本教程的目标之一便是降低新人们的阅读难度。尽管我们推荐你在阅读完本教程后再开始相关阅读，但是如果有点疑问的话有本书参考参考还是比较好的。
3. 较高的自主学习能力。我们并不提供，或者说难以提供人工服务。如果你在阅读过程中遇到许多困难，就只能自己使用**搜索引擎**之类的东西了。不过想必在经过高中三年的磨练之后，这点素质你还是有的。

下面开始和我们一起探索神秘的C++世界吧：
[**传送门**](lesson1.html)

# 第1课：Hello, World!

什么是"Hello World"呢？“你好，世界“？自然不可能，它是指每一种计算机语言中的最基本的一段程序——在屏幕上输出一段话，"Hello, World!"。关于它的维基百科条目，[请戳这里](http://zh.wikipedia.org/wiki/Hello_World)。

这是一段基础的C++的Hello World程序。

	#include <iostream>
	using namespace std;
	
	int main () {
	    cout << "Hello, World!" << endl;
	    return 0;
	}

很简单，不是吗？好吧我知道这里总共有6行代码，而每行代码对于大家可能都难以理解。我来做点基本的解释吧。
解释就是：

	#include <iostream>
	using namespace std;
	
	int main () {
	    return 0;
	}
这五行代码都是每一个C++程序所必须拥有的。

>大家还记得在初中的时候化学老师告诉我们化学反应有四大基本反应类型：化合、分解、置换和复分解。天真的少年们认真的记着，直到高一化学给他们射了一箭。

所以，上面某句话会迟早会被被推翻。

好吧大家都是会英语的，include的意思是包含，"#include &lt;iostream&gt;"是指包含一个叫做iostream的东西。iostream，I/O Stream(I/O=>Input/Output)，输入输出流。这个流嘛，可以理解为那个细胞间信息传递的那个信息流（好吧我生物很烂，有错勿吐槽），iostream嘛，就是和屏幕交互的一个输入输出系统。这句话就是——**启用输入输出系统！**

第二行比较复杂，大家就这么将就着用着，在每个程序开头敲一行而已。

main是主要的意思。int main () { }定义了一个主函数，所有C++的代码，至少你写出来的代码都是由它开始执行的。流程图或者类似物遇到过没？main函数就是入口。

C++中的每一条语句都要由一个分号结束。比如"using namespace std;","cout << "Hello, World" << endl;","return 0;"。分号之前的就是语句。"return 0;"是一个操作系统相关的规范，即一个程序正常结束以后必须返回一个整数值0。至于return和返回值之间的关系，下节课再说。

所以大家都知道所谓cout就是这个程序的核心了（废话，只有这里有"Hello, World!"嘛！）。那么我们来简单的介绍一下这个cout：

cout << sth 代表着输出某个东西。当然这个东西必须是存在的，或者说编译器可以理解的，如一个字符，'A'，一个字符串"Hello, World"，一个整数，123，一个可以输出的变量，如endl（end line）。cout后面可以跟无数个输出的参数，只要别打一个分号结束该语句就行了。

	cout << 123 << ' ' << "Hello, World!" << endl;
	cout << 345 << ' ' << "Bye bye!" << endl;
	
好吧，晕了吧？慢慢理解。先说说字符、字符串和整数。

字符就是字符，不过必须由''括起来。字符串就是一个由""括起来的一段话，括起来的内容就是它的值。整数就是123456什么的，－789也可以，还可以8进制（用0开头），如0123，或者16进制（用0x/0X开头），如0x123。当然输出的都是十进制。

>尝试输出123, 0123, 0x123并换行，在计算器下验证输出结果

变量，其实就是一个能存储东西的标识符，类似x，不过值是可以变化的。

>endl是啥我还真没研究过，不过想必是一个系统定义的，行为和变量类似（或者就是变量的）玩意。当然它不止是换行，只是看起来像换行。

所以，定义变量就是“设x = 123; x = 456; cout << x << endl;”？怎么可能。每个变量都要有自己的类型，你要这样声明它：

	/*
	 * Type var;
	 * Type var1, var2;
	 * 以整数为例
	 */
	int var; //整数变量var, int=>interger
	var = 0; //无需解释
	int var1 = 0, var2 = var, var3(0), var4(var1); //变量可以在创建时赋值，可以用=或者()，其实还能用{}
	int var5{var};
	cout << var << ' ' << ' ' << var1 << . . . << endl; //刚才的例题有没有忘打空格？
	
好了，看晕了吧？淡定的想一想。

然后来讨论一下变量名的规矩。必须以\_（下划线）或大小写字母开头，中间只能出现下划线、大小写字母或数字。顺便说一下，我上面的所有代码都是严格大小写的，也就是说C++是严格大小写的。什么意思呢？main就是main，不要打成Main；int var = 10后，cout << var << endl;可以，cout << VAR << ENDL;就不行。同理，int VAR后可别cout << var。你一开始用大写还是小写，后面就用大写或者小写严格一致哦^_^；

>那么来写一个很简单的程序吧，输入整数a，b，输出a + b。

cout是输出，输入自然就是cin。输出用的是<<，输入用的就是>>。

题目在[这里](http://acceptnoob.com/problem-00001.html)。

答案在这里：

	＃include <iostream>
	using namespace std;
	
	int main () {
	    int a, b;
	    cin >> a >> b;
	    cout << a + b << endl;
	    return 0;
	}
	
想必跃跃欲试的同学们会蛋疼一个问题，我们只能给整数进行加法运算吗？

好吧你可以a + b, a - b, a * b, a / b, a % b。 a * b就是a乘b，a / b就是a除以b，a % b就是余数，mod。自己试一下吧。

>试着编写一个程序，输入整数a，b，输出a + b, a - b, a * b, a / b, a % b。

好吧，中场休息。Time for installing B！

欢迎装X归来。不过我们学的还有很多。比如拉拉小朋友遇到了一个问题：

>老师给我两个数字a, b，如果a > b，则输出a - b，否则输出b - a

那么我们来讨论一点逻辑相关的东西。

其实很简单，a > b, a < b, a == b（为什么不用a = b？a = b是指让a的值为b）。这些式子（学名表达式，上面的五则运算也是表达式）的值都是一个叫做bool的类型。

	bool flag1 = true, flag2 = false, flag3 = 1, flag4 = 0;
	
bool变量有两个值，true，也就是1，代表真，false，也就是0，代表假。

>写个形如"bool flag = 4 > 5; cout << flag << endl;"这样的程序吧。

好了，玩好了吧。bool变量也是可以运算的，猜一猜以下运算符分别是什么意思：

	bool a = true, b = false;
	则a || b == true, a || a == true, b || b == false
	则a && b == false, a && a == true, b && b == false
	则!a = false, !b = true
	
||=>与，&&=>且，!=>非

这有什么用呢？下面介绍伟大的条件语句！

	if (值为bool的东西) {
	    如果值为真的话，执行本语句
	}
	else {
		否则执行本语句
	}

对了，如果整数值为0，表示假，**否则**为真。

来点好玩的：

	if (exp1) {
	    if (expr2) {
	    	expr1 && expr2 == true
	    }
	    else  {
	    }
	}
	else if (expr2) {
	    也可以嵌套
	}
	else if () {
	}
	无限层之后
	else {
	}
	
明白了？[帮助小拉拉吧！](http://acceptnoob.com/problem-00002.html)

好吧，继续给出答案：

	#include <iostream>
	using namespace std;
	
	int main () {
	    int a, b;
	    cin >> a >> b;
	    if (a < b) cout << b - a << endl;
	    else {
	        cout << a - b;
	        cout << endl;
	    }
	    return 0;
	}
	
如果if或者else后面跟的语句只有一条，可以省略大括号！如果else后面没有语句，可以不写else！当然，别这样写：

	if (exp1)
	    if (exp2) {
	    }
	else {
	}
	
打空格（一般都是4格一层，这种东西叫做缩进），只是为了阅读代码条理清晰，编译器可不认哦！所以上面的代码实际的意思是：
	
	if (exp1)
	    if (exp2) { }
	    else {}
	else { 还可以接哦 }

下面来讨论一种本题的简洁一点的写法：

	cout << (a < b ? b - a : a - b) << endl;
	
value ? exp1 : exp2，这叫条件表达式，value真，执行exp1，否则执行exp2

