# statNS

在你的C语言程序中调用statNS库的初等方法：

gcc example/test.c lib/libstatNS.so -o test.out

使用这一方法调用该库存在弊端，即test.out和lib/libstatNS.so的相对位置不能改变，否则你无法运行test.out

而且引用statNS.h的时候必须要注意你的代码源文件只能在当前位置进行编译。

确保一切正常后，运行./test.out查看结果，

这里我没来得及说明库函数究竟都是做什么用的，

希望test.c这个简单的demo能让你理解：

1)如何合法地调用它们

2)程序运行的结果保存在哪里。


如果你希望能长期部署statNS库，以致于你能在任何地方能像对待math.h那般进行操作，请你在拥有sudo权限的情况下运行以下命令：

sudo cp lib/* /usr/lib64/

sudo cp src/*.h /usr/include/

如此一来，程序的开头引用#include "src/statNS.h"可以直接改为#include <statNS.h>，而编译命令则需要改为：

gcc example/test.c -lstatNS -o test.out

这样你的代码源文件可以任意位置进行编译，而且编译得到的test.out也不受位置束缚，它可以移动到你计算机上的任意位置运行。


如果此代码对你有帮助，请规范引用我们的工作：

DOI https://doi.org/10.1103/PhysRevC.99.045806

# English version:
========================

Simplest way to compile and use statNS code in C langugue (QUICK compile):

gcc test.c lib/libstatNS.so -o test.out

There are disadvantages in using the QUICK compile command. The compiled binary is dynamically linked with the library file libstatNS.so through relative path, so you can NOT change the relative position bewteen your binary output test.out and the libaray file lib/libstatNS.so, or you will fail to run test.out. What's more, you can only perform the compile at the current path, or your programe won't link to lib/libstatNS.so correctly.

Run ./test.out to check the results,
I'm sorry for the bad description in this code.
Hope the simple demo written in test.c can help you understand:
1) how to call the lib function correctly,
2) which variable will store the computation results.

If you want to deploy statNS library so that you can treat it like <math.h> in C standary library, you may run the following command with sudo privilege:

sudo cp lib/* /usr/lib64/

sudo cp src/*.h /usr/include/

After deploy, you are allowed to use #include <statNS.h> to replace the current statement #include "src/statNS.h", and the compile command need to change as (FIRM compile):

gcc test.c -lstatNS -o test.out

Using the FIRM compile command will allow you to compile your own .c files at any path, and allow the output binary files to run at any path on your device.

If you found this code helpful, please cite our work correctly:

DOI https://doi.org/10.1103/PhysRevC.99.045806
