# 本地 C 语言编辑器选择

> 本篇完全是**介绍性**的内容，核心观点为推荐安装配置 VSCode、不推荐使用 Dev-C++。但如果存在重大的环境配置困难，可以临时使用 Dev-C++ 作为过渡。

!!! info "可以跳过本篇直接进入[下一篇](vsc_install.md)安装配置 VSCode"

代码编辑器，也就是一个能方便写代码的软件。你可以用各种软件写代码，Vim、Emacs，甚至记事本也可以拿来写代码。

IDE，全称 Integrated Development Environment，即集成开发环境。除了基础的源代码编辑功能，IDE 还一般包括编译器、调试器、GUI 等功能。

> GUI，全称 Graphics User Interface，即图形用户界面，和它相对的是 CLI (Command-Line Interface，命令行界面)。

- VSCode (推荐)
    - 由 Microsoft 开发的代码编辑器，全称 Visual Studio Code
    - 跨平台，完全免费，支持丰富的插件扩展，功能极其强大
    - 到实验室和公司阶段仍然可以继续使用
    - 虽然严格来说是代码编辑器，但是插件配置后功能可以非常强大，具有 IDE 的一些特性
- Dev-C++ (不推荐)
    - 最早由 BloodShed 开发的 C/C++ IDE
    - 免费，但并不跨平台
    - 非常方便安装使用，不需要手动安装编译器，许多初学者的入门 IDE
    - 但是**非常不推荐长期使用**，旧版已经多年无人维护，不管新版旧版都存在许多奇怪的问题
- CLion 
    - 由 JetBrains 开发的专门面向 C/C++ 的 IDE
    - 跨平台，集成了 CMake
    - 收费，但目前学生和学术人员（教师）身份验证后可以免费使用
    - 本人未使用过，但据说代码提示和规范提醒做得不错
- Vim/Emacs
    - 具有极客风格的代码编辑器
    - 某位 OS 老师盛赞这才是 Professionals 该用的代码编辑器
    - 没有 GUI 也能直接写代码，比记事本方便一些
- Visual Studio/XCode
    - IDE，前者由 Microsoft 开发，后者由 Apple 开发
    - 都不跨平台，一般分别用于开发专用于 Windows/Apple 平台的应用程序

**推荐安装 VSCode**，在[下一篇](vsc_install.md)中将介绍其安装教程。

**非常不推荐**安装 Dev-C++。但是如果运行环境安装存在巨大的困难，可以暂且将 Dev-C++ 作为前期作业的一个替代手段。可以参考这篇[知乎文章](https://zhuanlan.zhihu.com/p/88295732?utm_source=qq)安装 Dev-C++，或者直接从[官网](https://www.bloodshed.net/)跳转下载安装包。其安装基本上是傻瓜式的，未来你在课程中可能难免遇见仍在将 Dev-C++ 作为主力 IDE 的课友，可能需要跟他们合作或者对他们的课程作业进行互评，届时将会发现 Dev-C++ 带来的巨大不便。

初学者不推荐直接上手 Vim/Emacs，比较熟练的同学可以自行探索体验 Professionals 的人生。