CC		= icc
CFLAGS		= -g -O2 -fdebug-prefix-map=/home/richard/debs/NONGIT/most/check/most-5.0.0a=. -fstack-protector-strong -Wformat -Werror=format-security -march=native -pipe -Wall -DUTF8 
LDFLAGS		= -Wl,-z,relro -Wl,--as-needed,--gc-sections,--print-gc-sections,--print-memory-usage,--stats
SLANG_INC	= 
SLANG_LIB	= -L/usr/lib/x86_64-linux-gnu -lslang
MISCLIBS	= 
RPATH		= -Wl,-R/usr/lib/x86_64-linux-gnu

#-----------------------------------------------------------------------------
# Location where object files are placed (Absolute path)
#-----------------------------------------------------------------------------
SRCDIR = /home/richard/debs/NONGIT/most/check/most-5.0.0a/src
OBJDIR = /home/richard/debs/NONGIT/most/check/most-5.0.0a/src/$(ARCH)objs

#----------------------------------------------------------------------------
# 5. Install location
#----------------------------------------------------------------------------
INSTALL		= /usr/bin/install -c
INSTALL_DATA	= ${INSTALL} -m 644
DESTDIR		=
prefix		= /usr/local
exec_prefix	= ${prefix}
datarootdir	= ${prefix}/share
BIN_DIR		= $(prefix)/bin
MAN_DIR		= $(datarootdir)/man
DOC_DIR		= $(datarootdir)/doc/most
SYS_INITFILE	= ${prefix}/etc/most.conf
MKINSDIR	= ../autoconf/mkinsdir.sh

DOC_FILES = most.doc README most-fun.txt lesskeys.rc most.rc changes.txt

#----------------------------------------------------------------------------
# Nothing below here should require changing.
#----------------------------------------------------------------------------
DEST_DOCDIR	= $(DESTDIR)$(DOC_DIR)
DEST_MANDIR	= $(DESTDIR)$(MAN_DIR)
DEST_BINDIR	= $(DESTDIR)$(BIN_DIR)
#
SHELL = /bin/sh
OBJS =  $(OBJDIR)/buffer.o $(OBJDIR)/cmd.o $(OBJDIR)/display.o $(OBJDIR)/edit.o $(OBJDIR)/file.o $(OBJDIR)/help.o $(OBJDIR)/keym.o $(OBJDIR)/keyparse.o $(OBJDIR)/line.o $(OBJDIR)/main.o $(OBJDIR)/most.o $(OBJDIR)/search.o $(OBJDIR)/sysdep.o $(OBJDIR)/window.o
OFILES =  buffer.o cmd.o display.o edit.o file.o help.o keym.o keyparse.o line.o main.o most.o search.o sysdep.o window.o

EXEC = most
CONFIG_H = config.h
INCS = $(SLANG_INC)
ALL_CFLAGS = $(CFLAGS) -Dunix $(INCS)
EXECLIBS = $(RPATH) $(SLANG_LIB) $(MISCLIBS) -lm
#
most_O_DEP = $(SRCDIR)/version.h
UPDATE_VERSION_SCRIPT = $(HOME)/bin/update_changes_version

COMPILE_CMD = $(CC) -c $(ALL_CFLAGS) -DMOST_SYSTEM_INITFILE='"$(SYS_INITFILE)"'
#
all: $(EXEC)
$(EXEC): $(OBJDIR) $(CONFIG_H) slangversion $(OBJDIR)/$(EXEC)
	@echo $(EXEC) created in $(OBJDIR)
$(OBJDIR)/$(EXEC): $(OBJS)
	cd $(OBJDIR); $(CC) $(OFILES) -o $(EXEC) $(LDFLAGS) $(EXECLIBS)
#
$(OBJDIR):
	-mkdir $(OBJDIR)
#
$(CONFIG_H) : $(SRCDIR)/sysconf.h
	/bin/cp $(SRCDIR)/sysconf.h $(CONFIG_H)
#
slangversion: $(OBJDIR)/chkslang
	$(OBJDIR)/chkslang $(EXEC) 20000
#
$(OBJDIR)/chkslang: $(OBJDIR)/chkslang.o
	$(CC) $(OBJDIR)/chkslang.o -o $(OBJDIR)/chkslang
#
$(SRCDIR)/version.h: $(SRCDIR)/../changes.txt
	if [ -x $(UPDATE_VERSION_SCRIPT) ]; then \
	  $(UPDATE_VERSION_SCRIPT) $(SRCDIR)/../changes.txt $(SRCDIR)/version.h; \
	fi
