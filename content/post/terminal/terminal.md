---
title: "简单的终端操作 - Windows篇"
description: 
date: 2023-11-03T08:15:29Z
image: 
math: 
license: 
hidden: false
comments: true
categories:
    - random
tags:
    - terminal
---

## 认识终端

### 路径

终端界面通常是一个纯色的窗口，没有GUI，并且操作主要是输入命令。刚打开终端，通常会看到一行提示，内容大致如下（以命令提示符`cmd.exe`为例）：

`C:\Users\username>`

这里显示的路径为当前的所在目录，没有输入绝对路径的操作（绝对路径例如：`D:\Data\Videos\foo.mp4`）会被以相对路径方式处理，终端会在当前文件夹下寻找对应文件名的文件（如直接输入`bar.mp4`，则实际指向的文件是`C:\Users\username\bar.mp4`）。

### 更改路径

想要更改路径，可以使用命令 `cd 目的地路径`（例：`cd D:\Data\MyFiles`）。特别注意：在命令提示符（`cmd.exe`）下，如果目的地路径盘符与当前盘符不同（盘符例：`C:` 或 `D:` 或 `E:`），则需要再输入一行盘符（例如直接输入`D:`）来更改路径。

> 注：PowerShell下可以直接更改路径，无需输入盘符。**如无特殊需求，建议使用PowerShell进行操作，更加方便**

方便起见，在使用终端操作的时候，尽量把当前目录更改为你要进行操作的工作目录，这样就可以使用不用把绝对路径全部写出的相对路径，输入文件名即可，省时省力。

如果需要前进至某个目录，或者返回至上一个目录，可以参考以下方法：

前进：`cd .\NextFolder` \
返回至上一个目录（也称父目录）：`cd ..`

> 注：当前目录可以用一个英文句点 `.` 代替，而父目录可以用两个英文句点 `..` 代替。\
> 路径中的 `\` 和 `/` 如无特殊情况，一般含义相同

## 使用终端

### 运行程序

例：当前目录下有如下文件：

```text
    目录: D:\demo\folder


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         2023/11/3     16:46            204 archive.zip
-a----         2023/11/3     15:47       11134540 galaxy brain meme.mp4
-a----         2023/11/3     16:45              0 random.txt
-a----        2023/10/21     12:29         655275 test_cmd.exe
```

> 注：此处使用PowerShell操作。如无特殊说明，后文的操作均使用PowerShell进行。\
> 此处使用了 `ls` 命令进行查看，也可以使用 `dir` 命令，但是在命令提示符中则无法使用 `ls` 命令。\
> PowerShell的 `ls` 命令与其别名机制有关，命令输出的详细释义和命令本身的更多使用方法也会在日后进行介绍。

从 `Name` 一栏可以看出，目录下总共有$4$个文件：`archive.zip`，`galaxy brain meme.mp4`，`random.txt`，`test_cmd.exe`，输出按照字典序排序。现在，如果想使用`test_cmd.exe`对某个文件进行处理，可以使用如下命令：

`./test_cmd "galaxy brain meme.mp4" output.mp4`

在终端内运行`.exe`（或`.com`等）扩展名的应用程序时，可以省略扩展名。\
在引用文件名或路径含有空格的文件时，需要注意把整个路径用**双引号**（在PowerShell中也可为单引号）括起来，否则文件名会被空格分割，被识别为多个参数。

> 注：PowerShell中可以不加 `./` 前缀直接运行命令，但是由于其设置，在当前文件夹下的命令不能直接按照这种方式运行，否则会报出以下错误：

```text
test_cmd.exe : 无法将“test_cmd.exe”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ test_cmd.exe
+ ~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (test_cmd.exe:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

同时，PowerShell也会有以下提示：

```text
Suggestion [3,General]: 找不到命令 test_cmd.exe，但它确实存在于当前位置。默认情况下，Windows PowerShell 不会从当前位置加载命令。如果信任此命令，请改为键入“.\test_cmd.exe”。有关详细信息，请参阅 "get-help about_Command_Precedence"。
```

### 命令补全

在选择文件或者输入命令时，可以使用`Tab`键（`Tab`键一般位于`Caps Lock`大写锁定键的上方）进行命令补全，可以大大提升输入效率。

还是上面的例子，想要运行`test_cmd.exe`，可以先输入`test`（任意前缀都可以，但是前缀内容越详细，匹配的范围越小，找到想要命令或文件的速度越快），然后按下`Tab`键，此时就会自动补全`.\test_cmd.exe`命令。快速输入文件名同理。

如果文件夹下有多个相同前缀的文件名的文件，输入前缀后未必是你想要的文件，可以再次按下`Tab`键切换不同文件，直到变为目标文件为止。若文件过多，可以按照上文的操作扩充前缀。

### 强制终止

使用 `Ctrl + C` 键可以强制终止当前正在运行的进程，并返回到终端。在终端里输入命令时也可以随时按下 `Ctrl + C` 键来取消执行当前命令，清空输入。

> 注：在PowerShell中使用 `Ctrl + C` 键会使终端输出红色的 `^C` 以标注操作。
