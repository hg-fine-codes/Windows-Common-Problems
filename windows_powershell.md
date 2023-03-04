# Windows PowerShell的使用总结

/*

* File: windows_powershell.md
* Project: windows总结
* File Created: Wednesday, 10th November 2021 7:33:18 pm
* Author: Hanlin Gu (hg_fine_codes@163.com)
* -----
* Last Modified: Saturday, 4th March 2023 4:29:00 pm
* Modified By: Hanlin Gu (hg_fine_codes@163.com>)
 */

<!-- TOC -->

* [1. 快捷键](#1-快捷键)
  * [1.1. 显示当前文件夹的路径 pwd](#11-显示当前文件夹的路径-pwd)
  * [1.2. 列举文件加的内容 ls or dir](#12-列举文件加的内容-ls-or-dir)
  * [1.3. 清空命令行上面的显示 clear](#13-清空命令行上面的显示-clear)
  * [1.4. 路径中的符号](#14-路径中的符号)
    * [1.4.1. 用户主目录 ~](#141-用户主目录-)
    * [1.4.2. 根目录 /](#142-根目录-)
    * [1.4.3. 当前目录 ./ or](#143-当前目录--or)
    * [1.4.4. 上一级目录 ../](#144-上一级目录-)
  * [1.5. 进入某个或退出某个目录 cd](#15-进入某个或退出某个目录-cd)
  * [1.6. 建立目录 mkdir](#16-建立目录-mkdir)
  * [1.7. 移动目录与文件 mv](#17-移动目录与文件-mv)
  * [1.8. 复制目录与文件 cp](#18-复制目录与文件-cp)
    * [1.8.1. 将test.md文件复制到相同目录下](#181-将testmd文件复制到相同目录下)
    * [1.8.2. 将test.md文件复制到桌面目录下](#182-将testmd文件复制到桌面目录下)
  * [1.9. 删除目录与文件 rm](#19-删除目录与文件-rm)
  * [1.10. 重命名文件夹和文件 ren](#110-重命名文件夹和文件-ren)
    * [1.10.1. 在同一文件夹中重命名文件夹或者文件](#1101-在同一文件夹中重命名文件夹或者文件)
    * [1.10.2. 重命名任意文件中的文件夹或者文件](#1102-重命名任意文件中的文件夹或者文件)
  * [1.11. 查询Windows Powershell指令和说明文件 get-help](#111-查询windows-powershell指令和说明文件-get-help)
* [2. 打开Windows PowerShell](#2-打开windows-powershell)
* [3. 从PowerShell中打开文件夹](#3-从powershell中打开文件夹)
  * [3.1. 打开当前目录](#31-打开当前目录)
* [4. 创建新的文件夹和文件](#4-创建新的文件夹和文件)
  * [4.1. 创建新的文件夹](#41-创建新的文件夹)
  * [4.2. 创建新的文件](#42-创建新的文件)
* [5. 打开文件](#5-打开文件)

<!-- /TOC -->

<div style="page-break-after:always"></div>

## 1. 快捷键

### 1.1. 显示当前文件夹的路径 pwd

```powershell
pwd
```

```powershell
Path
----
E:\操作系统总结\windows总结
```

### 1.2. 列举文件加的内容 ls or dir

```powershell
ls

dir
```

```powershell
目录: E:\操作系统总结\windows总结
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          2021/7/1     10:58              0 windows_power_shell.md
```

### 1.3. 清空命令行上面的显示 clear

```powershell
clear
```

### 1.4. 路径中的符号

#### 1.4.1. 用户主目录 ~

操作系统会为每个登录到系统上的用户分配一个特定的目录，这个目录的名字一般跟用户的名称是一样的，在这个目录的下面，会存放属于这个用户的文档。这个目录就是用户的主目录，这个目录在命令行里面，用~来表示。

```powershell
cd ~
```

#### 1.4.2. 根目录 /

一个斜线（/），表示系统的根目录，Windows 上表示的是在某个盘符下的根目录，比如**ls /** 这条命令会显示出*C盘根目录下面的所有的东西*。Mac与Linux上都表示的是系统的根目录。

```powershell
cd /
```

#### 1.4.3. 当前目录 ./ or

./  或者 . ，表示当前目录，比如你要*处理当前目录下面的东西*，可以在路径的前面加上 ./ ，比如上面介绍的 ls 命令，你想列出当前目录下面的东西，可以用 ls ./ ， 不过*一般可以省略掉它*，直接用 ls 命令就表示要显示当前目录下面的东西。

```powershell
ls ./
```

#### 1.4.4. 上一级目录 ../

你想处理你所在位置的上一级别的目录里的东西，可以在路径的一开始用一个 ../， 比如想要**显示当前目录的上一个级别里的东西**，可以输入  ls ../。一个 ../ 就表示前一个级别的目录，前两个级别就是 ../../。

```powershell
ls ../
```

### 1.5. 进入某个或退出某个目录 cd

```powershell
cd folder_address
```

### 1.6. 建立目录 mkdir

在指定的地方创建一个新的目录，可以使用 mkdir （make directory），后面加上要创建的目录的名字：mkdir 目录名  我现在的位置是在桌面上，打算在桌面上创建一个叫 projects 的目录：mkdir projects 如果需要创建一个目录结构，就是你可能想要在某个目录下面，再创建一个子目录。  Windows 上，可以直接在 mkdir命令的后面加上要创建的目录的路径，这个路径上面的所有的目录，如果还不存在 ，就会去创建一个。

### 1.7. 移动目录与文件 mv

把目录或者文件移动到一个新的地方，用的是 mv （move）命令，这个命令也可以用来重命名目录或者文件。
命令的后面先是要移动的东西，再用一个空格，然后接着是移动到的新的位置。

```powershell
mv address/file_name.file_format new_address
```

### 1.8. 复制目录与文件 cp

cp（copy）命名可以复制指定的文件或者目录，先指定一下要复制的东西，空格分隔一下，接着是要复制到的位置。

#### 1.8.1. 将test.md文件复制到相同目录下

```powershell
cp .\test.md test_copy.md
```

#### 1.8.2. 将test.md文件复制到桌面目录下

```powershell
cp .\test.md C:\Users\admin\Desktop
```

### 1.9. 删除目录与文件 rm

要把指定的目录或者文件删除掉，用的是 rm （remove）命令，在它后面加上要删除掉的东西就行了，在删除目录的时候，需要用一个 -r 参数，另外，可以再加上一个 -f 参数，这样在删除目录里的文件的时候不会出现提示。注意在 Windows Powershell 上面用 rm 命令，不需要使用参数。

```powershell
rm file_name or folder_name
rm -r folder_name
```

### 1.10. 重命名文件夹和文件 ren

#### 1.10.1. 在同一文件夹中重命名文件夹或者文件

```powershell
ren file_name_1 file_name_2
```

#### 1.10.2. 重命名任意文件中的文件夹或者文件

将文件夹path中，名为file_name_1的文件重命名为file_name_2

```powershell
ren path/file_name_1 file_name2
```

### 1.11. 查询Windows Powershell指令和说明文件 get-help

get-help 是颇为重要的 cmdlet，可以查询所有的 Windows PowerShell 指令和说明文件。例如：

* get-help \*：列出所有的主题，包括指令和概念。
* get-help \* | more：列出所有的主题，包括指令和概念，而且显示满整个视窗就暂停。
* get-help about\*：列出所有的概念主题。
* get-help get\*：列出所有 get开头的主题。
* get-help {<指令名称或主题名称>}：列出指定的指令或主题的说明，例如 get-help dir 可以查询 dir 指令的用法。

## 2. 打开Windows PowerShell

## 3. 从PowerShell中打开文件夹

打开E盘的“操作系统总结”文件夹

```'powershell
cd 'E:\操作系统总结'
```

### 3.1. 打开当前目录

弹出Powershell当前的文件夹

```powershell
start .
```

## 4. 创建新的文件夹和文件

### 4.1. 创建新的文件夹

```powershell
mkdir folder_name
```

### 4.2. 创建新的文件

```powershell
new-item file_name.file_format -type file
```

## 5. 打开文件

```powershell
./file_name.file_format
```
