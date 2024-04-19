TRIGGER_NAME := perf-trigger
GATHER_NAME := perf-gather
CC_x64 := x86_64-w64-mingw32-gcc
STRIP_x64 := x86_64-w64-mingw32-strip
CFLAGS := -masm=intel
TRIGGER_LIBS := -l pdh
GATHER_LIBS := -l advapi32

bof: bof_64
exe: exe_64
all: bof exe

bof_64:
	$(CC_x64) $(CFLAGS) -o dist/$(TRIGGER_NAME).x64.o -c src/$(TRIGGER_NAME).c -DBOF
	$(CC_x64) $(CFLAGS) -o dist/$(GATHER_NAME).x64.o -c src/$(GATHER_NAME).c -DBOF
	$(STRIP_x64) --strip-unneeded dist/$(TRIGGER_NAME).x64.o
	$(STRIP_x64) --strip-unneeded dist/$(GATHER_NAME).x64.o


exe_64:
	$(CC_x64) $(CFLAGS) -o dist/$(TRIGGER_NAME).x64.exe src/$(TRIGGER_NAME).c $(TRIGGER_LIBS)
	$(CC_x64) $(CFLAGS) -o dist/$(GATHER_NAME).x64.exe src/$(GATHER_NAME).c $(GATHER_LIBS)
	$(STRIP_x64) --strip-all dist/$(TRIGGER_NAME).x64.exe
	$(STRIP_x64) --strip-all dist/$(GATHER_NAME).x64.exe



clean:
	rm dist/*