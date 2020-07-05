ithemedir = $(DESTDIR)$(themedir)
ithemedirsaku = $(DESTDIR)$(themedirsaku)
ithemedirseaf = $(DESTDIR)$(themedirseaf)
ithemedirslat = $(DESTDIR)$(themedirslat)
ithemedirstar = $(DESTDIR)$(themedirstar)
ithemedirstee = $(DESTDIR)$(themedirstee)

ithemedirs = $(ithemedir) $(ithemedirsaku) $(ithemedirseaf) $(ithemedirslat) $(ithemedirstar) $(ithemedirstee)

DISTCHECK_CONFIGURE_FLAGS = --disable-icon-mapping

SUBDIRS = $(subdirs)

ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

theme_in_files = gnome-legacy/index.theme.in
theme_DATA = $(theme_in_files:.theme.in=.theme)

THEME_DIRS=$(shell SIZES="$(render_sizes)"; for size in $$SIZES; do for dir in `find $(srcdir)/gnome-legacy/$$size/* -type d`; do printf "$$dir,"; done; done; echo "scalable/actions,scalable/apps,scalable/devices,scalable/emblems,scalable/mimetypes,scalable/places,scalable/status,scalable/categories")

%.theme: %.theme.in gnome-legacy Makefile
	dirs="`echo $(THEME_DIRS) | sed -e 's#$(srcdir)/gnome-legacy/##g'`"; \
	sed -e "s|\@THEME_DIRS\@|$$dirs|g" < $< > $@; \
	for dir in `echo $$dirs | sed -e "s/,/ /g"`; do \
		sizefull="`dirname $$dir`"; \
		if test "$$sizefull" = "scalable"; then \
			size="16"; \
		else \
			size="`echo $$sizefull | sed -e 's/x.*$$//g'`"; \
		fi; \
		context="`basename $$dir`"; \
		echo "[$$dir]" >> $@; \
		if test "$$context" = "actions"; then \
			echo "Context=Actions" >> $@; \
		fi; \
		if test "$$context" = "animations"; then \
			echo "Context=Animations" >> $@; \
		fi; \
		if test "$$context" = "apps"; then \
			echo "Context=Applications" >> $@; \
		fi; \
		if test "$$context" = "categories"; then \
			echo "Context=Categories" >> $@; \
		fi; \
		if test "$$context" = "devices"; then \
			echo "Context=Devices" >> $@; \
		fi; \
		if test "$$context" = "emblems"; then \
			echo "Context=Emblems" >> $@; \
		fi; \
		if test "$$context" = "emotes"; then \
			echo "Context=Emotes" >> $@; \
		fi; \
		if test "$$context" = "intl"; then \
			echo "Context=International" >> $@; \
		fi; \
		if test "$$context" = "mimetypes"; then \
			echo "Context=MimeTypes" >> $@; \
		fi; \
		if test "$$context" = "places"; then \
			echo "Context=Places" >> $@; \
		fi; \
		if test "$$context" = "status"; then \
			echo "Context=Status" >> $@; \
		fi; \
		echo "Size=$$size" >> $@; \
		if test "$$sizefull" = "scalable"; then \
			echo "MinSize=8" >> $@; \
			echo "MaxSize=512" >> $@; \
			echo "Type=Scalable" >> $@; \
		elif test "$$size" = "256"; then \
			echo "MinSize=56" >> $@; \
			echo "MaxSize=512" >> $@; \
			echo "Type=Scalable" >> $@; \
		elif test "$$size" = "512"; then \
			echo "MinSize=56" >> $@; \
			echo "MaxSize=512" >> $@; \
			echo "Type=Scalable" >> $@; \
		else \
			echo "Type=Fixed" >> $@; \
		fi; \
		echo "" >> $@; \
	done

install-data-local:
	if [ -h $(ithemedir) ]; then \
		rm -f $(ithemedir); \
	fi
	if [ -d $(ithemedir) ]; then \
		touch $(ithemedir); \
	fi

install-exec-hook:
	for size in $(render_sizes); do \
		if [ -d $(ithemedir)/$$size/apps -a -f $(ithemedir)/$$size/emblems/emblem-default.png ]; then \
			(cd $(ithemedir)/$$size/apps; ln -vsf ../emblems/emblem-default.png \
				preferences-desktop-default-applications.png); \
		fi; \
			if [ -d $(ithemedir)/$$size/actions -a -f $(ithemedir)/$$size/devices/media-floppy.png ]; then \
			(cd $(ithemedir)/$$size/actions; ln -vsf ../devices/media-floppy.png \
				document-save.png); \
		fi; \
		if [ -f $(ithemedir)/$$size/apps/preferences-desktop-display.png ]; then \
			(cd $(ithemedir)/$$size/apps; ln -vsf preferences-desktop-display.png \
				mate-preferences-desktop-display.png); \
		fi; \
		if [ -f $(ithemedir)/$$size/mimetypes/text-x-preview.png ]; then \
			(cd $(ithemedir)/$$size/mimetypes; ln -vsf text-x-preview.png \
				application-x-generic.png); \
		fi; \
		if [ -d $(ithemedir)/$$size/mimetypes -a -f $(ithemedir)/$$size/places/folder.png ]; then \
			for dir in $(ithemedirs); do \
				if [ ! -d $$dir/$$size/mimetypes ]; then \
					mkdir -v $$dir/$$size/mimetypes; \
				fi; \
				(cd $$dir/$$size/mimetypes; ln -vsf ../places/folder.png \
					inode-directory.png); \
			done; \
		fi; \
	done

install-data-hook:
	for dir in $(ithemedirs); do \
		if test -z "$(DESTDIR)" && test -n "$(GTK_UPDATE_ICON_CACHE)" ; then \
			$(GTK_UPDATE_ICON_CACHE) -q $$dir; \
		fi; \
	done

uninstall-hook:
	for dir in $(ithemedirs); do \
		rm -f  $$dir/icon-theme.cache; \
	done

EXTRA_DIST = \
	$(subdirs) \
	COPYING_CCBYSA3 \
	COPYING_LGPL \
	$(theme_in_files)

CLEANFILES = \
	$(theme_DATA)

MAINTAINERCLEANFILES = \
	Makefile.in \
	aclocal.m4 \
	config.guess \
	config.h.in \
	config.sub \
	configure \
	depcomp \
	install-sh \
	intltool-*.in \
	libtool \
	ltmain.sh \
	missing \
	mkinstalldirs
