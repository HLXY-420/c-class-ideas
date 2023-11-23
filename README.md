# 一些关于C/C++语言课程的想法

## 0 关于

一个仓库，用来记录关于C/C++语言课程的想法，具体可以参见以下内容或者[index.md](./docs/index.md)。关于现在正在尝试做的相关事项，参见[短期尝试](./docs/workon-list.md)。

## 1 背景

在某大学的大一C语言课上当着助教，平时主要负责帮助同学解决编程时遇到的问题和困难。半个学期下来，发现了初学者们遇到的问题的一些规律，也与其他学校的朋友交流了一下，发现各处的C/C++课程都存在着一些共同的问题：

1. **C/C++语言本身的难度：** 这两门语言在接近计算机底层和易于编写上做到了一个不错的平衡，但是这个平衡是针对有经验的程序员而非编程初学者的。漫长的历史使得它们本身的内容越来越复杂，这进一步增加了将它们作为第一门编程语言的学习成本。举个例子，在绝大多数课程上第一个引入的IO，就有scanf、printf、gets、puts等多个功能不同的函数。理解它们并合理地运用之，对新手就已经是一种挑战了。
2. **课程设计和实施的问题：** 我发现，多数的C/C++课程存在课程与时代脱节和教学与实践脱节的现象。我至今仍未见到一本提到c11或者c++11的国内教科书，许多已被弃用的写法仍然出现在它们中，即使它们的出版/印刷日期就在最近几年。同时，编程也存在这样一个问题：已经学会的人难以重新站在初学者的视角思考。这一点在课程的讲解和实践性质作业的布置上的体现尤其显著，即很少有老师能讲好这门课。

这两个问题的结果就是，很少有人从大学课堂上学会C/C++，大多数人会选择慕课或者其他资料进行自学。

然后，根据我对这门课程的理解，给大一年级开设的C/C++课程的主要目的应该是以下两点：

1. **计算思维和程序设计思维：** 会上C/C++课程的学生，其专业本身也会学到/用到许多编程相关的内容或者工具，对程序理论和设计思想的了解是必要的。C/C++课程作为第一门编程课，自然要担任培养学生计算思维和程序设计思维的角色，为后续的课程打下基础。
2. **对计算机底层逻辑的了解：** C/C++课程选择这两门语言的原因之一，我认为就是它们与计算机底层设计联系密切，可以为学生之后的操作系统或者体系结构乃至硬件相关的课程作铺垫，一般来说，开设C/C++课程的专业后续都至少会有其中一门课。

至于学习这两门语言本身，我认为并非这门课程的重点，一来编程语言只要编程范式相同，互相之间的语法差别一般并不显著，迁移学习的成本并不高，二来在实际的应用中，C/C++也并非唯一的主流，编程语言各有各的生态位，对于不打算在这两门语言上深耕的人来说，上面列出的两点远比额外的C/C++知识重要。

## 2 一些想法

基于以上列出和讨论的事项和一些自己或者周围人学习编程的经验，我有了一些对C/C++课程的改进想法。

### 2.1 “程序分析”

在设计程序时，我们一般要同时考虑整体性的程序功能的设计和细节上具体语句/函数等等的组织。一般的C/C++课程主要讲解后者，而前者则更依赖学生在完成题目或者项目时的自行探索。但是实际的编程语言中，各种语句和函数有着相当丰富的用法，衍生出种类繁多的写法，在课程中不可能全部覆盖。因此，我认为，一套描述语句/函数功能并把它们和整体程序的设计联系起来的方法论才是C/C++课程该介绍的。

在一般的C/C++课堂上，使用命令式编程足以解决所有问题了。但是在当助教答疑的过程中，我发现不少同学学习C/C++的第一个困难是理解for/while循环结构并将其运用于程序中，我依照这两种循环语句的逻辑去讲也收效甚微，但是用for-each乃至map和reduce式的处理来讲解，他们很快就可以理解并写出来类似逻辑的代码。于是我认为，在学习时部分引入命令式之外的编程思想，对于某些内容的理解可能反而更有帮助。

一种常见的设计程序的方法，是依据条件设计出程序整体的功能和表示各个现实对象的抽象对象，然后把程序分拆成多个模块，每个模块负责一部分功能。假如把这个想法略作修改，整体程序可以很自然地设想成一个函数，接受对应形式和内容的输出，产生对应的输出。拆分子模块可以改为拆分成许多小函数，复合成为整体程序这个函数。

另一边，程序中已有的函数显然可以视作函数。而各种语句则类似于符号逻辑中的语句。于是，我们可以把所有的程序都拆分成由函数和逻辑构成，整体程序的本质也可以与细节上具体的函数或者语句等同。从而，每一个引入的语句或者函数都可以被很好地描述与定义，并被学生融入自己的程序中。

于是，我认为值得引入少量离散数学的内容，比如简单的集合论和数理逻辑，帮助学生从这个角度理解和设计程序。由于这个想法和数学中的分析学的部分内容略有相似，我将其命名为“程序分析”。

### 2.2 简化C

前面提到，C/C++语言课程的问题之一，就是C/C++语言本身的难度。但是又因为需要培养学生对计算机底层设计的了解，因此不宜直接换成其他语言，况且一般足够接近硬件的语言，学习曲线都是比较陡峭的。

