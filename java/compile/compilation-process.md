### Java源代码编译成Class文件的过程
#### javac编译器
javac编译器是官方JDK中提供的前端编译器

#### javac编译过程
JVM规范定义了Class文件结构格式，但没有定义如何从java程序文件转化为Class文件，所以不同编译器可以有不同实现

##### 子过程:
- 解析与填充符号表过程：解析主要包括词法分析和语法分析两个过程
- 插入式注解处理器的注解处理过程
- 语义分析与字节码的生成过程

#### javac中的访问者模式
访问者模式可以将数据结构和对数据结构的操作解耦
使得增加对数据结构的操作不需要修改数据结构
也不必修改原有的操作
而执行时再定义新的Visitor实现者
- Javac经过第一步解析（词法分析和语法分析）
- 会生成用来一棵描述程序代码语法结构的抽象语法树
- 每个节点都代表程序代码中的一个语法结构
- 包、类型、修饰符、运算符、接口、返回值、甚至注释等
- 不同编译阶段都定义了不同的访问者去处理该语法树（节点）

#### 解析与填充符号表
- 解析：词法、语法分析

#### 词法分析
- 概念解理
- 词法分析是将源代码的字符流转变为标记（Token）集合

#### 语法分析
- 语法分析是根据Token序列构造抽象语法树的过程
- 抽象语法树（Abstract Syntax Tree,AST）
  - 是一种用来描述程序代码语法结构的树形表示方式
  - 每个节点都代表程序代码中的一个语法结构
  - 语法结构（Construct）包括：包、类型、修饰符、运算符、接口、返回值、甚至注释
  
#### 代码执行的解析过程
- 由JavaCompiler.compile()方法调用JavaCompiler.parseFiles()方法完成参数输入的所有文件的编译
- JavaCompiler.parseFiles()方法中又调用本类中的parse()方法对其中一个文件进行编译
- JavacParser.parseCompilationUnit()方法中调用JavacParser.typeDeclaration()进行文件中所有类型定义的解析

#### 代码执行的填充过程
- JavaCompiler.enterTrees() 方法调用 Enter.main() 方法
- Enter.main() 方法调用中本类的 complete() 方法
- 接着complete() 方法还会不断调用前面生成的每个类的类符号实例的 ClassSymbol.complete() 方法
- MemberEnter.complete() 中会添加类的默认构造函数（如果没有任何的）

#### Java语言层面特征签名:
方法名、参数类型和参数顺序

#### JVM层面特征签名:
方法名、参数类型、参数顺序和返回值类型
这个在后面文章介绍Class文件格式再详细说明

#### 编译器自动添加实例构造函数、"this" 类变量符号、"super" 父类变量
- 类中没有定义任何实例构造函数，编译器会自动添加默认的类实例构造函数
- 添加 "this" 类变量
- "super" 父类变量符号

#### 插入式注解处理器的注解处理过程
- 源码分析
- 注解处理器实现与运行
- 语义分析与字节码生成

https://blog.csdn.net/tjiyu/article/details/53748965