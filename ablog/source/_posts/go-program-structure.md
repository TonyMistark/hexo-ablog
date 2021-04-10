---
layout: post
title:  "Go 语言结构"
date:   2019-07-25 16:39:40 +0800
categories: Golang
---
在我们开始学习Go编程语言的基础构建模块钱，让我们先来了解Go语言最简单程序的结构。

#### Go Hello World
Go 语言的基础组成有以下几个部分：
* 包声明
* 引入包
* 函数
* 变量
* 语句 & 表达式
* 注释
接下来让我们来看下简单代码，该代码输出了"Hello World"：
```golang
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

让我妈来看一下上面的程序各个部分：
1.第一行代码package main 定义了包命。你必须在源文件中非注释的第一行指明
这个文件属于哪个包，如：package main。package main 表示一个可以独立
执行的程序，每个Go应用程序都包含一个名为main的包。
2.下一行 import "fmt" 告诉Go编译器这个程序需要fmt包（的函数，或者其他元素），
fmt包实现了格式化IO（输入输/出）的函数。
3.下一行func main() 是程序开始执行的函数。main函数是每个可执行程序所必须包含的，
一般来说都是在启动后第一个执行的函数（如果有init()函数则会先执行该函数）。
4.下一行/* */是注释
5.下一行fmt.Println()可以将字符串输出到控制台，并在最后自动增加换行符\n。
Print和Println两个函数也支持使用变量，如：fmt.Println(arr)。如果没有特别指定，
它们会以默认的打印格式将变量arr输出到控制台。
6.党标识符（包括常量、变量、类型、函数名、结构字段等等）以一个大写字母开头，如：Group，
那么使用这种形式的标识符的对象就可以被外部包的代码使用（客户端程序需要先导入这个包），
这被称为导出（就像面向对象语言的public）；标识符如果以小写字母开头，则对包外是不可见的，
但是他们整个包的内容部是可见并且可用的（像面向对象语言中的protected）。

#### 执行Go程序
让我们来看下如何编写Go代码并自行它，步骤如下：
1.打开编辑器如vim，编写代码
2.将代码保存为hello.go
3.打开终端（terminal）命令行，并进入程序文件保存的目录中。
4.输入命令go run hello.go 并回车执行代码。
5.如果操作正确，你讲在屏幕上看到"Hello，World！字样的输出。
```golang
$ go run hello.go
Hello, World!
```
6.我们还可以使用`go build`命令来生成二进制文件：
```golang
$ go build hello.go
$ ls
hello hello.go
$ ./hello
Hello, World!
```