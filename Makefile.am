DISTCHECK_CONFIGURE_FLAGS = --disable-icon-mapping

SUBDIRS = $(SVGSRCDIR) \
	gnome-seafoam \
	gnome-sakura \
	gnome-stardust \
	gnome-steel

ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

theme_in_files = index.theme.in
theme_DATA = $(theme_in_files:.theme.in=.theme)

THEME_DIRS=$(shell SIZES="$(render_sizes)"; for size in $$SIZES; do for dir in `find $(srcdir)/$(SVGOUTDIR)/$$size/* -type d`; do printf "$$dir,"; done; done; echo "scalable/actions,scalable/apps,scalable/devices,scalable/emblems,scalable/mimetypes,scalable/places,scalable/status,scalable/categories")

%.theme: %.theme.in $(SVGOUTDIR) Makefile
	dirs="`echo $(THEME_DIRS) | sed -e 's#$(srcdir)/gnome-slate/##g'`"; \
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
		else \
			echo "Type=Fixed" >> $@; \
		fi; \
		echo "" >> $@; \
	done

install-data-local:
	if [ -h $(DESTDIR)$(themedir) ]; then \
		rm -f $(DESTDIR)$(themedir); \
	fi
	if [ -d $(DESTDIR)$(themedir) ]; then \
		touch $(DESTDIR)$(themedir); \
	fi

install-exec-hook:
	(cd $(DESTDIR)$(themedir)/16x16/apps; ln -sf ../emblems/emblem-default.png \
		preferences-desktop-default-applications.png)
	(cd $(DESTDIR)$(themedir)/22x22/apps; ln -sf ../emblems/emblem-default.png \
		preferences-desktop-default-applications.png)
	(cd $(DESTDIR)$(themedir)/24x24/apps; ln -sf ../emblems/emblem-default.png \
		preferences-desktop-default-applications.png)
	(cd $(DESTDIR)$(themedir)/32x32/apps; ln -sf ../emblems/emblem-default.png \
		preferences-desktop-default-applications.png)
	(cd $(DESTDIR)$(themedir)/48x48/apps; ln -sf ../emblems/emblem-default.png \
		preferences-desktop-default-applications.png)
	(cd $(DESTDIR)$(themedir)/16x16/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)
	(cd $(DESTDIR)$(themedir)/22x22/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)
	(cd $(DESTDIR)$(themedir)/24x24/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)
	(cd $(DESTDIR)$(themedir)/32x32/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)
	(cd $(DESTDIR)$(themedir)/48x48/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)
	(cd $(DESTDIR)$(themedir)/256x256/actions; ln -sf ../devices/media-floppy.png \
		document-save.png)

install-data-hook:
	if test -z "$(DESTDIR)" && test -n "$(GTK_UPDATE_ICON_CACHE)" ; then \
		$(GTK_UPDATE_ICON_CACHE) -q $(DESTDIR)$(themedir); \
	fi

uninstall-hook:
	@rm -f  $(DESTDIR)$(themedir)/icon-theme.cache

EXTRA_DIST = \
	gnome-sakura \
	gnome-slate \
	gnome-stardust \
	gnome-seafoam \
	gnome-steel \
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
