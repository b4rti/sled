# Makefile for sled modules.
MODULES = random_static.so twinkle.so text.so random_rects.so fish.so

CC ?= cc
CFLAGS := -std=gnu99 -O2 -Wall -Wno-unused-command-line-argument
CPPFLAGS += -I..

OS := $(shell uname)
ifeq ($(OS),Linux)
	LIBS += -ldl
endif

DEFINES := -DISMODULE $(DEFINES)

all: $(MODULES)

# Common rules
%.so: %.o
	$(CC) -fPIC -shared $(CFLAGS) $(LDFLAGS) $(LIBS) -o $@	$^

%.o: %.c
	$(CC) -c -fPIC $(CFLAGS) $(CPPFLAGS) $(LDFLAGS)	$(DEFINES)	$^	-o $@

# Include files go here
%.c: font.h ../main.h ../matrix.h ../modloader.h ../plugin.h ../random.h ../timers.h ../types.h

# Module specific stuffs
fish.so: LDFLAGS += -pthread
