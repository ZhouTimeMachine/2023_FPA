# 安装 C 语言编译器

!!! info "本篇相对比较复杂，如果在本篇配置遇到难以解决的困难，而作业/实验截止日期快要到了，可以跳过本篇参考 [下一篇](local_env.md) 安装 Dev-C++ 进行临时开发。"

写完了 C 语言代码，我们需要让它变成能跑的程序，这就需要准备 C 语言的编译器支持。以下主要介绍 Windows 系统的配置。

## 就决定是你了，gcc！

> 自由软件 (free software)，根据自由软件基金会对其的定义，是一类可以不受限制地自由使用、复制、研究、修改和分发的，尊重用户自由的软件。——维基百科

gcc，全称 GNU Compiler Collection，著名的自由软件，被许多现代类 Unix 操作系统采用为标准编译器，但是 Windows 上并不直接支持。我们想要在 Windows 系统上使用，一般得依赖 MinGW 的 gcc，tdm-gcc 也是基于 MinGW 的 gcc 来的。

!!! info "有能力的同学推荐在 Windows 上开启 WSL，使用 WSL 进行 C 语言开发。WSL 可以理解为在 Windows 的电脑中模拟一个 Linux 的小系统，从而能方便地控制环境。[WSL 安装简单引导](../windows_lost/#wsl)提供了一个简单的引导。"

## Windows 小白教程之 tdm-gcc

> 前面选择了 WSL 的同学可以自行配置或者参考[WSL 安装简单引导](../windows_lost/#wsl)，然后再看[第 3 节](#gcc_1)。Mac 用户可以直接看[第 3 节](#gcc_1)。

可以按照老师的视频教程下载 [tdm-gcc](https://jmeubank.github.io/tdm-gcc/download/)，目前最新版为 gcc 10.3.0。

桌面找到 `此电脑`，右键属性，可以看到是 64 位系统还是 32 位系统（现在一般都是 64 位系统）。64 位系统直接下载 tdm64-gcc-10.3.0-2.exe 安装即可，32 位则选择 tdm-gcc-10.3.0.exe。

同样考虑自定义安装选项：

- 自定义目录
    - 默认 C 盘也挺不错
- 可选的安装项
    - 可以全选。如果确定不需要一些东西可以不选，比如确定自己不会再需要调试 32 位程序的话可以不选 gdb32
- Start Menu items
    - 看个人意愿，可以不选
- Add to PATH
    - **建议选上**。如果不选或者忘选了，将会需要自己配置 tdm-gcc 的环境变量路径。

> P.S. 如果希望用更新版本的 gcc 可以使用 [winlibs 编译的 mingw-gcc](https://winlibs.com/)，或者你可以自己选择。

## 测试 gcc 是否正确安装

=== "Windows"
    在命令提示符/终端中输入 `gcc`，应当出现如下信息：
    ```
    gcc: fatal error: no input files
    compilation terminated.
    ```

    !!! info "不了解 Windows 上的命令提示符/终端的同学可以参考[运行与终端](../windows_lost/#_1)"
    
    如果没有，可能是你还没有安装 gcc，或者你前一步 `Add to PATH` 没有正常进行，可能需要参照 [Windows 修改环境变量](#windows)进行环境变量的检查。
    
    命令提示符/终端中输入 `gcc --version`，应当出现类似如下的信息。
    ```
    gcc.exe (tdm64-1) 9.2.0
    Copyright (C) 2019 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions.  There is NO
    warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
    ```
    
    我的版本显示是 `9.2.0`，是因为装了旧版本的 tdm-gcc，你们的显示将会是 `10.3.0`。

=== "WSL"
    终端中输入 `gcc`，应当出现如下信息：
    ```
    gcc: fatal error: no input files
    compilation terminated.
    ```

    终端中输入 `gcc --version`，可能会出现类似如下的信息：
    ```
    gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
    Copyright (C) 2021 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions.  There is NO
    warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
    ```

=== "macOS"
    Mac 用户直接使用 `gcc -v` （或者 `xcode-select --install`）会提示你安装开发者工具，然后就会自动安装 XCode 在内的一系列开发支持，最后告诉你你安装的 gcc 其实是 clang，本质上是它将 gcc 作为 clang 的别名 (alias) 了。

    成功安装后，终端输入 gcc 会出现如下信息：
    ```
    clang: error: no input files
    ```
    
    使用 `gcc --version` 可能出现以下信息：
    ```
    Apple clang version 14.0.3 (clang-1403.0.22.14.1)
    Target: x86_64-apple-darwin22.6.0
    Thread model: posix
    InstalledDir: /Library/Developer/CommandLineTools/usr/bin
    ```
    
    gcc 和 clang 都是 C 语言编译器，只是特性上存在差异。在作业和实验中，一个好的遵从标准的 C 代码，由不同的编译器编译后不应当产生不同的运行结果。因此如果你使用 clang 编译 C 代码运行不符合预期，代码出问题的概率比 clang 特性出问题的概率大很多。
## Windows 修改环境变量

> Windows 用户环境变量配置出现问题了才需要看这一小节

检查一下环境变量，Win + R 键输入 `sysdm.cpl` 后回车，会出现 “系统属性” 界面，选择 “高级”，如下图所示：

<div style="text-align:center;">
<img src="../graph/env_var.png" alt="env_var" style="margin: 0 auto; zoom: 80%;"/>
</div>

打开环境变量，在 “系统变量” 或者 “用户变量” 中找到 `PATH` 变量，在其中增加一项 tdm-gcc 的路径。例如你如果默认安装 tdm-gcc，那么路径可能就是 `C:\TDM-GCC-64\bin`。