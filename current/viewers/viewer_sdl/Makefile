# viewers/viewer_sdl/

# Compile options
SRCDIR = ../../src
INCLUDEDIR = ../../include
CC = gcc
#CFLAGS = -O2 -Wall -Werror -W $(INCLUDE) `sdl-config --cflags`
CFLAGS = -g -O0 -Wall -Werror -W $(INCLUDE) `sdl-config --cflags`
INCLUDE = -I$(INCLUDEDIR)
LDFLAGS = -L/usr/X11/lib
ifeq ($(OS),Windows_NT)
LDLIBS = `sdl-config --libs` -lopengl32 -lwsock32
else
LDLIBS = `sdl-config --libs` -lGL
endif


TARGET = viewer_sdl

all : $(TARGET)

clean :
	$(RM) $(TARGET) *.o

depend :
	makedepend -Y -- $(INCLUDES) -- $(wildcard *.h *.c)

.PHONY : all clean depend
######################################################################
REQUIRE_LIB = $(SRCDIR)/liburg_c.a
$(REQUIRE_LIB) : $(wildcard $(SRCDIR)/*.[ch])
	cd $(@D)/ && $(MAKE) $(@F)

viewer_sdl : plotter_sdl.o $(REQUIRE_LIB)

# DO NOT DELETE

plotter_sdl.o: plotter_sdl.h
viewer_sdl.o: plotter_sdl.h
