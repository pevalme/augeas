SUBDIRS = gnulib/lib src
if ENABLE_GNULIB_TESTS
SUBDIRS += gnulib/tests
endif
SUBDIRS += tests man doc examples

ACLOCAL_AMFLAGS = -I gnulib/m4

lensdir=$(datadir)/augeas/lenses/dist
lenstestdir=$(datadir)/augeas/lenses/dist/tests

dist_lens_DATA=$(wildcard lenses/*.aug)
dist_lenstest_DATA=$(wildcard lenses/tests/*.aug)

EXTRA_DIST=augeas.spec build/ac-aux/move-if-change Makefile.am HACKING.md

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = augeas.pc

distclean-local:
	-find $(top_builddir)/build/* -maxdepth 0 -not -name ac-aux | xargs rm -rf

ChangeLog:
	if test -d $(top_srcdir)/.git; then                             \
	  $(top_srcdir)/build/ac-aux/gitlog-to-changelog > $@;             \
	fi

dist: ChangeLog

.PHONY: ChangeLog
