CXX =		g++
CC =		$(CXX)
CXXFLAGS =      -g -O -s -frounding-math
CXXFLAGS +=     -Wextra -Wall -Werror -fPIC
CXXFLAGS +=	-Wno-unused-variable -Wno-unused-parameter
CXXFLAGS +=	-Wno-unused-function
ifeq ($(findstring g++,$(CXX)),g++)
    CXXFLAGS += -no-canonical-prefixes -Wno-builtin-macro-redefined \
                -D__DATE__="redacted" -D__TIMESTAMP__="redacted" \
                -D__TIME__="redacted" -U_FORTIFY_SOURCE \
                -D_FORTIFY_SOURCE=1 -fstack-protector
endif
CXXFLAGS +=     -std=c++11
CXXFLAGS +=	$(shell root-config --cflags)
LDFLAGS =	$(shell root-config --ldflags)
LDLIBS =	$(shell root-config --libs)

CXXFLAGS +=	-I$(BOOST_ROOT)/include

CXXFLAGS +=	-I../..

TARGET =	photon_ml

all:		$(TARGET)

clean:
		/usr/bin/rm -f *~ *.o $(TARGET) ml_out.py

%.cc:		../../special_function.h