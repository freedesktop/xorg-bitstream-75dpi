#  Copyright 2005 Red Hat, Inc.
#
#  Permission to use, copy, modify, distribute, and sell this software
#  and its documentation for any purpose is hereby granted without
#  fee, provided that the above copyright notice appear in all copies
#  and that both that copyright notice and this permission notice
#  appear in supporting documentation, and that the name of Red Hat
#  not be used in advertising or publicity pertaining to distribution
#  of the software without specific, written prior permission.  Red
#  Hat makes no representations about the suitability of this software
#  for any purpose.  It is provided "as is" without express or implied
#  warranty.
#
#  RED HAT DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE,
#  INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS, IN
#  NO EVENT SHALL RED HAT BE LIABLE FOR ANY SPECIAL, INDIRECT OR
#  CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS
#  OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
#  NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN
#  CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

FONT_DIR = 75dpi
FONT_FILES = \
	charB08 \
	charB10 \
	charB12 \
	charB14 \
	charB18 \
	charB24 \
	charBI08 \
	charBI10 \
	charBI12 \
	charBI14 \
	charBI18 \
	charBI24 \
	charI08 \
	charI10 \
	charI12 \
	charI14 \
	charI18 \
	charI24 \
	charR08 \
	charR10 \
	charR12 \
	charR14 \
	charR18 \
	charR24 \
	tech14 \
	techB14 \
	term14 \
	termB14

BDF_FILES = $(FONT_FILES:%=%.bdf)
PCF_FILES = $(FONT_FILES:%=%.pcf.gz)

SUFFIXES = .bdf .pcf.gz

.bdf.pcf.gz:
	@rm -f $@
	$(BDFTOPCF) -t $^ | gzip > $@

fontdir = $(libdir)/X11/fonts/$(FONT_DIR)
font_DATA = $(PCF_FILES)
CLEANFILES = $(font_DATA)

EXTRA_DIST = $(BDF_FILES) autogen.sh

install-data-hook:
	@rm -f $(DESTDIR)$(fontdir)/fonts.scale
	$(MKFONTSCALE) $(DESTDIR)$(fontdir)
	@rm -f $(DESTDIR)$(fontdir)/font.dir
	$(MKFONTDIR) $(DESTDIR)$(fontdir)

distuninstallcheck:
	@: