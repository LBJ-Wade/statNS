Basic method to compile and use statNS code in C langugue (QUICK compile):
gcc test.c lib/libstatNS.so -o test.out

There are disadvantages in using the QUICK compile command. The compiled binary is dynamically linked with the library file libstatNS.so through relative path, so you can NOT change the relative position bewteen your binary output test.out and the libaray file lib/libstatNS.so, or you will fail to run test.out. What's more, you can only perform the compile at the current path, or your programe can't link to lib/libstatNS.so correctly.

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

If you want to make changes to the library, you can modify its source code src/statNS.c, then re-compile it like this:
gcc src/statNS.c -lm -lpthread -shared -fPIC -o lib/libstatNS.so

re-compile the library is necessary for the following reasons:
1) libstatNS.so is damaged or incompatiable with your operation system, it needs to be re-compiled
2) you want to change some function or add your own function in the library
