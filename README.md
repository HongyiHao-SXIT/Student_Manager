# 学生成绩管理系统

## 一、项目概述

本学生成绩管理系统是一个基于 C++ 语言开发的命令行应用程序，旨在帮助教师或相关管理人员方便地对学生的多门课程成绩进行各种操作管理，包括成绩的输入、查询、修改、删除、统计分析以及排序显示等功能，满足日常教学中对学生成绩管理的基本需求。
## 二、功能介绍
<b>成绩输入（Input）</b><br>
通过命令行交互的方式，引导用户依次输入学生的班级、学号、姓名以及多门课程（电子技术、C++ 程序设计、多媒体技术、大学英语、高等数学、大学体育、马克思主义基本原理）的成绩。在输入学号时会进行查重验证，确保学号的唯一性；对于每门课程成绩，会进行合法性校验，只接受 1 - 100 之间的数字作为有效成绩输入。输入完一名学生成绩后，会询问是否继续录入其他学生成绩，最后将所有录入的成绩数据保存到名为score.txt的文件中。<br>

<b>成绩统计（Statistic）</b><br>
从score.txt文件中读取已存储的学生成绩数据，然后在命令行展示出包含班级、学号、姓名和平均分的学生成绩统计信息表格，方便直观地查看各学生的平均成绩情况。展示完毕后会暂停命令行界面，等待用户操作。<br>

<b>成绩查找（Lookup）</b><br>
首先从score.txt文件读取学生成绩数据，接着提示用户输入要查找的学生学号，根据输入的学号在已存储的数据中进行匹配查找。若找到对应学号的学生，则详细展示该学生的各项成绩信息（班级、学号、姓名以及各课程成绩和平均分）；若未找到匹配学号的学生，则给出相应提示信息。<br>

<b>成绩修改（Modify）</b><br>
同样先从score.txt文件获取成绩数据，再让用户输入要修改成绩的学生学号，找到对应学生后展示其原始成绩信息，并提示用户重新输入各项成绩，重新计算平均分。完成修改后，会询问用户是否保存数据，若用户确认保存（输入y或Y），则将更新后的所有学生成绩数据重新写入到score.txt文件中。<br>
<b>成绩删除（Delete）</b><br>
从score.txt文件读取成绩数据后，根据用户输入的要删除学生的学号进行查找。若找到对应的学生，会将该学生的记录从数据中移除（通过覆盖式移动后续学生记录实现），然后将更新后的学生成绩数据重新写入score.txt文件（学生数量减 1），同时给出删除成功的提示；若未找到对应学号的学生，则显示相应提示信息。<br>

<b>成绩插入（Insert）</b><br>
先是读取score.txt文件中的已有成绩数据，接着在命令行引导用户输入新学生的各项成绩信息（班级、学号、姓名及各课程成绩等），计算平均分后添加到成绩数据中。每添加完一名学生成绩，会询问是否继续插入新学生成绩，全部完成后将更新后的所有成绩数据重新写入到score.txt文件中。<br>

<b>成绩排序（Sort）</b><br>
读取score.txt文件里的学生成绩数据，按照平均分进行降序排列（使用冒泡排序算法，通过交换各项成绩及对应学生信息的方式实现排序），排序完成后展示包含班级、学号、姓名以及各课程成绩和平均分的详细信息表格，最后将排序后的成绩数据再次写入score.txt文件中。<br
>
<b>成绩显示（Output）</b>
从score.txt文件读取成绩数据，若文件中有记录，则以表格形式展示所有学生的详细成绩信息（班级、学号、姓名以及各课程成绩和平均分）；若文件中无记录，则提示 “没有记录”。

## 三、使用方法
### 编译运行
确保系统已安装支持 C++ 11 及以上标准的编译器（如 GCC、Clang 或者 Visual C++ 等），将代码保存为.cpp文件（例如student_score_management.cpp）后，在命令行中进入代码所在目录，使用相应编译器命令进行编译，例如使用 GCC 编译可执行命令g++ student_score_management.cpp -o student_score_management（生成名为student_score_management的可执行文件，文件名可自定义），然后运行生成的可执行文件即可启动成绩管理系统。
菜单操作
启动系统后，会显示操作菜单，包含以下选项：<br>
<b>【1】输入学生成绩：</b>进入成绩录入流程，按照提示依次输入学生各项信息及成绩。<br>
**【2】显示统计数据：** 展示所有学生的统计成绩信息（班级、学号、姓名、平均分）。<br>
**【3】查找学生成绩：** 根据输入学号查找并显示对应学生的详细成绩情况。<br>
**【4】修改学生成绩：** 通过学号定位学生，重新录入并更新其成绩信息（可选择是否保存）。<br>
**【5】删除学生成绩：** 依据学号删除指定学生的成绩记录。<br>
**【6】插入学生成绩：** 添加新学生的成绩信息到已有数据中。<br>
**【7】按平均分排列：** 对所有学生成绩按平均分降序排列并展示，同时更新文件中的数据顺序。<br>
**【8】显示学生成绩：** 展示所有学生的完整成绩详情表格。<br>
**【0】退出管理系统：** 结束程序运行。<br>
根据需求选择相应的数字序号，然后按照后续的提示信息进行具体操作即可。

## 四、代码结构说明
**Student类**<br>

定义了学生成绩管理系统中的核心数据结构，包含了表示学生信息和成绩的私有成员变量，如num（学号）、name（姓名）、各课程成绩（elec、c_program等）以及平均分average等，同时声明了多个公有成员函数，每个函数对应一种成绩管理操作（如Input、Statistic等），这些函数实现了对学生成绩数据的具体处理逻辑。<br>

**menu函数**<br>
用于在命令行中展示系统操作菜单，并获取用户输入的合法操作选项（0 - 8 之间的数字），通过循环和输入校验确保用户输入符合要求，最后返回用户选择的操作对应的数字。<br>

**main函数**<br>
作为程序的入口点，通过无限循环不断调用menu函数获取用户操作选择，然后利用switch语句根据不同的选择调用Student类中对应的成员函数来执行相应的成绩管理操作，直到用户选择退出系统（选择0）为止。

## 五、注意事项
**文件操作相关**<br>
程序通过读写名为score.txt的文本文件来持久化存储学生成绩数据，需确保程序对该文件所在目录具有读写权限，否则可能出现文件打开失败等问题（如显示score.txt can't open!提示）。另外，文件中的数据格式需遵循程序写入时的格式约定，随意修改文件内容可能导致数据读取或写入错误。<br>
**输入格式要求**<br>
在进行各种成绩输入、学号输入等操作时，需严格按照命令行提示的格式要求进行输入。例如成绩需输入 1 - 100 之间的整数，学号输入要保证唯一性等，不符合格式要求可能会出现输入验证不通过，需要重新输入的情况。<br>
## 六、改进方向
**数据存储优化**<br>
目前采用简单的文本文件存储数据，在处理大量学生成绩数据时效率较低且数据安全性有限，可以考虑使用数据库（如 MySQL、SQLite 等）来存储数据，提高数据读写效率以及数据管理的便利性和安全性。<br>

**用户界面改进**<br>
命令行交互方式相对不够友好直观，可以考虑开发图形用户界面（GUI），例如使用 Qt 等跨平台的 GUI 框架，让用户通过可视化界面更便捷地进行各项成绩管理操作。

**代码结构优化**<br>
部分函数（如排序函数Sort中交换数据的逻辑）代码较为冗长重复，可以进行函数封装等代码重构操作，提高代码的可读性、可维护性以及可扩展性，便于后续功能的添加和修改。