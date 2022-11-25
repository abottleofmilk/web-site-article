---
title: QT教程
date: 2022-11-24 19:49:29
tags:
  - GUI
  - QT
categories:
  - GUI
  - QT
---
## 工具

### QT目录结构

<img src="https://s2.loli.net/2022/11/25/7E2LJ3jxRqlWgcY.png" style="zoom: 80%;" />

Qt 类库的帮助文件位于 Docs 文件夹里，需要用 Qt Assistant 工具才能查看。QtCreator 是个例外，QtCreator 使用 MSVC2015 编译生成的，所以安装目录里有一个 vcredist 文件夹存储 VC 运行库安装文件。最后的 MaintenanceTool.exe ，对于离线安装包，它只能用于删除软件包，如果 Qt 开发环境是用在线安装方式装的，这个工具还可以管理开发环境组件和升级组件。

<img src="https://s2.loli.net/2022/11/25/93YAlISg5hmLOD1.png" style="zoom: 75%;" />

### 常用工具

在上个世纪八十年代，计算机都是奢侈品，操作系统里最著名的是 Unix 家族， 当时还没有 Windows、Linux 之类的，Unix 系统都是商业软件，里面的应用软件也是商业软件， 全是封闭的环境。 系统程序员 Richard M. Stallman (RMS) 在此环境下创立了与众不同的 [GNU 项目](https://www.gnu.org/) (GNU's Not Unix) ， 以及推进自由软件发展的 [Free Software Foundation (FSF) 自由软件基金会](https://www.fsf.org/)。 GNU 项目是为了创建自由的类 Unix 系统，也因此开发出来很多开源的系统工具，其中非常著名的就是 [GCC](http://c.biancheng.net/gcc/) （GNU Compiler Collection，GNU编译器套件）。

| 工具 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| gcc  | GNU C 语言编译器。                                           |
| g++  | GNU [C++](http://c.biancheng.net/cplus/) 语言编译器。        |
| ld   | GNU 链接器，将目标文件和库文件链接起来，创建可执行程序和动态链接库。 |
| ar   | 生成静态库 .a ，可以编辑和管理静态链接库。                   |
| make | 生成器，可以根据 makefile 文件自动编译链接生成可执行程序或库文件。 |
| gdb  | 调试器，用于调试可执行程序。                                 |
| ldd  | 查看可执行文件依赖的共享库（扩展名 .so，也叫动态链接库）。   |

+ CMake（Cross platform Make）是一个开源的跨平台自动化构建工具， 可以跨平台地生成各式各样的 makefile 或者 project 文件， 支持利用各种编译工具生成可执行程序或链接库。 CMake 自己不编译程序， 它相当于用自己的构建脚本 CMakeLists.txt，叫各种编译工具集去生成可执行程序或链接库。
+ 原本 GNU 工具只在 Linux/Unix 系统里才有，随着 Windows 系统的广泛使用， 为了在 Windows 系统里可以使用 GNU 工具，诞生了 MinGW（Minimalist GNU for Windows） 项目，利用 MinGW 就可以生成 Windows 里面的  exe 程序和 dll 链接库。
+  另外提一下，由于 MinGW 本身主要就是编译链接等工具和头文件、库文件，并不包含系统管理、文件操作之类的 Shell 环境， 这对希望用类 Unix 命令的开发者来说还是不够用的。 所以 MinGW 官方又推出了 MSYS（Minimal SYStem），相当于是一个部署在 Windows 系统里面的小型 Unix 系统环境， 移植了很多 Unix/Linux 命令行工具和配置文件等等，是对 MinGW 的扩展。MSYS2 是 MSYS 的衍生版，不仅支持 64 位系统和 32 位系统，还有自己的独特的软件包管理工具，它从 Arch Linux  系统里移植了 pacman 软件管理工具，所以装了 MSYS2 之后，可以直接通过 pacman  来下载安装软件，而且可以自动解决依赖关系、方便系统升级等。装了 MSYS2 之后，不需要自己去下载 MinGW-w64，可以直接用 pacman 命令安装编译链接工具和 git 工具等。

Qt 官方的开发环境安装包里有自己专门的开发工具，之前用过 qmake 命令。qmake 是 Qt 开发最核心的工具，既可以生成 Qt 项目文件 .pro ，也可以自动生成项目的 Makefile 文件。

| 工具      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| qmake     | 核心的项目构建工具，可以生成跨平台的 .pro 项目文件，并能依据不同操作系统和编译工具生成相应的 Makefile，用于构建可执行程序或链接库。 |
| uic       | User Interface Compiler，用户界面编译器，Qt 使用 XML 语法格式的 .ui 文件定义用户界面，uic 根据 .ui 文件生成用于创建用户界面的 C++ 代码头文件，比如 ui_*****.h 。 |
| moc       | Meta-Object Compiler，元对象编译器，moc 处理 C++ 头文件的类定义里面的 Q_OBJECT  宏，它会生成源代码文件，比如 moc_*****.cpp ，其中包含相应类的元对象代码，元对象代码主要用于实现 Qt  信号/槽机制、运行时类型定义、动态属性系统。 |
| rcc       | Resource Compiler，资源文件编译器，负责在项目构建过程中编译 .qrc 资源文件，将资源嵌入到最终的 Qt 程序里。 |
| qtcreator | 集成开发环境，包含项目生成管理、代码编辑、图形界面可视化编辑、 编译生成、程序调试、上下文帮助、版本控制系统集成等众多功能， 还支持手机和嵌入式设备的程序生成部署。 |
| assistant | Qt 助手，帮助文档浏览查询工具，Qt 库所有模块和开发工具的帮助文档、示例代码等都可以检索到，是 Qt 开发必备神器，也可用于自学 Qt。 |
| designer  | Qt 设计师，专门用于可视化编辑图形用户界面（所见即所得），生成 .ui 文件用于 Qt 项目。 |
| linguist  | Qt 语言家，代码里用 tr() 宏包裹的就是可翻译的字符串，开发人员可用 lupdate 命令生成项目的待翻译字符串文件 .ts，用  linguist 翻译多国语言 .ts ，翻译完成后用 lrelease 命令生成 .qm 文件，然后就可用于多国语言界面显示。 |
| qmlscene  | 在 Qt 4.x 里是用 qmlviewer 进行 QML 程序的原型设计和测试，Qt 5 用 qmlscene 取代了旧的 qmlviewer。新的 qmlscene 另外还支持 Qt 5 中的新特性 scenegraph 。 |

### 术语

#### Project

Project 的中文翻译是“项目”或者“工程”，这里的项目是指为实现某个相对独立功能的程序代码合集，这些代码不单单是放在一块，而是有相互之间的关联性，并且有专门负责管理该项目的项目文件，比如：

- Qt 使用 .pro 文件管理项目；
- VC++ 则使用 .vcproj 作为项目文件。 

集成开发环境通常都是依据项目文件（.pro/.vcproj）管理和构建项目。

#### Makefile

即生成脚本，虽然可以直接调用编译器如 g++  编译程序，但是如果项目里的代码文件变多了，哪些代码文件更新了需要重新编译，哪些代码没有改不需要重新编译等等，靠程序员自己记忆去处理是比较麻烦的事，还有哪些代码需要预处理或是链接哪些库文件， 这些都是繁杂的过程。为了规范程序的编译生成过程，产生了规范化的生成脚本，就是 Makefile，生成器 make 可以依据规范的  Makefile 自动生成目标程序或库文件。

#### Debug 和 Release

Debug 即调试，Release 即发行。代码编写之后，生成的目标程序或库文件通常不会绝对正确，或多或少有些毛病（bug），  因此需要进行纠错调试（Debug）。调试过程中需要源代码和二进制目标程序之间一一对应的关系， 这样才能定位到错误代码，所以 Debug  版本的程序是臃肿而不进行优化的。

 与之相对的是 Release 发行版，在纠正了发觉到的错误后，需要发布程序用于实际用途，实际应用时强调运行效率高，减少冗余代码，因此会对二进制程序进行大量优化，提升性能。这样发布的二进制目标程序就是 Release 版。

#### Explicit Linking 和 Implicit Linking

动态链接库通常都有其导出函数列表，  告知其他可执行程序可以使用它的哪些函数。可执行程序使用这些导出函数有两种方式：一是在运行时使用主动加载动态库的函数，Linux 里比如用  dlopen 函数打开并加载动态库，Windows 里一般用 LoadLibrary  打开并加载动态库，只有当程序代码执行到这些函数时，其参数里的动态库才会被加载，这就是显式链接。显式链接方式是在运行时加载动态库，其程序启动时并不检查这些动态库是否存在。

 隐式链接是最为常见的，所有的编译环境默认都是采用隐式链接的方式使用动态库。隐式链接会在链接生成可执行程序时就确立依赖关系，在该程序启动时，操作系统自动会检查它依赖的动态库，并一一加载到该程序的内存空间，程序员就不需要操心什么时候加载动态库了。VC 链接器使用的 .lib 文件分两类，一种是完整的静态库，体积比较大，另一种是动态库的导出声明，体积比较小。MinGW 链接器使用的 .a 文件也是类似的，Qt 官方库都是按照动态库发布的，静态库只有自己编译才会有。

### 控件与事件

- QMainWindow 类生成的窗口自带菜单栏、工具栏和状态栏，中央区域还可以添加多个控件，常用来作为应用程序的主窗口；
- QDialog 类生成的窗口非常简单，没有菜单栏、工具栏和状态栏，但可以添加多个控件，常用来制作对话框。
- 实际开发中，制作应用程序的主窗口可以用 QMainWindow 或者 QWdiget；制作一个提示信息的对话框就用 QDialog 或 QWidget；如果暂时无法决定，后续可能作为窗口，也可能作为控件，就选择 QWidget。

事件处理函数通常会完成两项任务，分别是：

- ​		修改控件的某些属性，比如当用户按下按钮时，按钮的背景颜色会发生改变，从而提示用户已经成功地按下了按钮；
- ​		运用信号和槽机制处理事件。

### 信号和槽

一个 connect() 函数只能关联一个信号函数和一个槽函数，程序中可以包含多个 connect() 函数，能实现以下几种效果：

- 关联多个信号函数和多个槽函数；
- 一个信号函数可以关联多个槽函数，当信号发出时，与之关联的槽函数会一个接一个地执行，但它们执行的顺序是随机的，无法人为指定哪个先执行、哪个后执行；
- 多个信号函数可以关联同一个槽函数，无论哪个信号发出，槽函数都会执行。

## 基础

### QT与其他GUI库

Windows 下的 GUI 解决方案比较多：

- 基于 [C++](http://c.biancheng.net/cplus/) 的有 [Qt](http://c.biancheng.net/qt/)、MFC、WTL、wxWidgets、DirectUI、Htmlayout；
- 基于 [C#](http://c.biancheng.net/csharp/) 的有 WinForm、WPF；
- 基于 [Java](http://c.biancheng.net/java/) 的有 AWT、[Swing](http://c.biancheng.net/swing/)；
- 基于 Pascal 的 有Delphi；
- 基于Go语言的有 walk 和 electron；
- 还有国内初露头角的 aardio；
- Visual Basic 曾经很流行，现在逐渐失去了色彩；
- 如果你有 Web 开发经验，也可以基于 Webkit 或 Chromium 将网页转换为桌面程序。



<img src="https://s2.loli.net/2022/11/25/kzIwlg5F2KBUOjT.png" alt="image-20221125165119244" style="zoom: 67%;" />



MFC 只能应用在 Windows 平台，而 Qt 是跨平台的，一次编写，到处运行。 另外，Qt 已经封装了底层细节，学习 Qt 将会非常简单；而 MFC 只是给 Windows API 加了一层包装，不了解 Windows API 也学不好 MFC。Linux 下常用的 GUI 库有基于 C++ 的 Qt、GTK+、wxWidgets，以及基于 Java 的 AWT 和  Swing。其中最著名的就是 Qt 和 GTK+：KDE 桌面系统已经将 Qt 作为默认的 GUI 库，Gnome 桌面系统也将 GTK+  作为默认的 GUI 库。

### QT程序

Qt Creator 可以创建多种项目，在最左侧的列表框中单击“Application”，中间的列表框中列出了可以创建的应用程序的模板，各类应用程序如下：

- Qt Widgets Application，支持桌面平台的有图形用户界面（Graphic User Interface，GUI） 界面的应用程序。GUI 的设计完全基于 C++ 语言，采用 Qt 提供的一套 C++ 类库。
- Qt Console Application，控制台应用程序，无 GUI 界面，一般用于学习 C/C++ 语言，只需要简单的输入输出操作时可创建此类项目。
- Qt Quick Application，创建可部署的 Qt Quick 2 应用程序。Qt Quick 是 Qt 支持的一套 GUI  开发架构，其界面设计采用 QML 语言，程序架构采用 C++ 语言。利用 Qt Quick  可以设计非常炫的用户界面，一般用于移动设备或嵌入式设备上无边框的应用程序的设计。
- Qt Quick Controls 2 Application，创建基于 Qt Quick Controls 2 组件的可部署的 Qt Quick 2 应用程序。Qt Quick Controls 2 组件只有 Qt 5.7 及以后版本才有。
- Qt Canvas 3D Application，创建 Qt Canvas 3D QML 项目，也是基于 QML 语言的界面设计，支持 3D 画布。

项目结构：

- Demo.pro 是项目管理文件，包括一些对项目的设置项。
- Headers 分组，该节点下是项目内的所有头文件（.h），图 5 中所示项目有一个头文件 mainwindow.h，是主窗口类的头文件。
- Sources 分组：该节点下是项目内的所有 C++源文件（.cpp），图 5 中所示项目有两个 C++ 源文件，mainwindow.cpp  是主窗口类的实现文件，与 mainwindow.h 文件对应。main.cpp 是主函数文件，也是应用程序的入口。
- Forms 分组：该节点下是项目内的所有界面文件（.ui）。图 5 中所示项目有一个界面文件mainwindow.ui，是主窗口的界面文件。界面文件是文本文件，使用 XML 语言描述界面的组成。

**默认情况下，Qt 提供的所有组件（控件、部件）都是隐藏的，不会自动显示**。

### 布局管理

Qt 共提供了 5 种布局管理器，每种布局管理器对应一个类，分别是 QVBoxLayout（垂直布局）、QHBoxLayout（水平布局）、QGridLayout（网格布局）、QFormLayout（表单布局）和 QStackedLayout（分组布局）。



<img src="https://s2.loli.net/2022/11/25/qg8znERj9PoDBIC.png" alt="image-20221125171951969" style="zoom:80%;" />

### pro文件详解

| 配置项                                          | 含 义                                                        |
| ----------------------------------------------- | ------------------------------------------------------------ |
| QT                                              | 指定项目中用到的所有模块，默认值为 core 和 gui，中间用 += 符号连接。 |
| greaterThan(QT_MAJOR_VERSION, 4): QT += widgets | 如果 QT 版本大于 4（Qt5 或更高版本），则需要添加 widgets 模块，该模块包含所有控件类。 |
| TARGET                                          | 指定程序成功运行后生成的可执行文件的名称，中间用 = 符号连接。 |
| TEMPLATE                                        | 指定如何运行当前程序，默认值为 app，表示当前程序是一个应用程序，可以直接编译、运行。常用的值还有 lib，表示将当前程序编译成库文件。 |
| DEFINES                                         | 在程序中新定义一个指定的宏，比如 DEFINES += xxx，如同在程序中添加了 #define xxx 语句。 |
| SOURCES                                         | 指定项目中包含的所有 .cpp 源文件。                           |
| HEADERS                                         | 指定项目中包含的所有 .h 头文件。                             |
| FORMS                                           | 指定项目中包含的 ui 文件。                                   |
| INCLUDEPATH                                     | 指定头文件的存储路径，例如：INCLUDEPATH += /opt/ros/include  |
| CONFIG                                          | 经常对应的值有： 			 				 					release：以 release 模式编译程序； 				 					debug：以 debug 模式编译程序； 				 					warn_on：编译器输出尽可能多的警告； 				 					c++11：启动 C++11 标准支持。 			 			例如 CONFIG += c++11。 |

### 打包

windeployqt 是 Qt 提供的 Windows 平台打包工具，它能找到 StuInfoFile.exe 可执行文件需要的所有动态链接库，并将它们拷贝到当前文件夹中。打包成功后将文件夹发给别人即可。

## 常用类



## 组件总览

## QML

QML是⼀种描述⽤户界⾯的声明式语⾔。它将⽤户界⾯分解成⼀些更⼩的元素，这些元素能够结合成⼀个组件。QML语⾔描述了⽤户界⾯元素的形状和⾏为。⽤户界⾯能够使⽤JavaScript来提供修饰，或者增加更加复杂的逻辑。从这个⾓度来看它遵循HTML-JavaScript模式，但QML是被设计⽤来描述⽤户界⾯的，⽽不是⽂本⽂档。

### QML和C++
为了适应手机移动应用开发， Qt5 将 QML 脚本编程提到与传统 C++ 部件编程相同的高度，力推 QML 界面编程，当然 QML 主要用于手机移动应用程序。 QML 包含大量使用手机移动设备的功能模块，比如基本部件（QtQuick 模块）、GPS 定位、渲染特效、蓝牙、NFC、WebkKit 等等。QML 类似于网页设计的 HTML，是一种标记语言，我们可以借助 CSS 对它进行美化，也可以借助 [JavaScript](http://c.biancheng.net/js/) 进行交互。有 Web 开发经验的读者学习 QML 将非常轻松。

 使用 QML 开发界面主要有以下几个优点：

- QML 非常灵活，可以做出非常炫酷的效果，例如 QQ、360、迅雷等都不在话下。
- QML 是标记语言，见名知意，非常容易编写和阅读，大大提高了开发和维护效率。
- QML 界面简洁大气，有很多动画，适合移动端。
- 不同平台下的 QML 使用相同的渲染机制，界面效果一致，不会随操作系统的不同而变化。

## 参考
1. [Qt教程|C语言中文网](http://c.biancheng.net/view/1792.html)
2. [QmlBook](http://qmlbook.github.io/indxex.html)
3. [doc.qt.io](https://doc.qt.io/)