#
clean:
	/bin/rm -f $(OBJDIR)/* *~
distclean: clean
	/bin/rm -rf $(OBJDIR) Makefile sysconf.h
installdirs:
	$(MKINSDIR) $(DEST_DOCDIR)
	$(MKINSDIR) $(DEST_MANDIR)/man1
	$(MKINSDIR) $(DEST_BINDIR)
install: all installdirs
	$(INSTALL) -s $(OBJDIR)/most $(DEST_BINDIR)
	$(INSTALL_DATA) ../most.1 $(DEST_MANDIR)/man1
	@for i in $(DOC_FILES); \
	do \
		i=../$$i; \
		echo $(INSTALL_DATA) $$i $(DEST_DOCDIR); \
		$(INSTALL_DATA) $$i $(DEST_DOCDIR); \
		if [ "$$?" != "0" ]; then \
		  exit 1; \
		fi; \
	done
# The symlinks target is for my own private use.  It simply creates the object
# directory as a symbolic link to a local disk instead of an NFS mounted one.
symlinks:
	-/bin/rm -f $(ARCH)objs
	mkdir -p $(HOME)/sys/$(ARCH)/objs/most/src
	ln -s $(HOME)/sys/$(ARCH)/objs/most/src $(ARCH)objs
#---------------------------------------------------------------------------
# Rules (automatically generated)
#---------------------------------------------------------------------------

$(OBJDIR)/buffer.o : $(SRCDIR)/buffer.c $(DOT_O_DEPS) $(buffer_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(buffer_C_FLAGS) $(SRCDIR)/buffer.c

$(OBJDIR)/cmd.o : $(SRCDIR)/cmd.c $(DOT_O_DEPS) $(cmd_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(cmd_C_FLAGS) $(SRCDIR)/cmd.c

$(OBJDIR)/display.o : $(SRCDIR)/display.c $(DOT_O_DEPS) $(display_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(display_C_FLAGS) $(SRCDIR)/display.c

$(OBJDIR)/edit.o : $(SRCDIR)/edit.c $(DOT_O_DEPS) $(edit_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(edit_C_FLAGS) $(SRCDIR)/edit.c

$(OBJDIR)/file.o : $(SRCDIR)/file.c $(DOT_O_DEPS) $(file_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(file_C_FLAGS) $(SRCDIR)/file.c

$(OBJDIR)/help.o : $(SRCDIR)/help.c $(DOT_O_DEPS) $(help_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(help_C_FLAGS) $(SRCDIR)/help.c

$(OBJDIR)/keym.o : $(SRCDIR)/keym.c $(DOT_O_DEPS) $(keym_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(keym_C_FLAGS) $(SRCDIR)/keym.c

$(OBJDIR)/keyparse.o : $(SRCDIR)/keyparse.c $(DOT_O_DEPS) $(keyparse_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(keyparse_C_FLAGS) $(SRCDIR)/keyparse.c

$(OBJDIR)/line.o : $(SRCDIR)/line.c $(DOT_O_DEPS) $(line_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(line_C_FLAGS) $(SRCDIR)/line.c

$(OBJDIR)/main.o : $(SRCDIR)/main.c $(DOT_O_DEPS) $(main_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(main_C_FLAGS) $(SRCDIR)/main.c

$(OBJDIR)/most.o : $(SRCDIR)/most.c $(DOT_O_DEPS) $(most_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(most_C_FLAGS) $(SRCDIR)/most.c

$(OBJDIR)/search.o : $(SRCDIR)/search.c $(DOT_O_DEPS) $(search_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(search_C_FLAGS) $(SRCDIR)/search.c

$(OBJDIR)/sysdep.o : $(SRCDIR)/sysdep.c $(DOT_O_DEPS) $(sysdep_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(sysdep_C_FLAGS) $(SRCDIR)/sysdep.c

$(OBJDIR)/window.o : $(SRCDIR)/window.c $(DOT_O_DEPS) $(window_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(window_C_FLAGS) $(SRCDIR)/window.c

$(OBJDIR)/chkslang.o : $(SRCDIR)/chkslang.c $(DOT_O_DEPS) $(chkslang_O_DEP)
	cd $(OBJDIR); $(COMPILE_CMD) $(chkslang_C_FLAGS) $(SRCDIR)/chkslang.c

