# Makefile for self materials of ftp.kaist.ac.kr
# Author: Jaeho Shin <netj@sparcs.org>
# Created: 2008-06-22

FTPROOT=/mirror/ftp
FILES=.message index.html id_rsa.pub robots.txt

all: $(FILES:%=$(FTPROOT)/%)

index.html: index.html.in $(FTPROOT)
	cp -f $< $@
	chmod +w $@
	screen -Dm vim -u NONE -i NONE -n $@ \
	    +1 +'/\(begin\|end\) of contents' +'norm jVnkdk' \
	    +'r!./list-data-links $(FTPROOT)' \
	    +'norm VNj=ZZ'
	chmod a=r $@

robots.txt: generate-robots-txt.sh
	./$< >$@

.SECONDEXPANSION:
$(FTPROOT)/%: $$(@F)
	sudo -u mirror install -m a=r $< $@

