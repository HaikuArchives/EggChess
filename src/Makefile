#No nonsense generic BeOS makefile for Eggchess

LIBS = -L/boot/develop/tools/gnupro/lib -lSDL
CLIBS = -L/boot/develop/tools/gnupro/lib -lSDL -ISDL_image

OBJECTS = ./objects/sge_surface.o ./objects/sge_primitives.o ./objects/sge_tt_text.o ./objects/sge_bm_text.o ./objects/sge_misc.o ./objects/sge_textpp.o ./objects/sge_blib.o ./objects/sge_rotation.o ./objects/sge_collision.o ./objects/sge_shape.o ./objects/eggchess.o



#begin gather the hardware info....
MACHINE = $(shell uname -m)
ifeq ($(MACHINE), BePC)
	CPU = x86
	CFLAGS = -O9 -I. -g -I/boot/system/develop/headers/SDL -I/boot/develop/tools/gnupro/include -Wall -ffast-math $(shell sdl-config --cflags)
	STRIP = strip ../eggchess.x86 --strip-all
else
	CPU = ppc
	CFLAGS = -I. -g -I/boot/system/develop/headers/SDL -I/boot/develop/tools/gnupro/include
	STRIP = echo "Not on the PPC matey ;-)"
endif
#end hardware info...

#build rules

eggchess: sge_surface.o sge_primitives.o sge_tt_text.o sge_bm_text.o sge_misc.o sge_textpp.o sge_blib.o sge_rotation.o sge_collision.o sge_shape.o eggchess.o
	$(CC) -o ../eggchess.$(CPU) $(OBJECTS) $(CFLAGS) $(CLIBS) $(RESFILE)
	rm objects/*.o
	$(STRIP)

eggchess.o: eggchess.cpp
	$(CC) $(CFLAGS)  -o ./objects/eggchess.o -c eggchess.cpp 

sge_surface.o: sge_surface.cpp sge_surface.h
	$(CC)  $(CFLAGS) -o ./objects/sge_surface.o -c sge_surface.cpp

sge_primitives.o: sge_primitives.cpp sge_primitives.h
	$(CC)  $(CFLAGS) -o ./objects/sge_primitives.o -c sge_primitives.cpp

sge_tt_text.o: sge_tt_text.cpp sge_tt_text.h
	$(CC)  $(CFLAGS) -o ./objects/sge_tt_text.o -c sge_tt_text.cpp

sge_bm_text.o:  sge_bm_text.cpp sge_bm_text.h
	$(CC)  $(CFLAGS) -o ./objects/sge_bm_text.o -c sge_bm_text.cpp 

sge_misc.o: sge_misc.cpp sge_misc.h
	$(CC)  $(CFLAGS) -o ./objects/sge_misc.o -c sge_misc.cpp  

sge_textpp.o: sge_textpp.cpp sge_textpp.h
	$(CC)  $(CFLAGS) -o ./objects/sge_textpp.o -c sge_textpp.cpp 

sge_blib.o: sge_blib.cpp sge_blib.h
	$(CC)  $(CFLAGS) -o ./objects/sge_blib.o -c sge_blib.cpp 

sge_rotation.o: sge_rotation.cpp sge_rotation.h
	$(CC)  $(CFLAGS) -o ./objects/sge_rotation.o -c sge_rotation.cpp  

sge_collision.o: sge_collision.cpp sge_collision.h
	$(CC)  $(CFLAGS) -o ./objects/sge_collision.o -c sge_collision.cpp 

sge_shape.o: sge_shape.cpp sge_shape.h
	$(CC)  $(CFLAGS) -o ./objects/sge_shape.o -c sge_shape.cpp 
