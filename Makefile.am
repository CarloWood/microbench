AM_CPPFLAGS = -iquote $(top_builddir) -iquote $(top_srcdir)

noinst_LTLIBRARIES = libmicrobench.la

SOURCES = \
	microbench.h \
	systemtime.h \
	systemtime.cpp

libmicrobench_la_SOURCES = ${SOURCES}
libmicrobench_la_CXXFLAGS = -std=c++11

# --------------- Maintainer's Section

if MAINTAINER_MODE
distclean-local:
	-rm -f *.s *.ii

clean-local:
endif

MAINTAINERCLEANFILES = $(srcdir)/Makefile.in
