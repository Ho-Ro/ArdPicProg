
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

.PHONY: all
all:	$(TARGET)

$(TARGET):	$(OBJECTS)
	$(CXX) -o $(TARGET) $(OBJECTS) $(LDFLAGS)

.PHONY: install
install: $(TARGET) $(MANPAGE)
	$(MKDIR_P) $(BINDIR)
	$(MKDIR_P) $(MANDIR)/man1
	install -c -o 0 -g 0 -m 755 $(TARGET) $(BINDIR)/
	install -c -o 0 -g 0 -m 644 $(MANPAGE) $(MANDIR)/man1/

.PHONY: uninstall
uninstall:
	$(RM_F) $(BINDIR)/$(TARGET)
	$(RM_F) $(MANDIR)/man1/$(MANPAGE)

.PHONY: clean
clean:
	$(RM_F) $(TARGET) $(TARGET).exe $(OBJECTS) *~

.PHONY: deb
deb:	$(TARGET) $(MANPAGE)
	fakeroot checkinstall --default --pkggroup=electronics --install=no --backup=no --deldoc=yes

.PHONY: debinstall
debinstall:
	sudo dpkg -i `ls ardpicprog_*_amd64.deb | tail -1`

hexfile.o: hexfile.h serialport.h
main.o: serialport.h hexfile.h
serialport.o: serialport.h
serialport_posix.o: serialport.h
