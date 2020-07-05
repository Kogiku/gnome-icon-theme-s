ithemedir = $(DESTDIR)$(themedir)

icon_in_files = $(shell SRCDIR="$(srcdir)"; for i in `find $$SRCDIR -name "*.svg"`; do printf "$$i "; done)

$(render_sizes): Makefile

install-data-local:
	for size in $(render_sizes); do \
		echo "Going to copy files for $$size"; \
		for file in `cd $(top_srcdir)/gnome-legacy/$$size && find . -name "*.png"`; do \
			context="`dirname $$file`"; \
			$(mkdir_p) $(ithemedir)/$$size/$$context; \
			$(install_sh_DATA) $(top_srcdir)/gnome-legacy/$$size/$$file $(ithemedir)/$$size/$$file; \
		done; \
	done; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedir); \
		for size in $(render_sizes); do \
			cd $$size || continue; \
			echo "Going to set up icon mapping for $$size"; \
			for dir in `find . -type d`; do \
				context="`echo $$dir | cut -c 3-`"; \
				if [ $$context ]; then \
					$(ICONMAP) -c $$context; \
				fi; \
			done; \
			cd ..; \
		done; \
	fi

uninstall-local:
	rm -rf $(ithemedir)

EXTRA_DIST =			\
	$(icon_in_files)


MAINTAINERCLEANFILES =		\
	Makefile.in		\
	$(icon_cache)
