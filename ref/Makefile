CC ?= /usr/bin/cc
CFLAGS += -Wall -Wextra -Wpedantic -Wmissing-prototypes -Wredundant-decls \
  -Wshadow -Wvla -Wpointer-arith -O3 -fomit-frame-pointer
NISTFLAGS += -Wno-unused-result -O3 -fomit-frame-pointer

SOURCES = sign.c packing.c polyvec.c poly.c ntt.c reduce.c rounding.c fips202.c symmetric-shake.c
OBJECTS = $(SOURCES:.c=.o)
HEADERS = config.h params.h api.h sign.h packing.h polyvec.h poly.h ntt.h \
  reduce.h rounding.h symmetric.h randombytes.h fips202.h

.PHONY: all clean

all: libdilithium.so

libdilithium.so: $(OBJECTS)
	$(CC) -shared -o $@ $(OBJECTS)

%.o: %.c $(HEADERS)
	$(CC) $(CFLAGS) -fPIC -c $< -o $@

clean:
	rm -f *.o libdilithium.so