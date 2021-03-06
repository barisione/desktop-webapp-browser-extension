AC_PREREQ([2.63])

AC_INIT([desktop-webapp-browser-extension],
        [0.3.0],
	[https://github.com/rodrmoya/desktop-webapp-browser-extension],
	[desktop-webapp-browser-extension],
	[https://github.com/rodrmoya/desktop-webapp-browser-extension])

AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE([1.11 foreign -Wno-portability no-define no-dist-gzip dist-xz tar-ustar])

AM_SILENT_RULES([yes])

AC_CONFIG_MACRO_DIR([m4])

AC_PROG_CC
AM_PROG_CC_C_O
AC_PROG_CC_C99

AC_PROG_MKDIR_P
AC_PROG_SED

AC_DISABLE_STATIC
LT_INIT

dnl ***************************************************************************
dnl Internationalization
dnl ***************************************************************************
IT_PROG_INTLTOOL([0.50.0])

GETTEXT_PACKAGE=desktop_webapp_browser_extension
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [GETTEXT package name])


PKG_CHECK_MODULES(DESKTOPWEBAPP_NPAPI_PLUGIN,
                  glib-2.0
                  gio-2.0
                  gdk-pixbuf-2.0
                  gtk+-3.0
                  )
GLIB_GSETTINGS


dnl ***************************************************************************
dnl Chromium extension
dnl ***************************************************************************

AC_ARG_ENABLE(chromium, 
	AS_HELP_STRING([--enable-chromium], 
		[Build Chromium extension. [default=yes]]),
		[enable_chromium=$enableval], [enable_chromium="yes"])
if test "x$enable_chromium" = "xyes"; then
    AC_DEFINE([WITH_CHROMIUM], 1, [Build Chromium extension.])
fi
AM_CONDITIONAL([WITH_CHROMIUM], [test "x$enable_chromium" = "xyes"])

AC_ARG_ENABLE(google-chrome,
       AS_HELP_STRING([--enable-google-chrome],
               [Build Google Chrome extension. [default=yes]]),
               [enable_google_chrome=$enableval], [enable_google_chrome="yes"])
if test "x$enable_google_chrome" = "xyes"; then
    AC_DEFINE([WITH_GOOGLE_CHROME], 1, [Build Google Chrome extension.])
fi
AM_CONDITIONAL([WITH_GOOGLE_CHROME], [test "x$enable_google_chrome" = "xyes"])

AC_CONFIG_FILES([
Makefile
chromium-extension/Makefile
npapi-plugin/Makefile
npapi-plugin/src/Makefile
po/Makefile.in
])
AC_OUTPUT

AC_MSG_NOTICE([

  desktop-webapp-browser-extension $VERSION
  -----------------------------------------

  Chromium extension      : ${enable_chromium}
  Google Chrome extension : ${enable_google_chrome}
])
