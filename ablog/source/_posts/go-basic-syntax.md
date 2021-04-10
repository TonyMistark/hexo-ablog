---
layout: post
title:  "Go 语言基础语法"
date:   2020-04-10 16:39:40 +0800
categories: Golang
---

#### Go标记
go语言程序可以由多个标记组成，可以是关键字，标识符，常量，字符串，符号。
如一下Go语句由6个标记组成：
```golang
fmt.Println("Hello, World!")
```
6个标记：
1. fmt
2. .
3. Println
4. (
5. "Hello, World!"
6. )

##### 行分隔符
在Go程序中，一行嗲表一个语句结束。每个语句不需要像C家族中的其他语言一样
以分号；结尾，因为这些工作都将由Go编译器完成。
如果你打算将多个语句卸载一行，它们必须只用；认为的区分开，但在实际开发中
我们并不鼓励这种做法。
一下为两个语句：
```golang
fmt.Println("Hello, World")
fmt.Println("Hi, my world")
```
#### 注释
```golang
// 单行注释
/*
多行
注释
*/
```
#### 标识符
标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或者是多个
字母（A-Z和a-z）下划线_组成的序列，但是第一个字符必须是字母或者下换线而不能是数字。

#### 字符串连接
Go语言的字符串可以通过`+`实现：
```golang
package main
import "fmt"
func main () {
    fmt.Println("Google" + "Baidu")
}
```

#### 关键字

下面列举了Go代码中会使用的25个关键字或者保留字：
break, default func, interface, select, 
case, defer, go, map, struc,
chan, else, goto, package, switch,
const, fallthrough, if, range, type,
continiue, for, import, return, var

除了以上介绍的这些关键词，Go语言还有36个预定义标识符：
append, bool, byte, cap, close, complex, complex64, complex128, uint16,
copy, false, float32, float64, imag, int, int8, int16, uint32,
int32, int64, iota, len, make, new, nil, panic, uint64, 
print, println, real, recover, string, true, uint, uint8, uintptr
程序一般由关键字、常量、变量、运算符、类型和函数组成。
程序中可能使用到这些分隔符：括号(), 类型和大括号{}
程序组可能会使用到这些标点符号.、,、;、: 和 …。

#### Go语言的空格
Go语言中变量的声明必须使用空格隔开，如：`var age int;`

### 格式化字符串
Go语言中使用`fmt.Sprintf`格式化字符串并赋值给新串：
````golang
package main
package main


import "fmt"


func main() {
    var stockcode= 123
    var enddate = "2021-04-10"
    var url = "Code=%d&endDate=%s"
    var target_url = fmt.Sprintf(url, stockcode, enddate)
    fmt.Println(target_url)
}
````
输出结果：
`Code=123&endDate=2021-04-10`
