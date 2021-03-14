
TARGET = ardpicprog
MANPAGE = ardpicprog.1
VERSION = 1.8.horo

PREFIX = /usr
BINDIR = $(PREFIX)/bin
MANDIR = $(PREFIX)/share/man

MKDIR_P = mkdir -p
RM_F = rm -f

SOURCES = hexfile.cpp main.cpp serialport.cpp serialport_posix.cpp
OBJECTS = hexfile.o main.o serialport.o serialport_posix.o

CXXFLAGS = -g -Wall -DARDPICPROG_VERSION=\"$(VERSION)\"

LDFLAGS += -g -lstdc++

all:	$(TARGET)

$(TARGET):	$(OBJECTS)
	$(CXX) -o $(TARGET) $(OBJECTS) $(LDFLAGS)

install: all
	$(MKDIR_P) $(BINDIR)
	$(MKDIR_P) $(MANDIR)/man1
	install -c -o 0 -g 0 -m 755 $(TARGET) $(BINDIR)/
	install -c -o 0 -g 0 -m 644 $(MANPAGE) $(MANDIR)/man1/

uninstall:
	$(RM_F) $(BINDIR)/$(TARGET)
	$(RM_F) $(MANDIR)/man1/$(MANPAGE)

clean:
	$(RM_F) $(TARGET) $(TARGET).exe $(OBJECTS)

deb:	all
	fakeroot checkinstall --default --pkggroup=electronics --install=no --backup=no --deldoc=yes


hexfile.o: hexfile.h serialport.h
main.o: serialport.h hexfile.h
serialport.o: serialport.h
serialport_posix.o: serialport.h
