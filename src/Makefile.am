## Process this file with automake to produce Makefile.in
## $Id: Makefile.am,v 1.11 2003/07/12 10:25:41 mhe Exp $

SUBDIRS = libmhe ftp

bin_PROGRAMS = yafc

BUILT_SOURCES = yafcrc.h

yafc_SOURCES = main.c \
   alias.c cmd.c commands.c completion.c get.c fxp.c gvars.c lglob.c \
   help.c input.c local.c login.c list.c put.c rm.c tag.c \
   redir.c prompt.c transfer.c rc.c set.c ltag.c bookmark.c utils.c

noinst_HEADERS = \
   alias.h cmd.h completion.h commands.h transfer.h \
   gvars.h help.h input.h get.h put.h lglob.h \
   set.h syshdr.h redir.h login.h utils.h bookmark.h tag.h ltag.h prompt.h \
   redir.h rc.h

yafc_LDADD = ftp/libftp.a libmhe/libmhe.a ../lib/libfoo.a

yafc_DEPENDENCIES = $(yafc_LDADD) yafcrc.h
INCLUDES = -I. -I.. -I$(srcdir) -I$(top_srcdir)/lib \
-I$(top_srcdir)/src/ftp -I$(top_srcdir)/src/libmhe

DEFS = -DSYSCONFDIR=\"@sysconfdir@\" @DEFS@

CLEANFILES=*~ \#*\#
DISTCLEANFILES=.deps/* yafcrc.h

yafcrc.h: $(top_srcdir)/yafcrc.sample
	echo "const char *default_yafcrc = \"\"" > yafcrc.h
	cat $(top_srcdir)/yafcrc.sample | sed 's/\\/\\\\/g' | sed 's/"/\\\"/g' | sed 's/^\(.*\)$$/\"\1\\n\"/' >> yafcrc.h
	echo ";" >> yafcrc.h
