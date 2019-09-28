---
layout: post
title:  "Go 语言环境安装"
date:   2019-07-25 16:39:40 +0800
categories: Golang
---
##### Go语言支持以下系统：

* Linux
* FreeBSD
* macOS
* Windows

安装包下载地址：https://golang.org/dl/

官网安装教程：https://golang.org/doc/install

##### Windows 系统下安装

Windows下可以使用.msi后缀直接安装。

默认情况下.msi文件会安装在C:\Go目录下，可以将C:\Go\bin目录添加到Path环境变量中(怎么添加自行search)。添加后需要重启命令窗口才能生效。

* 安装测试

创建工作目录GoWorkSpace

test.go

```go
package main
import "fmt"
fun main() {
    fmt.Println("Hello, World!")
}
```

使用go命令执行结果如下：

```shell
C:\GoWorkSpace>go run test.go
Hello, World!
```

##### UNIX/Linux/Mac OS/FreeBSD 安装

[下载](https://golang.org/dl/ "安装包")对应的安装包并解压到`/usr/local`,然后创建一个go文件夹，例如：

```shell
$ tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

接下来把`/usr/local/go/bin`加到path变量里面，根据自己的系统把下面这一行添加进去(有可能是.zshrc或者.bashrc或者.profile)

```
export PATH=$PATH:/usr/local/go/bin
```

##### macOS 安装包安装

[下载](https://dl.google.com/go/go1.12.7.darwin-amd64.pkg "安装包")对应的安装，默认会安装到`/usr/loacl/go`地址下。

