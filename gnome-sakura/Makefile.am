# from https://github.com/mate-desktop/mate-icon-theme/blob/master/menta/Makefile.am

ithemedirsaku = $(DESTDIR)$(themedirsaku)

install-data-local:
	$(mkdir_p) $(ithemedirsaku); \
	for dir in `cd $(top_srcdir)/gnome-sakura && find . -type d | sed s/.//`; do \
		$(mkdir_p) $(ithemedirsaku)$$dir; \
	done; \
	for file in `cd $(top_srcdir)/gnome-sakura && find . -name "*.png" | sed s@./@/@`; do \
		$(install_sh_DATA) $(top_srcdir)/gnome-sakura/$$file $(ithemedirsaku)/$$file; \
	done; \
	$(install_sh_DATA) $(top_srcdir)/gnome-sakura/index.theme $(ithemedirsaku)/index.theme; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedirsaku); \
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
	if [ -d "$(ithemedirsaku)" ]; then \
		cd $(ithemedirsaku); \
		for file in `find . -name *.png | sed s@./@/@`; do \
			rm -f $(ithemedirsaku)$$file; \
		done; \
		rm -f $(ithemedirsaku)/index.theme; \
	fi

MAINTAINERCLEANFILES = \
	Makefile.in \
	Makefile
