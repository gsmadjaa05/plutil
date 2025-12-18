AC_PREREQ([2.69])
AC_INIT([plutil], [0.1.0], [https://github.com/screenplaydev/plutil/issues])
AC_CONFIG_SRCDIR([Libraries/plist/Tools/plutil.cpp])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIRS([m4])

AM_INIT_AUTOMAKE([foreign subdir-objects silent-rules])
AM_SILENT_RULES([yes])

AC_PROG_CC
AC_PROG_CXX
AC_PROG_INSTALL
LT_INIT
PKG_PROG_PKG_CONFIG

AC_LANG([C++])

# Figure out the host platform.
case "$host_os" in
  mingw* | msys*)
    is_mingw=yes
    AC_DEFINE([HAVE_MINGW], [1], [Define if building for MinGW/MSYS2])
    ;;
  *)
    is_mingw=no
    ;;
esac
AM_CONDITIONAL([WINDOWS_BUILD], [test "x$is_mingw" = "xyes"])

# Prefer the MSYS2 provided prefix when available to avoid writing to /usr/local.
if test "x$prefix" = "xNONE" && test "x$is_mingw" = "xyes"; then
  if test -n "$MINGW_PREFIX"; then
    prefix="$MINGW_PREFIX"
  else
    case "$MSYSTEM" in
      MINGW64) prefix=/mingw64 ;;
      MINGW32) prefix=/mingw32 ;;
    esac
  fi
fi

AC_MSG_NOTICE([install prefix: $prefix])

# Compiler defaults.
if test "x$is_mingw" = "xyes"; then
  PLATFORM_CPPFLAGS="-D__USE_MINGW_ANSI_STDIO=1"
else
  PLATFORM_CPPFLAGS=
fi
AC_SUBST([PLATFORM_CPPFLAGS])

# Threads.
AC_CHECK_LIB([pthread], [pthread_create],
  [PTHREAD_LIBS="-lpthread"],
  [PTHREAD_LIBS=""])
AC_SUBST([PTHREAD_LIBS])

# Optional linenoise (not used on Windows).
AC_ARG_ENABLE([linenoise],
  AS_HELP_STRING([--disable-linenoise], [Skip building bundled linenoise]),
  [], [enable_linenoise=yes])

LINENOISE_SOURCE="$srcdir/ThirdParty/linenoise/linenoise.c"
if test "x$enable_linenoise" = "xyes" \
   && test -f "$LINENOISE_SOURCE" \
   && test "x$is_mingw" != "xyes"; then
  LINENOISE_ENABLED=yes
else
  LINENOISE_ENABLED=no
fi
AM_CONDITIONAL([HAVE_LINENOISE], [test "x$LINENOISE_ENABLED" = "xyes"])

# libxml2 is required on non-Windows builds.
if test "x$is_mingw" = "xyes"; then
  LIBXML2_CFLAGS=
  LIBXML2_LIBS=
  PLIST_WINDOWS_LIBS="-lole32"
else
  PLIST_WINDOWS_LIBS=
  PKG_CHECK_MODULES([LIBXML2], [libxml-2.0 >= 2.7])
fi
AC_SUBST([LIBXML2_CFLAGS])
AC_SUBST([LIBXML2_LIBS])
AC_SUBST([PLIST_WINDOWS_LIBS])

# process library platform libs.
if test "x$is_mingw" = "xyes"; then
  PROCESS_WINDOWS_LIBS="-luserenv -lshell32 -ladvapi32"
else
  PROCESS_WINDOWS_LIBS=
fi
AC_SUBST([PROCESS_WINDOWS_LIBS])

AC_CONFIG_FILES([Makefile
                 Libraries/Makefile
                 Libraries/ext/Makefile
                 Libraries/libutil/Makefile
                 Libraries/process/Makefile
                 Libraries/plist/Makefile])

AC_OUTPUT

