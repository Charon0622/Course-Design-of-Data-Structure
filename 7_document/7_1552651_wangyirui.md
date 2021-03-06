###<center><h1>数据结构项目一文档</h1></center><br/>
#####<center><h5>同济大学 软件学院 15级2班 1552651 王依睿</h5></center>
---
<center><h2>目录</h2></center>

<!-- MarkdownTOC -->

- 使用说明
- 概述
- 函数接口

<!-- /MarkdownTOC -->


---
## 使用说明
### 操作手册
- 运行程序后，请求用户输入表达式。<br/>
![qwer] (file:\E:\Study\data\project\7\7_document\7_1.jpg)
- 输出波兰表达式、中缀表达式、逆波兰表达式。<br/>
![qwer] (file:\E:\Study\data\project\7\7_document\7_2.jpg)

### 注意事项
- 输入的表达式字符长度请勿超过100。
- 请输入合法的中缀表达式。
- 表达式中仅允许 '+' 、 '-' （作为减号或负号）、 '*' 、 '/' 、匹配的前后括号（ '(' 、 ')' ）以上六种运算符出现。
- 单个数字的取值在 -2147483648 ~ +2147483647 之间。

---
## 概述
### 程序设计目的
- 实现一个将中缀表达式转换成波兰表达式和逆波兰表达式的简单程序，练习二叉树的编写实现，熟悉面向对象程序设计。
### 算法思路
- 将读入的操作数和操作符进行预处理，将单个操作符或操作数以及它们的优先级存入一个结构体里（注意：如果遇到 '-' 作为负号使用，程序将其处理为 "(-1)*" 这个等价操作）。
- 利用一个操作符栈和一个操作数栈将表达式存入一个二叉树中：
    + 从表达式左端开始，如遇到操作数将其压入操作数栈。
    + 如遇到操作符，将其与栈顶操作符相比较：
    
        * 若栈顶操作符优先级高于当前待入栈的操作符，栈顶操作符出栈，操作数栈进行两次栈顶操作数出栈，并将操作符作为根节点，操作数分别作为左右子节点构造一棵二叉树，并将此压入操作数栈作为一个操作数。重复以上做法，直至栈顶操作符优先级低于或等于当前操作符待入栈的操作符。
        * 若栈顶操作符优先级低于或等于当前待入栈的操作符，将其压入操作符栈。
        
    + 处理完表达式最后一项后，用与上述相同的方法构造二叉树直至操作符栈弹空。
    + 从操作数栈中取出的唯一一个元素即是我们所要的表达式树。
    
- 利用二叉树的先序遍历输出波兰表达式，利用二叉树的后序遍历输出逆波兰表达式。

### 数据结构
- 采用两个栈，一个作为操作数栈，一个作为操作符栈
- 将二叉树节点封装成一个结构体
- 将二叉树（表达式树）封装成一个类

###文件目录
- 1_1552651_wangyirui.cpp（主文件）
- BT_class.h（二叉树类）
- BT_class.cpp（二叉树类函数实现）
- 1_1552651_wangyirui.exe（可执行文件）
- 1_1552651_wangyirui.pdf（项目文档）

---
##函数接口
###二叉树节点接口（Node）
成员函数名|功能|参数|返回值类型
:--------:|:--:|:--:|:--------:
void setNode(char opr, int pr) |设置节点内部操作符及其优先级|操作符opr，优先级pr|
void setNode(int opd, int pr)|设置节点内部操作数及其优先级（其优先级表示节点内部存储的是操作数）| 操作数opd，优先级pr|

###二叉树接口（BT）
成员函数名|功能|参数|返回值类型
:--------:|:--:|:--:|:--------:
void visit(pNode x)|访问并打印节点|根节点pNode|
void travPre_R(pNode x)|通过先序遍历打印节点|根节点pNode|
void travIn_R(pNode x)|通过后序遍历打印节点|根节点pNode|
void empty(pNode x)|用于清空二叉树|根节点pNode|

###栈处理函数接口
成员函数名|功能|参数|返回值类型
:--------:|:--:|:--:|:--------:
void stackprocess(pNode *expr, int cnt, pNode &root)|对表达式进行栈处理|表达式数组pNode *，表达式数组长度int，根节点 pNode|

###构造二叉树函数接口
成员函数名|功能|参数|返回值类型
:--------:|:--:|:--:|:--------:
void buildtree(pNode opr, pNode sucopd, pNode preopd)|构造二叉树|根节点（操作符）pNode，左儿子（操作数1）pNode，右儿子（操作数2）pNode





