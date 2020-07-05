# from https://github.com/mate-desktop/mate-icon-theme/blob/master/menta/Makefile.am

ithemedirseaf = $(DESTDIR)$(themedirseaf)

install-data-local:
	$(mkdir_p) $(ithemedirseaf); \
	for dir in `cd $(top_srcdir)/gnome-seafoam && find . -type d | sed s/.//`; do \
		$(mkdir_p) $(ithemedirseaf)$$dir; \
	done; \
	for file in `cd $(top_srcdir)/gnome-seafoam && find . -name "*.png" | sed s@./@/@`; do \
		$(install_sh_DATA) $(top_srcdir)/gnome-seafoam/$$file $(ithemedirseaf)/$$file; \
	done; \
	$(install_sh_DATA) $(top_srcdir)/gnome-seafoam/index.theme $(ithemedirseaf)/index.theme; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedirseaf); \
		for size in `find . -mindepth 1 -maxdepth 1 -type d | sed s@./@@`; do \
			cd $$size || continue ; \
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
	rm -rf $(ithemedirseaf)

MAINTAINERCLEANFILES = \
	Makefile.in \
	Makefile
