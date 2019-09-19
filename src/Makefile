
NAME=ws2_32.dll

OBJOPT=
LNKOPT= -lws2_32 -liphlpapi -static -shared
CC=i686-w64-mingw32.static-gcc


#####################################################################################
#Don't change anything below. Unless you know what you are doing.
#####################################################################################
SRC_LIST_C=$(wildcard *.c)
SRC_LIST_CPP=$(wildcard *.cpp)
SRC_LIST=$(SRC_LIST_C) $(SRC_LIST_CPP)
OBJs=$(SRC_LIST_C:.c=.o) $(SRC_LIST_CPP:.cpp=.o)
STAMP=$(shell date +%Y%m%d-%H%M%S )
V ?= 0

ifeq ($(V),0)
SILENT:=--silent
endif
verbose = $(verbose_$(V))
verbose_0 = @set -e;

%.o: %.c
	$(verbose)echo "  GEN [$@]";\
	$(CC) -D VDATE=\"$(STAMP)\" -D BNAME=\"$(NAME)\" -c $< -o $@ $(OBJOPT)

%.o: %.cpp
	$(verbose)echo "  GEN [$@]";\
	$(CC) -D VDATE=\"$(STAMP)\" -D BNAME=\"$(NAME)\" -c $< -o $@ $(OBJOPT)

all: $(OBJs)
	$(verbose)echo "  LNK [$(NAME)]";\
	$(CC) $(OBJs) -o $(NAME) $(LNKOPT)

clean: 
	$(verbose)for i in $(OBJs);do echo "  DEL [$$i]";rm -f $$i;done; \
	echo "  DEL [$(NAME)]";\
	rm -f $(NAME)

install:
	echo "Nothing to do. Just copy '$(NAME)' where you need.";

echo:
	$(verbose)echo "src: $(SRC_LIST)";\
	echo "objs: $(OBJs)";
