CC=g++
CPPFLAGS=-std=c++14
CFLAGS=-O3 -g -Wall -fmessage-length=0 -fopenmp -mavx -maes -mtune=native

WHICH				:= $(shell which which)
MKDIR				:= $(shell $(WHICH) mkdir)
DIRNAME				:= $(shell $(WHICH) dirname)

CFLAGS+=-mpclmul
CPPFLAGS+=-mpclmul
INCFLAGS=-Isrc
TARGET=$(BLDDIR)/libFFT.a

SRCS:= $(shell ls src/*.cpp)
OBJS=$(addprefix $(BLDDIR)/, $(SRCS:.cpp=.o))

$(BLDDIR)/%.o: %.cpp
#	@echo 'Building file: $@ ($<)'
	@$(MKDIR) -p $(shell $(DIRNAME) $@)
	$(CC) $(CFLAGS) $(CPPFLAGS) $(INCFLAGS) -c -o "$@" "$<"

all: $(TARGET)

clean:
	$(RM) -f $(TARGET) $(OBJS) $(DEPS)

$(TARGET): $(OBJS)
#	@echo 'Building target: $@'
	ar -r  "$@" $(OBJS) $(LIBS)
