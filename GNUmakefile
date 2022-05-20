# $Copyright: $
# Copyright (c) 1996 - 2022 by Steve Baker
# All Rights reserved
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
# Author  : Jeong Han Lee
# email   : jeonghan.lee@gmail.com
# Date    : 2022.05.08
#
# 2022-05-08 : Rewritten Makefile for Cross Compiler of Linux

TOP:=$(CURDIR)


DESTDIR?=
BINDIR?= $(PREFIX)bin
EXE = tree

INCDIR:=$(TOP)
SRCDIR:=$(TOP)

VPATH = $(INCDIR) $(SRCDIR)
CFLAGS += -I $(INCDIR)

SRCS=tree.c list.c hash.c color.c file.c filter.c info.c unix.c xml.c json.c html.c strverscmp.c
OBJS=$(addsuffix .o,$(basename $(SRCS)))

#
# Our target OS is linux-arm (Very old)
CFLAGS=-O2 -Wall -fomit-frame-pointer -std=gnu99

.PHONY: clean install uninstall 

#------------------------------------------------------------

all: $(EXE)

$(EXE): $(OBJS)
	$(LINK.c) $^ -o $@

%.o: %.c
	$(COMPILE.c) $(OUTPUT_OPTION) $<

clean:
	$(RM) -r $(EXE) $(OBJS)


install: $(BIN)
	install -DT -m 755 $(EXE) $(DESTDIR)/$(BINDIR)/$(EXE)

distclean: clean
	@$(RM) $(BIN)

uninstall: 
	$(RM) -v $(DESTDIR)/$(BINDIR)/$(EXE)

PRINT.%:
	@echo $* = $($*)
	@echo $*\'s origin is $(origin $*)

