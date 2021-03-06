#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").  
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
#ident	"@(#)Makefile	1.0	06/03/07	SMI"
#
# Copyright 2007 Sun Microsystems, Inc.  All rights reserved.
# Use is subject to license terms.
#

include $(SRC)/Makefile.master

DIR:sh = basename `pwd`

LOCALE:sh = cd ..;basename `pwd`

EN_CONV_TABLES = \
		BIG5-1.GLGR.txt \
		GB2312-0.GR.txt \
		GBK-0.GLGR.txt \
		HKSCS-1.GLGR.txt \
		ISO8859-10.GR.txt \
		ISO8859-15.GR.txt \
		ISO8859-2.GR.txt \
		ISO8859-3.GR.txt \
		ISO8859-4.GR.txt \
		ISO8859-5.GR.txt \
		ISO8859-6.GLGR.txt \
		ISO8859-7.GR.txt \
		ISO8859-8.GR.txt \
		ISO8859-9.GR.txt \
		JISX0201-0.GL.txt \
		JISX0201-0.GR.txt \
		JISX0208-0.GL.txt \
		JISX0208-0.GR.txt \
		JISX0212-0.GR.txt \
		JISX0213-1.GL.txt \
		JISX0213-1.GR.txt \
		JISX0213-2.GL.txt \
		JISX0213-2.GR.txt \
		KSC-JOHAP.GLGR.txt \
		SUN.UNICODE.INDIA-0.GLGR.txt \
		SUNUDCJA.GL.txt \
		TIS620.2533-0.GR.txt \
		UNICODE-FONTSPECIFIC.GLGR.txt

HI_CONV_TABLES = \
		U32_TO_CS_0 \
		U32_TO_CS_1 \
		U32_TO_CS_14 \
		U32_TO_CS_15 \
		U32_TO_CS_16 \
		U32_TO_CS_2

XUCTBLGEN = $(SRC)/src/cmd/xuctblgen/xuctblgen

FILES = $(EN_CONV_TABLES)

TARGETDIR = $(FILEROOT)/usr/openwin/lib/locale/common/$(DIR)

TARGETDIRS = $(TARGETDIR)

SUBDIRS = 

all:=		TARGET= all
install :=	TARGET= install
clean :=	TARGET= clean
clobber :=	TARGET= clobber

all: $(TARGETDIRS) $(XUCTBLGEN) $(EN_CONV_TABLES)
	$(INSDIR) $(FILEROOT)/usr/openwin/lib/locale/$(LOCALE)/$(DIR)
	XLOCALEDIR=$(FILEROOT)/usr/openwin/lib/locale $(XUCTBLGEN) -locale $(LOCALE)

include $(SRC)/src/Makefile.targ

install: all $(SUBDIRS)

$(HI_CONV_TABLES): $(HI_CONV_TABLES:%=$(FILEROOT)/usr/openwin/lib/locale/$(LOCALE)/$(DIR)/%)
	$(INS) $(FILEROOT)/usr/openwin/lib/locale/$(LOCALE)/$(DIR) $@

$(EN_CONV_TABLES): FRC
	grep -v '^#' $@ > $(@:%.txt=$(TARGETDIR)/%.txt)

$(XUCTBLGEN): 
	cd $(SRC)/src/cmd/xuctblgen/;make all

clean: objclean
	$(RM) -r $(TARGETDIR)
	$(RM) U32*

FRC:

