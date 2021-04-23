CC = gcc

CC_FLAGS = -pedantic -Wall
LD_FLAGS = -lzmq -L. 

CC_LIB_FLAGS = -c -pedantic -Wall -fPIC
LD_LIB_FLAGS = -shared -lzmq

all: server client

server : server.c libtools.so
	$(CC) $(CC_FLAGS) server.c -o server $(LD_FLAGS) -ltools

client : client.c libtools.so
	$(CC) $(CC_FLAGS) client.c -o client $(LD_FLAGS) -ltools

libtools.so : zmq_comm.o
	$(CC) zmq_comm.o -o libtools.so $(LD_LIB_FLAGS)

zmq_comm.o : zmq_comm.c
	$(CC) $(CC_LIB_FLAGS) zmq_comm.c

clean:
	rm -f *.o *.so server client
