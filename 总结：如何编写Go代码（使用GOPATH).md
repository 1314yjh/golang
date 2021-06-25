# 总结：如何编写Go代码（使用GOPATH)
原文：https://golang.org/doc/gopath_code 

## 简介

本文档演示了一个简单的Go包的开发，并介绍了go工具(也就是命令行里面的go命令，正常安装好go环境，就有这个命令)，go工具是获取、构建和安装Go包和命令的标准方式。
 
go工具要求你以一种特定的方式组织你的代码。请仔细阅读本文档。它解释了最简单的方法来启动和运行你的Go安装。

## 代码结构

### 概述

1. Go程序员通常将所有的Go代码保存在一个工作区。
2. 一个工作区包含许多版本的代码仓库（例如由Git管理）。
3. 每个代码仓库包含一个或多个包。
4. 每个包放在一个目录中，目录下面由一个或多个 Go 源文件组成。
5. 一个包的目录路径决定了它的导入路径。

请注意，这与其他编程环境不同。在其他编程环境中，每个项目都有一个独立的工作空间，工作空间与版本控制库紧密相连。

### 工作空间(workspaces)

一个工作空间是一个根部下面有两个目录的层次结构:
1. src 目录包含go源码文件
2. bin 目录包含可执行命令

go工具编译并安装二进制文件到bin目录。

src下面通常包含多个版本控制仓库(比如git),跟踪一个或者多个源码包的开发。

为了让你了解工作区的实际情况，这里有一个例子。

```
bin/
    hello                          # command executable - 可执行命令
    outyet                         # command executable - 可执行命令
src/
    github.com/golang/example/
        .git/                      # Git repository metadata  - Git 仓库元数据
        hello/
            hello.go               # command source - 命令的源码
        outyet/
            main.go                # command source - 命令的源码
            main_test.go           # test source - 测试代码
        stringutil/
            reverse.go             # package source - 包源码
            reverse_test.go        # test source - 测试代码
    golang.org/x/image/
        .git/                      # Git repository metadata
        bmp/
            reader.go              # package source - 包源码
            writer.go              # package source - 包源码
    ... (many more repositories and packages omitted) ... - 省略了更多的存储库和软件包
    
```
上面的树结构展示了一个工作区包含2个仓库(example 和 image).