对于这种情况，我的想法是制作一个C/C++类库，封装一些辅助宏/函数/容器等内容，使得基于此库编写的C/C++程序可以实现接近python的简洁易懂程度。然后在课程中先教会学生基于此库编写C/C++代码。参考北京市高中技术学考中即有python编程题目，可以认为像python这样的编程语言是绝大多数人都可以学会的，大学生应当至少有与高中生相近的学习能力，那么一门学习难度与python相近的语言应该不会成为困难。

然后，在每讲完一个专题之后，就要求学生不再使用该库中对应的部分，如果要使用，则需要自己实现。这样直到课程的最后，所有学生都理应学会了如何编写一般意义上的C/C++语言程序。并且因为在学会简化的C/C++语言的过程中，学生们获得了一定的编程能力，因此在逐步返回标准C/C++时，所花费的时间会远小于从头学习C/C++语言的时间，所以这样的课程设计所花费的课时应该并不会超过传统C/C++课程。

### 2.3 可视化反馈

编程语言需要提过大量的实践练习才能掌握，作为一门课程，提供这一点所要依靠的就是布置足够多的实践题目或者项目性质的作业。于是C/C++课程的作业量往往不低：在身边的简单统计发现，零基础的同学每周完成课内作业至少需要一整个下午的时间，且大部分时候这个时间消耗会翻倍甚至更多。而面对繁多的作业，如果不能调动起学生的兴趣，那么很容易让课程变得无聊且令人反感。于是我轮询了身边人对编程感兴趣的起因，结论就是，要有能看到的成果，提供直观且强度足够的反馈。可以是oj上的排名，也可以是自己写着玩的小程序，等等等等。

引入oj并使用排名体系这件事情已经在一些学校的C/C++课程上实施了，但是绝大多数的OJ是面对题目准备的，很少具有评测程序项目的系统，我认为这是有必要去实现的：在编程水平到达一定程度后，动手实现小规模的实际项目比题目更能激发兴趣，也能顺带锻炼一些软件工程的能力——不过如何设计合适的项目作业确实是一个挑战，它需要足够有趣/有用且并不包含过于复杂的设计，或许可以从高级课程的较简单的部分中尝试提取。

也说说我想到的另一个可能的方法。既然要直观的反馈，那么利用计算机学科下与C/C++有些联系的图形学或许会是个不错的方法——提供一个简单的2D渲染引擎，至少像python的海龟画图那样，几行代码下去，图形跃然屏上。更进一步，可以让学生尝试用它构建一些简单的2D游戏，类似一些学校的C语言课程设计作业内容，但是相比于在一学期漫长的课程后才介绍这些内容，在课程的开头便引入，可以直观地让学生看到学会了C/C++，可以用来做什么。

### 2.4 信息相关的软技能

以上的三点更多关注于C/C++课程的教学内容，然而在答疑时我发现，有些并不直接相关于这门课的内容也影响着学生的学习体验和学习效果，并且这些内容往往与信息相关。那么，作为许多大学生的第一门信息相关的非传统课程，我认为有必要在课程的开头对它们做一些简要的介绍。

首先是在答疑时感受最多的，如何提问。经常我会遇到意义不明或者代码与输入输出只提供了一半的提问，次数累积起来，虽然我的耐心或许还能承受，但是它出现的频率已经足以证明它是个普遍性的问题了。在看到有不少课程/教学材料都会在开头介绍[提问的智慧（中译版）](https://github.com/tvvocold/How-To-Ask-Questions-The-Smart-Way)或者类似的内容后，我觉得它值得所有入门计算机的学生阅读一遍，也值得在课堂上专门拿出来些时间介绍其主要内容，或许结合上问程序题目的典型场景会更有效果。

其次是，是信息的检索能力。从体感上来说，我担任助教的班级上，信息检索能力大约有着和C/C++基础接近的分布和方差。于是，就像设计课程时更需要考虑零编程基础的群体一样，也应为信息检索能力一般的同学们设计些专门的内容。我觉得对于信息检索的介绍，可以分成授之以鱼和授之以渔的两部分——一方面提供一些C/C++语言常用的一些网站，比如[CppReference](https://zh.cppreference.com)，另一方面则说明一些信息检索相关的技能，比如搜索引擎的选取与使用，不同类型的信息来源的可信度，乃至一些简单的对LLMs的介绍等。

### 2.5 一个简单的课程设计想法

简单设想了一个两学期的C/C++语言课程，差不多正好对位C/C++语言程序设计+C/C++语言课设：

第一学期：程序分析与简化C/C++语言交叉进行 + 部分标准C/C++语言

第二学期：标准C/C++语言，后续的课程为各个进阶主题的介绍研讨性质课程，学生分组完成一个对应主题的项目作业。

## 3 接下来

以上所提到的，仍然只是一些粗糙的理解和想法，接下来我准备现在担任助教的课程乃至BJUT校内实践其中的一部分，写一些文档和题目，构建一些新的基础设施，做一些小组教学实验等等，更多请参见[短期尝试](./workon-list.md)。

与此同时，我准备调查些广受好评的C/C++语言课程或者计算机概论课程，了解它们是如何讲好这些内容的。也会去ACM SIGCSE等计算机教育相关的期刊会议里找找相关的研究。
我想我能想到的事情多半早前就有人想过，他们或许也会留下些什么值得参考的东西。
