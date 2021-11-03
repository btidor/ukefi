AUTOMAKE_OPTIONS = foreign

bin_SCRIPTS = src/update-ukefi
CLEANFILES = $(bin_SCRIPTS)

etcdir = $(sysconfdir)/ukefi
etc_DATA = data/directory

do_subst = sed -e 's,[@]datadir[@],$(datadir),g' \
               -e 's,[@]sysconfdir[@],$(sysconfdir),g'

src/update-ukefi: src/update-ukefi.in
	$(do_subst) < src/update-ukefi.in > src/update-ukefi
	chmod +x src/update-ukefi
