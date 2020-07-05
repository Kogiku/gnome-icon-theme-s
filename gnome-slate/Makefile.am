# from https://github.com/mate-desktop/mate-icon-theme/blob/master/menta/Makefile.am

ithemedirslat = $(DESTDIR)$(themedirslat)

install-data-local:
	$(mkdir_p) $(ithemedirslat); \
	for dir in `cd $(top_srcdir)/gnome-slate && find . -type d | sed s/.//`; do \
		$(mkdir_p) $(ithemedirslat)$$dir; \
	done; \
	for file in `cd $(top_srcdir)/gnome-slate && find . -name "*.png" | sed s@./@/@`; do \
		$(install_sh_DATA) $(top_srcdir)/gnome-slate/$$file $(ithemedirslat)/$$file; \
	done; \
	$(install_sh_DATA) $(top_srcdir)/gnome-slate/index.theme $(ithemedirslat)/index.theme; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedirslat); \
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
	rm -rf $(ithemedirslat)

MAINTAINERCLEANFILES = \
	Makefile.in \
	Makefile
