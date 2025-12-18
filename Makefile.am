SUBDIRS = Libraries

ACLOCAL_AMFLAGS = -I m4

EXTRA_DIST = README.md LICENSE ThirdParty

clean-local:
	-find . \( -name '*.o' -o -name '*.lo' -o -name '*.la' -o -name '*.lai' -o -name '.deps' -o -name '.libs' \) -exec rm -rf {} +
	-rm -rf bin

