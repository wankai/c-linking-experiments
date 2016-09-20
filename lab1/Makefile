CC=gcc
AR=ar
LD=ld

all: test1_alone, test1_static, test1_shared

test1_alone: test1.c
	$(CC) -c -o test1_alone test1.c

test1_static: test1.c libtest3.a
	$(CC) -c -o test1_static test1.c -L./ -ltest3

test1_shared: test1.c libtest4.so
	$(CC) -c -o test1_shared test1.c -L./ -ltest4
	
libtest3.a
	$(CC) -c test3.c
	$(AR)

libtest4.so
	$(CC) -shared -fPIC
	
clean:
	rm test1_alone
	rm test1_static
	rm test1_shared
	rm libtest2.a
	rm libtest4.so
