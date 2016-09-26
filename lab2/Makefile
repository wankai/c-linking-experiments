all: test1

test1: test1.c libtest2.so
  gcc -o test1 test1.c -L./ -ltest2
  
libtest2.so: test2.c
  gcc -shared -fPIC -o libtest2.so test2.c
