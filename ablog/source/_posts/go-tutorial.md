---
layout: post
title:  "Go 教程"
date:   2019-07-25 15:55:40 +0800
categories: Golang
---

#### Go 教程
Go是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。
Go是从2007年末由Robert Griesemer, Rob Pik, Ken Thompson主持开发，后来加入了
lan Lance Taylor, Russ Cox 等人，并最终于2009年11余额开源，在2012年早些时候发
布了Go1.0稳定版本。现在Go的开发已经是完全开放的，并且拥有一个活跃的社区。
* Go 语言特色
  * 简洁、快速、安全
  * 并行、有趣、开源
  * 内存管理、数组安全、编译寻思
* 语言用途
  Go 语言被设计成一门应用于搭建Web服务器，存储集群或者类似用途的巨型中烟服务器的系统编程语言。
  对于高性能分布式系统领域而言，Go语言无疑比大多数其他语言有着更公告的开发效率。它提供了海量
  并行的支持，对于游戏服务端的开发而言在合适不过了。
* 第一个Go程序

hello.go

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

运行 `go run` 命令执行

```shell
$ go run hello.go
hello, World!
```

此外还可以使用`go build` 命令生成二进制文件，再执行

```shell
$ go build hello.go
$ ls
hello hello.go
$ ./hello
Hello, World!
```

