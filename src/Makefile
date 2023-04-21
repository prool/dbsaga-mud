CC      = gcc
#PROF   = -p
NOCRYPT =

# Uncomment the line below if you have problems with math functions
MATH_LINK = -lm

# Uncomment the two lines below if compiling on a Solaris box
#SOLARIS_FLAG = -Dsun -DSYSV
#SOLARIS_LINK = -lnsl -lsocket

#Uncomment the line below if you are getting a line like:
#interp.c:757: warning: int format, time_t arg (arg 7)
TIME = -DTIMEFORMAT

#Uncomment the line below if you are getting implicit decleration of re_exec
#REG = -DREGEX

#Uncomment the line below if you are getting undefined re_exec errors
NEED_REG = -lgnuregex

#Uncomment the line below if you are getting undefined crypt errors
#NEED_CRYPT = -NOCRYPT

#DBUGFLG = -DREQUESTS

#Uncomment the line below if you want a performance increase though beware
#your core files may not be as much of a benefit if you do.
#OPT_FLAG = -finline-functions -funroll-loops -fdefer-pop -fstrength-reduce

#Uncomment if you wish to enable the Mud Client Compression Protocol
#Comment it out it if you are compiling with Cygwin
OPT_FLAG = -DMCCP

C_FLAGS = $(OPT_FLAG) -O -g3 -Wall -Wuninitialized $(PROF) $(NOCRYPT) $(DBUGFLG) -DSMAUG $(SOLARIS_FLAG) $(TIME) $(REG) -fcommon
L_FLAGS = $(OPT_FLAG) $(PROF) $(SOLARIS_LINK) $(NEED_CRYPT) ${MATH_LINK} -lz

#D_FLAGS : For the DNS Slave process. No need in linking all the extra libs for this.
D_FLAGS = -g3 -O $(PROF) $(SOLARIS_LINK)

#Uncomment the next three comments below if you want to use IMC
#USE_IMC    = -DUSE_IMC

#IMC_OFILES = imc.o imc-mail.o imc-interp.o imc-util.o imc-config.o \
#        imc-events.o imc-version.o imc-mercbase.o ice.o icec.o icec-mercbase.o

#IMC_CFILES = imc.c imc-mail.c imc-interp.c imc-util.c imc-config.c \
#        imc-events.c imc-version.c imc-mercbase.c ice.c icec.c icec-mercbase.c

O_FILES = act_comm.o act_info.o act_move.o act_obj.o act_wiz.o ban.o \
          board.o boards.o bounty.o build.o clans.o colorize.o comm.o \
          comments.o const.o db.o deity.o editor.o fight.o finger.o grub.o \
          handler.o hashstr.o hiscores.o hotboot.o house.o ibuild.o ident.o \
          imm_host.o interp.o magic.o makeobjs.o malloc.o mapout.o marry.o \
          misc.o mpxset.o mud_comm.o mud_prog.o new_fun.o pfiles.o planes.o \
          planet.o player.o polymorph.o rare.o requests.o reset.o save.o \
          services.o shops.o skills.o skills_android.o skills_dbs.o skills_genie.o \
          space.o special.o stat_obj.o tables.o track.o update.o dns.o new_auth.o \
          md5.o

C_FILES = act_comm.c act_info.c act_move.c act_obj.c act_wiz.c ban.c \
          board.c boards.c bounty.c build.c clans.c colorize.c comm.c \
          comments.c const.c db.c deity.c editor.c fight.c finger.c grub.c \
          handler.c hashstr.c hiscores.c hotboot.c house.c ibuild.c ident.c \
          imm_host.c interp.c magic.c makeobjs.c malloc.c mapout.c marry.c \
          misc.c mpxset.c mud_comm.c mud_prog.c new_fun.c pfiles.c planes.c \
          planet.c player.c polymorph.c rare.c requests.c reset.c save.c \
          services.c shops.c skills.c skills_android.c skills_dbs.c\
          space.c special.c stat_obj.c tables.c track.c update.c dns.c skills_genie.c \
          new_auth.c md5.c

H_FILES = mud.h bet.h board.h finger.h hotboot.h house.h pfiles.h rare.h new_auth.h

all:
	make dbs

dbs: $(O_FILES)
	rm -f dbsaga
# prool: L_FLAGS is moved to end of line (for compiling in Ubuntu)
	$(CC) $(USE_IMC) -o dbsaga $(O_FILES) -lcrypt $(L_FLAGS)
	chmod g+w dbsaga
	chmod a+x dbsaga
	chmod g+w $(O_FILES)

dbs2: $(O_FILES)
	rm -f dbsaga2
	$(CC) $(L_FLAGS) $(USE_IMC) -o dbsaga2 $(O_FILES)
	chmod g+w dbsaga2
	chmod a+x dbsaga2
	chmod g+w $(O_FILES)

dns: resolver.o
	rm -f resolver
	$(CC) $(D_FLAGS) -o resolver resolver.o
	chmod g+w resolver
	chmod a+x resolver
	chmod g+w resolver.o

.c.o: mud.h
	$(CC) -c $(C_FLAGS) $(USE_IMC) $<

clean:
	rm -f *.o dbsaga *~
