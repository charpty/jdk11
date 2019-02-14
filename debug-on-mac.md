## 环境

- OSX版本：10.14.2 (18C54)

- 内核：Darwin AppledeMacBook-Pro.local 18.2.0 Darwin Kernel Version 18.2.0: Mon Nov 12 20:24:46 PST 2018; 

- Xcode版本：10.1 (10B61)

- 编译器版本：clang-1000.11.45.5

- 源码位置：https://hg.openjdk.java.net/jdk-updates/jdk11u



## 源码下载

不要使用hg clone，可以直接下载压缩包。

经实验，下载tar.gz相对来说成功可能性大点，大多数包下载的差不多了，剩下的包可以点进去小目录再下载。



只是为了编译调试hotspot的情况下，很多目录倒也没必要下载，正好这几个目录也比较大，比如test目录。



## 编译

jdk11在osx编译还是非常简单方便的。



先安装下依赖

```bash
brew install ccache
brew install freetype
```

然后进入顶层目录进行configure

```bash
sh configure --with-debug-level=slowdebug --disable-warnings-as-errors
```

之后进行make就行了

```c
make images
```

这个target会把java用的模块都编译出来。

最关键的是得到了`java`、`hotspot`这两个文件。



## 调试

不管使用Xcode还是Clion，过程原理都是一样的。

1. 将源码导入IDE

2. 执行编译结果中的`java`命令



- 想具体执行那个文件可以在程序参数中指定

- 如果需要改动hotspot源码，可以每次启动前让IDE执行一下make命令

- 如果还想class文件也是编译而来，同样的可以在每次启动前让IDE执行一下javac命令




