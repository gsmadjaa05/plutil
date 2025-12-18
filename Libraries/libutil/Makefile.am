lib_LTLIBRARIES = libutil.la

libutil_la_SOURCES = \
  Sources/FSUtil.cpp \
  Sources/Filesystem.cpp \
  Sources/DefaultFilesystem.cpp \
  Sources/MemoryFilesystem.cpp \
  Sources/Permissions.cpp \
  Sources/Absolute.cpp \
  Sources/Relative.cpp \
  Sources/Unix.cpp \
  Sources/Windows.cpp \
  Sources/Options.cpp \
  Sources/Escape.cpp \
  Sources/Wildcard.cpp \
  Sources/md5.c

libutil_la_CPPFLAGS = \
  $(PLATFORM_CPPFLAGS) \
  -I$(top_srcdir)/Libraries/ext/Headers \
  -I$(top_srcdir)/Libraries/libutil/Headers

libutil_la_LIBADD = \
  $(top_builddir)/Libraries/ext/libext.la

libutil_la_LDFLAGS = -no-undefined -version-info 0:0:0

