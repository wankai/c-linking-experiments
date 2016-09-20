CC=gcc
AR=ar
LD=ld

all: test1_alone.o, test1_static.o, test1_shared.o

test1_alone.o: test1.c
	$(CC) -c -o test1_alone.o test1.c

test1_static.o: test1.c libtest3.a
	$(CC) -c -o test1_static.o test1.c -L./ -ltest3

test1_shared.o: test1.c libtest4.so
	$(CC) -c -o test1_shared.o test1.c -L./ -ltest4

test2.o: test2.c
	$(CC) -c test2.c
test3.o: test3.c
	$(CC) -c test3.c
test4.o: test4.c
	$(CC) -fPIC -c test4.c

libtest3.a: test3.o
	$(AR) crv libtest3.a test3.o
libtest4.so: test4.o
	$(CC) -shared -o libtest4.so test4.o
	
	

libtest4.so
	$(CC) -shared -fPIC
	
clean:
	rm test1_alone.o
	rm test1_static.o
	rm test1_shared.o
	rm libtest2.a
	rm libtest4.so
