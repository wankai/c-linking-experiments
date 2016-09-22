# 问题描述

一个C源文件中引用了一个外部变量，gcc在编译这个源文件的时候怎么确定此变量是
* 同项目内的, or
* 静态库中的, or
* 共享库中的 ？

# 实验1

**环境：** 

```bash
Apple LLVM version 7.3.0 (clang-703.0.31)
```

**步骤：**

```bash
1. make
```


**输出：**

```bash
gcc -c -o test1_alone.o test1.c
gcc -c test3.c
ar crv libtest3.a test3.o
a - test3.o
gcc -c -o test1_static.o test1.c -L./ -ltest3
clang: warning: -ltest3: 'linker' input unused
clang: warning: argument unused during compilation: '-L./'
gcc -fPIC -c test4.c
gcc -shared -o libtest4.so test4.o
gcc -c -o test1_shared.o test1.c -L./ -ltest4
clang: warning: -ltest4: 'linker' input unused
clang: warning: argument unused during compilation: '-L./'
```

**分析：**

编译器对 -L 和 -l 选项都告警，表明编译器并不需要这些信息。也就是说编译器不在乎引用的全局变量定义在项目内、静态库还是共享库。

**结论：**

源文件只知道引用了全局变量，不在乎它定义在哪里


# 实验2
