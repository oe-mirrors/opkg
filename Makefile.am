ACLOCAL_AMFLAGS = -I m4

SUBDIRS = libopkg src utils man

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = libopkg.pc

interceptdir = $(datadir)/opkg/intercept
intercept_DATA = intercept/ldconfig intercept/depmod intercept/update-modules

install-data-hook:
	chmod +x $(DESTDIR)$(datadir)/opkg/intercept/*

EXTRA_DIST = \
	$(intercept_DATA) \
	docs/ \
	scripts/ \
	tests/ \
	README.md \
	CHANGELOG*

run-tests:
	$(MAKE) -C tests DATADIR=@datadir@ SYSCONFDIR=@sysconfdir@ VARDIR=@localstatedir@

check: run-tests

install-ptest:
	cp -r $(srcdir)/tests $(DESTDIR)
	cp Makefile $(DESTDIR)
	sed -e 's/^Makefile/_Makefile/' < Makefile > $(DESTDIR)/Makefile
