lib_LTLIBRARIES = libprocess.la

libprocess_la_SOURCES = \
  Sources/Context.cpp \
  Sources/DefaultContext.cpp \
  Sources/MemoryContext.cpp \
  Sources/Launcher.cpp \
  Sources/DefaultLauncher.cpp \
  Sources/MemoryLauncher.cpp \
  Sources/User.cpp \
  Sources/DefaultUser.cpp \
  Sources/MemoryUser.cpp

libprocess_la_CPPFLAGS = \
  $(PLATFORM_CPPFLAGS) \
  -I$(top_srcdir)/Libraries/ext/Headers \
  -I$(top_srcdir)/Libraries/libutil/Headers \
  -I$(top_srcdir)/Libraries/process/Headers

libprocess_la_LIBADD = \
  $(top_builddir)/Libraries/ext/libext.la \
  $(top_builddir)/Libraries/libutil/libutil.la \
  $(PTHREAD_LIBS) \
  $(PROCESS_WINDOWS_LIBS)

libprocess_la_LDFLAGS = -no-undefined -version-info 0:0:0

