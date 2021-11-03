AUTOMAKE_OPTIONS = foreign

bin_SCRIPTS = src/update-ukefi
CLEANFILES = $(bin_SCRIPTS)

etcdir = $(sysconfdir)/ukefi
etc_DATA = data/directory data/pkcs11-pin data/pkcs11-serial

# The distribution is responsible for populating /etc/cmdline with the current
# kernel command-line paramters, and /etc/certificate.pem and /etc/key.pem with
# a generated keypair.

do_subst = $(SED) -e 's,[@]datadir[@],$(datadir),g' \
               -e 's,[@]sysconfdir[@],$(sysconfdir),g'

src/update-ukefi: src/update-ukefi.in
	$(do_subst) < src/update-ukefi.in > src/update-ukefi
	chmod +x src/update-ukefi

install-exec-hook:
	mkdir -p $(sysconfdir)/initramfs/post-update.d
	$(LN_S) $(bindir)/update-ukefi $(sysconfdir)/initramfs/post-update.d/90-update-ukefi
