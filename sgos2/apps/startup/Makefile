#sgos apps

CXXFLAGS = -g -Werror -I../../include/c++ -I../../include -nostdlib -fleading-underscore --no-exceptions
LDFLAGS = 
ODFLAGS = -S

#here defines the program information
PROGRAM = startup
LDFLAGS += ../../crt/crt.a
LDFLAGS += ../../api/api.dll

CXX = gcc $(CXXFLAGS)
LD = ld $(LDFLAGS)
OD = objdump $(ODFLAGS)
LD2 = ../../tools/ld2/ld2
WF = ../../tools/wf/wf
IMAGE = ../../sgos2.img

OBJECTS = $(patsubst %.c,%.o,  $(wildcard *.c))

all: $(PROGRAM).exe

$(PROGRAM).exe: $(OBJECTS)
	$(LD) $(OBJECTS) -o$(PROGRAM).exe
	$(OD) $(PROGRAM).exe > $(PROGRAM).dmp
	$(WF) $(IMAGE) -src $@ -dest sgos/$@

# Standard Procedures
.c.o:
	$(CXX) -c -o $@ $<

clean:
	$(RM) $(OBJECTS)
	$(RM) $(PROGRAM).dmp
	$(RM) $(PROGRAM).exe
