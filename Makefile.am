AUTOMAKE_OPTIONS = foreign

bin_SCRIPTS = src/update-ukefi src/ukefi-configure-boot
CLEANFILES = $(bin_SCRIPTS)

etcdir = $(sysconfdir)/ukefi
etc_DATA = data/directory

# The distribution is responsible for populating /etc/cmdline with the current
# kernel command-line paramters.

do_subst = $(SED) -e 's,[@]datadir[@],$(datadir),g' \
               -e 's,[@]sysconfdir[@],$(sysconfdir),g'

src/%: src/%.in
	$(do_subst) < $< > $@
	chmod +x $@

install-exec-hook:
	mkdir -p $(sysconfdir)/initramfs/post-update.d
	$(LN_S) $(bindir)/update-ukefi $(sysconfdir)/initramfs/post-update.d/90-update-ukefi
