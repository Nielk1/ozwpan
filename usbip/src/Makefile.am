AM_CPPFLAGS = -I$(top_srcdir)/libsrc -DUSBIDS_FILE='"@USBIDS_DIR@/usb.ids"'
AM_CFLAGS   = @EXTRA_CFLAGS@
LDADD       = $(top_builddir)/libsrc/libusbip.la

sbin_PROGRAMS := usbipd

usbipd_SOURCES := usbip_network.h usbipd.c usbip_network.c
