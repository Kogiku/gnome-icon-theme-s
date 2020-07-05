# from https://github.com/mate-desktop/mate-icon-theme/blob/master/menta/Makefile.am

ithemedirstee = $(DESTDIR)$(themedirstee)

install-data-local:
	$(mkdir_p) $(ithemedirstee); \
	for dir in `cd $(top_srcdir)/gnome-steel && find . -type d | sed s/.//`; do \
		$(mkdir_p) $(ithemedirstee)$$dir; \
	done; \
	for file in `cd $(top_srcdir)/gnome-steel && find . -name "*.png" | sed s@./@/@`; do \
		$(install_sh_DATA) $(top_srcdir)/gnome-steel/$$file $(ithemedirstee)/$$file; \
	done; \
	$(install_sh_DATA) $(top_srcdir)/gnome-steel/index.theme $(ithemedirstee)/index.theme; \
	if [ $(ICONMAP) != "false" ]; then \
		cd $(ithemedirstee); \
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
	if [ -d "$(ithemedirstee)" ]; then \
		cd $(ithemedirstee); \
		for file in `find . -name *.png | sed s@./@/@`; do \
			rm -f $(ithemedirstee)$$file; \
		done; \
		rm -f $(ithemedirstee)/index.theme; \
	fi

MAINTAINERCLEANFILES = \
	Makefile.in \
	Makefile
