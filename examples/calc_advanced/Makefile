CC=c++
CFLAGS=-Wall -Wextra -I/opt/local/include -I../../parser -ggdb3 -std=c++11

run.exe: calc_advanced.cpp lex.yy.o
	$(CC) $(CFLAGS) -o run.exe calc_advanced.cpp lex.yy.o

debug: calc_advanced.cpp lex.yy.o
	$(CC) $(CFLAGS) -o debug calc_advanced.cpp lex.yy.o -DDEBUG=

lex.yy.o: lex.yy.c
	cc -c lex.yy.c

lex.yy.c: calc_advanced.l
	flex calc_advanced.l

clean:
	rm *.o *.dot *.png debug run.exe lex.yy.c valgrind-out.txt

valgrind:
	valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes --verbose --log-file=valgrind-out.txt ./run.exe
