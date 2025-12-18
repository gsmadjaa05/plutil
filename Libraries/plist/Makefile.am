bin_PROGRAMS = plutil PlistBuddy
lib_LTLIBRARIES = libplist.la

if HAVE_LINENOISE
LINENOISE_SOURCE = ThirdParty/linenoise/linenoise.c
noinst_LTLIBRARIES = liblinenoise.la

liblinenoise_la_SOURCES = $(LINENOISE_SOURCE)
liblinenoise_la_CPPFLAGS = -I$(top_srcdir)/ThirdParty/linenoise
liblinenoise_la_LDFLAGS = -no-undefined

LINENOISE_LIBS = liblinenoise.la
LINENOISE_CPPFLAGS = -I$(top_srcdir)/ThirdParty/linenoise
else
LINENOISE_LIBS =
LINENOISE_CPPFLAGS =
endif

AM_CPPFLAGS = \
  $(PLATFORM_CPPFLAGS) \
  $(LIBXML2_CFLAGS) \
  $(LINENOISE_CPPFLAGS) \
  -I$(top_srcdir)/Libraries/ext/Headers \
  -I$(top_srcdir)/Libraries/libutil/Headers \
  -I$(top_srcdir)/Libraries/process/Headers \
  -I$(top_srcdir)/Libraries/plist/Headers \
  -I$(top_srcdir)/Libraries/plist/PrivateHeaders

libplist_la_SOURCES = \
  Sources/ObjectType.cpp \
  Sources/Array.cpp \
  Sources/Boolean.cpp \
  Sources/Data.cpp \
  Sources/Date.cpp \
  Sources/Dictionary.cpp \
  Sources/Integer.cpp \
  Sources/Null.cpp \
  Sources/Object.cpp \
  Sources/Real.cpp \
  Sources/String.cpp \
  Sources/UID.cpp \
  Sources/Base64.cpp \
  Sources/rfc4648.c \
  Sources/ISODate.cpp \
  Sources/UnixTime.cpp \
  Sources/Keys/Unpack.cpp \
  Sources/Format/Encoding.cpp \
  Sources/Format/unicode.c \
  Sources/Format/BaseXMLParser.cpp \
  Sources/Format/XMLParser.cpp \
  Sources/Format/XMLWriter.cpp \
  Sources/Format/XML.cpp \
  Sources/Format/SimpleXMLParser.cpp \
  Sources/Format/SimpleXML.cpp \
  Sources/Format/ABPContext.cpp \
  Sources/Format/ABPReader.cpp \
  Sources/Format/ABPWriter.cpp \
  Sources/Format/Binary.cpp \
  Sources/Format/ASCIIPListLexer.cpp \
  Sources/Format/ASCIIParser.cpp \
  Sources/Format/ASCIIWriter.cpp \
  Sources/Format/ASCII.cpp \
  Sources/Format/JSONParser.cpp \
  Sources/Format/JSONWriter.cpp \
  Sources/Format/JSON.cpp \
  Sources/Format/Any.cpp

libplist_la_LIBADD = \
  $(top_builddir)/Libraries/libutil/libutil.la \
  $(LIBXML2_LIBS) \
  $(PLIST_WINDOWS_LIBS)

libplist_la_LDFLAGS = -no-undefined -version-info 0:0:0

plutil_SOURCES = Tools/plutil.cpp
plutil_LDADD = \
  libplist.la \
  $(top_builddir)/Libraries/process/libprocess.la \
  $(top_builddir)/Libraries/libutil/libutil.la
plutil_CPPFLAGS = $(AM_CPPFLAGS)

PlistBuddy_SOURCES = Tools/PlistBuddy.cpp
PlistBuddy_LDADD = \
  libplist.la \
  $(top_builddir)/Libraries/libutil/libutil.la \
  $(LINENOISE_LIBS)
PlistBuddy_CPPFLAGS = $(AM_CPPFLAGS)

# Convenience: copy built executables to a top-level bin/ after build.
build_bindir = $(top_builddir)/bin

all-local: $(bin_PROGRAMS)
	$(MKDIR_P) $(build_bindir)
	$(INSTALL_PROGRAM) plutil$(EXEEXT) $(build_bindir)/plutil$(EXEEXT)
	$(INSTALL_PROGRAM) PlistBuddy$(EXEEXT) $(build_bindir)/PlistBuddy$(EXEEXT)

