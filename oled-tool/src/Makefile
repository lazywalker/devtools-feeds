BIN		= oled
CC      = gcc
CFLAGS  = -g -O3 -Wall
LDFLAGS = -g

OBJECTS = i2c_oled_128x64.o main.o msg_common.o

all:	BIN

BIN:	$(OBJECTS)
		$(CC) $(OBJECTS) $(CFLAGS) $(LIBS) -o $(BIN)

%.o: %.cpp
		$(CC) $(CFLAGS) -c -o $@ $<

install:
		install -m 755 $(BIN) /usr/local/bin/

clean:
		$(RM) $(BIN) *.o *.d *.bak *~
 
