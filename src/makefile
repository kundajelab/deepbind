SHELL := /bin/bash

all: ../deepbind

../deepbind: deepbind.c
	@gcc -o ../deepbind -O3 -DNDEBUG -Wno-unused-result -Wno-format-security deepbind.c -lm

clean:
	@rm ../deepbind
