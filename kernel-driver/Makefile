# -----------------------------------------------------------------------------
# Copyright (c) 2011 Ozmo Inc
# Released under the GNU General Public License Version 2 (GPLv2).
# -----------------------------------------------------------------------------

# fallback to the current kernel source
KSRC ?= /lib/modules/$(shell uname -r)/build

KMOD_SRC ?= $(CURDIR)

KMOD_OPTIONS = CONFIG_USB_WPAN_HCD=m

# Don't build any of the other drivers
#KMOD_OPTIONS +=
#EXTRA_CFLAGS +=

CFLAGS_oztrace.o = -I$(src)

all:
	$(MAKE) -C $(KSRC) M=$(KMOD_SRC) $(KMOD_OPTIONS) $(MAKECMDGOALS) EXTRA_CFLAGS="$(EXTRA_CFLAGS)"

.PHONY: all clean load unload reload test

clean:
	$(MAKE) -C $(KSRC) M=$(KMOD_SRC) clean $(KMOD_OPTIONS)

load:
	insmod $(KMOD_SRC)/ozwpan.ko

unload:
	rmmod ozwpan

reload: unload load

test: all reload

obj-$(CONFIG_USB_WPAN_HCD) += ozwpan.o
#ozwpan-y := \
        ozmain.o \
        ozpd.o \
        ozusbsvc.o \
        ozusbsvc1.o \
        ozhcd.o \
        ozeltbuf.o \
        ozproto.o \
        ozcdev.o \
        ozurbparanoia.o \
        oztrace.o
ozwpan-y += ozmain.o
ozwpan-y += ozpd.o
ozwpan-y += ozusbsvc.o
ozwpan-y += ozusbsvc1.o
ozwpan-y += ozhcd.o
ozwpan-y += ozeltbuf.o
ozwpan-y += ozproto.o
ozwpan-y += ozcdev.o
ozwpan-y += ozkobject.o
ozwpan-y += ozurbparanoia.o
ozwpan-y += oztrace.o

