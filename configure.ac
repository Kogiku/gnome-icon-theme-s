dnl Process this file with autoconf to produce a configure script.
AC_PREREQ(2.53)

AC_INIT([gnome-icon-theme-s], [3.12.0.8],
        [https://github.com/Kogiku/gnome-icon-theme-s/issues])
AC_CONFIG_SRCDIR([gnome-legacy/index.theme.in])

AM_INIT_AUTOMAKE([1.9 dist-xz no-dist-gzip tar-ustar foreign])

PKG_PROG_PKG_CONFIG([0.19])

AC_SUBST([subdirs], ["gnome-legacy gnome-sakura gnome-seafoam gnome-slate gnome-stardust gnome-steel"])

# Workaround to make aclocal get the right flags
AC_SUBST(ACLOCAL_AMFLAGS, "\${ACLOCAL_FLAGS}")

# Define the toplevel paths here
AC_SUBST(themedir, "\${datadir}/icons/gnome-legacy")
AC_SUBST(themedirsaku, "\${datadir}/icons/gnome-sakura")
AC_SUBST(themedirseaf, "\${datadir}/icons/gnome-seafoam")
AC_SUBST(themedirslat, "\${datadir}/icons/gnome-slate")
AC_SUBST(themedirstar, "\${datadir}/icons/gnome-stardust")
AC_SUBST(themedirstee, "\${datadir}/icons/gnome-steel")

# Icon sizes we want to install
AC_SUBST([render_sizes], ["8x8 16x16 22x22 24x24 32x32 48x48 256x256 512x512"])

# Allow icon mapping to be disabled
AC_ARG_ENABLE([icon-mapping],
   AC_HELP_STRING([--enable-icon-mapping],
                  [Enable compatibility symlinks [default=auto]]),
                  [enable_mapping=$enableval],
                  [enable_mapping=yes])

ICONMAP="true"
if test "x$enable_mapping" != "xno"; then
   UTILS_REQUIRED=0.8.7

   AC_MSG_CHECKING([icon-naming-utils >= $UTILS_REQUIRED])
   PKG_CHECK_EXISTS(icon-naming-utils >= $UTILS_REQUIRED,
                    have_utils=yes, have_utils=no)
   if test "x$have_utils" = "xyes"; then
      UTILS_PATH="`$PKG_CONFIG --variable=program_path icon-naming-utils`"
      ICONMAP="$UTILS_PATH/icon-name-mapping"
      AC_MSG_RESULT([yes])
   else
      AC_MSG_RESULT([no])
      AC_MSG_ERROR([icon-naming-utils >= $UTILS_REQUIRED is required to build
                    and install gnome-icon-theme-s])
   fi
else
   ICONMAP="false"
fi

AC_SUBST(ICONMAP)

AC_PATH_PROG(GTK_UPDATE_ICON_CACHE, gtk-update-icon-cache)

AC_CONFIG_FILES([
Makefile
gnome-legacy/Makefile
gnome-sakura/Makefile
gnome-seafoam/Makefile
gnome-slate/Makefile
gnome-stardust/Makefile
gnome-steel/Makefile
])

AC_OUTPUT
