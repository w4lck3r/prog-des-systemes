tous: lstar arrondi512
exec_tous: exec_arrondi512 exec_lstar

lstar: lstar.c
	gcc lstar.c -o lstar

exec_lstar:
	./lstar lstar.c

arrondi512: arrondi512.c
	gcc arrondi512.c -o arrondi512

exec_arrondi512:
	./arrondi512 arrondi512.c

clean: 
	rm -f lstar arrondi512

.PHONY:
	tous clean