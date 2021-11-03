AUTOMAKE_OPTIONS = foreign

bin_SCRIPTS = src/update-ukefi src/ukefi-configure-boot
CLEANFILES = $(bin_SCRIPTS)

# The distribution is responsible for populating /etc/ukefi/cmdline with the
# current kernel command-line paramters and /etc/ukefi/directory with a
# distribution-specific directory name.

do_subst = $(SED) -e 's,[@]datadir[@],$(datadir),g' \
               -e 's,[@]sysconfdir[@],$(sysconfdir),g'

src/%: src/%.in
	$(do_subst) < $< > $@
	chmod +x $@

install-exec-hook:
	mkdir -p $(sysconfdir)/initramfs/post-update.d
	$(LN_S) $(bindir)/update-ukefi $(sysconfdir)/initramfs/post-update.d/90-update-ukefi
