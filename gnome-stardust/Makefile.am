# from https://github.com/mate-desktop/mate-icon-theme/blob/master/menta/Makefile.am

ithemedirstar = $(DESTDIR)$(themedirstar)

install-data-local:
	$(mkdir_p) $(ithemedirstar); \
	for dir in `cd $(top_srcdir)/gnome-stardust && find . -type d | sed s/.//`; do \
		$(mkdir_p) $(ithemedirstar)$$dir; \
	done; \
	for file in `cd $(top_srcdir)/gnome-stardust && find . -name "*.png" | sed s@./@/@`; do \
		$(install_sh_DATA) $(top_srcdir)/gnome-stardust/$$file $(ithemedirstar)/$$file; \
	done; \
	$(install_sh_DATA) $(top_srcdir)/gnome-stardust/index.theme $(ithemedirstar)/index.theme; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedirstar); \
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
	if [ -d "$(ithemedirstar)" ]; then \
		cd $(ithemedirstar); \
		for file in `find . -name *.png | sed s@./@/@`; do \
			rm -f $(ithemedirstar)$$file; \
		done; \
		rm -f $(ithemedirstar)/index.theme; \
	fi

MAINTAINERCLEANFILES = \
	Makefile.in \
	Makefile
