# 问题描述

一个C源文件中引用了一个外部变量，gcc在编译这个源文件的时候怎么确定此变量是
* 同项目内的, or
* 静态库中的, or
* 共享库中的 ？

# 结论

编译器不在乎引用的全局变量在哪里定义

# 实验

## 实验1

**环境：** Apple LLVM version 7.3.0 (clang-703.0.31)

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

**结论：**

编译时不需要链接库信息
