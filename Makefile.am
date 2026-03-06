# Ensure the compiler looks in the sibling libbeato folders for headers
AM_CPPFLAGS = -I$(top_srcdir)/../libbeato

# Ensure the GCC 15 compatibility flags from configure.ac are used
AM_CFLAGS = $(CFLAGS) $(MACHTYPE_WARN) \
						-std=gnu17 \
						-Wno-error=incompatible-pointer-types \
						-Wno-error=implicit-function-declaration \
						-Wno-error=int-conversion \
						-Wno-unused-variable \
						-include zlib.h \
						-include math.h

bin_PROGRAMS = bwtool
bwtool_SOURCES = \
	aggregate.c \
	bwtool.c \
	bwtool_shared.c \
	chromgraph.c \
	distrib.c \
	extract.c \
	fill.c \
	find.c \
	lift.c \
	matrix.c \
	paste.c \
	rand.c \
	remove.c \
	roll.c \
	sax.c \
	shift.c \
	split.c \
	summarize.c \
	window.c

bwtool_LDADD = $(LIBS)

SUBDIRS = tests
