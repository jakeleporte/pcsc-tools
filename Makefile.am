PERL_BINS = ATR_analysis scriptor gscriptor
PERL_MANPAGES = ATR_analysis.1p scriptor.1p gscriptor.1p

bin_PROGRAMS = pcsc_scan
pcsc_scan_SOURCES = pcsc_scan.c pcsc_scan.1
pcsc_scan_CFLAGS = $(PCSC_CFLAGS)
pcsc_scan_LDADD = $(PCSC_LIBS)

bin_SCRIPTS = $(PERL_BINS)

pcsc_DATA = smartcard_list.txt
pcscdir = $(datarootdir)/pcsc

edit = sed \
	-e 's|@pcscdir[@]|$(pcscdir)|g'

ATR_analysis: ATR_analysis.in
	$(edit) $< > $@

ATR_analysis.1p: ATR_analysis.1p.in
	$(edit) $< > $@

# Clean up the macro-edited files
CLEANFILES = ATR_analysis ATR_analysis.1p

#  install the man pages
man_MANS = pcsc_scan.1 $(PERL_MANPAGES)

EXTRA_DIST = Changelog $(PERL_BINS) $(PERL_MANPAGES) $(pcsc_DATA) \
	LICENCE \
	gscriptor.desktop test.script

Changelog:
	git log --stat --decorate=short > $@
