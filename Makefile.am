
ACLOCAL_AMFLAGS = -I m4

AUTOMAKE_OPTIONS = foreign subdir-objects

if MINGW32
  W32_CPPFLAGS = -DWIN32_LEAN_AND_MEAN
  W32_LIBS = -lshlwapi
endif

if USE_LIBOUT123
  OUT123_SOURCES = \
src/audio/out123/audiodrv.cpp \
src/audio/out123/audiodrv.h
endif

if USE_ICONV
  ICONV_SOURCES = \
src/codepages.h
endif

AM_CPPFLAGS = \
-I $(top_builddir)/src \
-I $(top_srcdir)/src \
-DPKGDATADIR="\"$(pkgdatadir)/\"" \
$(SIDPLAYFP_CFLAGS) \
$(USBSID_CFLAGS) \
$(STILVIEW_CFLAGS) \
$(ALSA_CFLAGS) \
$(PULSE_CFLAGS) \
$(LIBUSB_CFLAGS) \
$(OUT123_CFLAGS) \
${W32_CPPFLAGS} \
@debug_flags@


bin_PROGRAMS = \
src/sidplayfp \
src/stilview

#=========================================================
# sidplayfp

src_sidplayfp_SOURCES = \
src/IniConfig.cpp \
src/IniConfig.h \
src/args.cpp \
src/dataParser.h \
src/keyboard.cpp \
src/keyboard.h \
src/main.cpp \
src/menu.cpp \
src/mixer.cpp \
src/mixer.h \
src/player.cpp \
src/player.h \
src/setting.h \
src/sidcxx11.h \
src/siddefines.h \
src/sidlib_features.h \
src/utils.cpp \
src/utils.h \
src/codeConvert.cpp \
src/codeConvert.h \
$(ICONV_SOURCES) \
src/audio/AudioBase.h \
src/audio/AudioConfig.h \
src/audio/AudioDrv.cpp \
src/audio/AudioDrv.h \
src/audio/IAudio.h \
src/audio/alsa/audiodrv.cpp \
src/audio/alsa/audiodrv.h \
src/audio/au/auFile.cpp \
src/audio/au/auFile.h \
src/audio/directx/audiodrv.cpp \
src/audio/directx/audiodrv.h \
src/audio/mmsystem/audiodrv.cpp \
src/audio/mmsystem/audiodrv.h \
src/audio/null/null.cpp \
src/audio/null/null.h \
src/audio/oss/audiodrv.cpp \
src/audio/oss/audiodrv.h \
$(OUT123_SOURCES) \
src/audio/pulse/audiodrv.cpp \
src/audio/pulse/audiodrv.h \
src/audio/wav/WavFile.cpp \
src/audio/wav/WavFile.h \
src/ini/iniHandler.h \
src/ini/iniHandler.cpp \
src/ini/sidfstream.h \
src/ini/types.h

src_sidplayfp_LDADD = \
$(LIBICONV) \
$(AUDIO_LDFLAGS) \
$(USBSID_LDFLAGS) \
$(SIDPLAYFP_LIBS) \
$(BUILDERS_LDFLAGS) \
$(ALSA_LIBS) \
$(PULSE_LIBS) \
$(LIBUSB_LIBS) \
$(OUT123_LIBS) \
$(W32_LIBS)

#=========================================================
# stilview

src_stilview_SOURCES = \
src/codeConvert.cpp \
src/codeConvert.h \
$(ICONV_SOURCES) \
src/stilview.cpp

src_stilview_LDADD = \
$(LIBICONV) \
$(STILVIEW_LIBS)

#=========================================================
# docs

EXTRA_DIST =  \
doc/en/sidplayfp.pod \
doc/en/sidplayfp.ini.pod \
doc/en/stilview.pod

dist_man_MANS = \
doc/en/sidplayfp.1 \
doc/en/sidplayfp.ini.5 \
doc/en/stilview.1

DISTCLEANFILES = $(dist_man_MANS)

.pod.1:
	@mkdir -p $(@D)
	pod2man -c "User Programs" -s 1 $< > $@

.pod.5:
	@mkdir -p $(@D)
	pod2man -c "File formats" -s 5 $< > $@
