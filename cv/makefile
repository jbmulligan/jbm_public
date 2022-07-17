
#pdf:	latex dvips ps2pdf xpdf
#pdf:	xelatex dvips ps2pdf
pdf:	xelatex

#NAME = jbm_pubs
#NAME = jbm_cv
NAME = jbm_short_cv

# on the sun, this was ptroff
ROFF=	groff

splist.ps:	splist
	$(ROFF) -ms -t splist > splist.ps

rplist.ps:	rplist
	$(ROFF) -ms -t rplist > rplist.ps

srplist.ps:	srplist
	$(ROFF) -ms -t srplist > srplist.ps

plist.ps:	plist
	$(ROFF) -ms -t plist > plist.ps

vita2.ps:	vita2
	$(ROFF) -ms -t vita2 > vita2.ps

vita2.asc:	vita2
	$(ROFF) -ms -Tascii vita2 > vita2.asc

#vita.ps:	vita
vita.ps:	long_vita
	$(ROFF) -ms -t long_vita > vita.ps

docs:	plist.ps vita.ps

#cover.ps:	cover
#	$(ROFF) -ms -t cover > cover.ps

cover.tell.ps:	cover.tell
	$(ROFF) -ms -t cover.tell > cover.tell.ps

promo95.ps:	promo95.new
	$(ROFF) -ms -t promo95.new > promo95.ps
	
promo97.ps:	promo97
	$(ROFF) -ms -t promo97 > promo97.ps
	
cover.ps:	cover.tell97
	$(ROFF) -ms -t cover.tell97 > cover.ps

cover.nr:	cover.tell97
	nroff -ms cover.tell97 > cover.nr


# Run make first to get references right. You might have to rerun
# a couple of times. After you get the references you can run
# make pdf to get the pdf file...


#all:	xelatex bibtex xdvi
all:	xelatex xdvi
ps:	xelatex dvips gsv

PS2PDFOPTS =	-dPDFSETTINGS=/prepress \
		-dSubsetFonts=true \
		-dEmbedAllFonts=true \
		-dMaxSubsetPct=100 \
		-dCompatibilityLevel=1.3

xelatex:
	xelatex $(NAME)
#	bibtex $(NAME)
#	xelatex $(NAME)
	xelatex $(NAME)

bibtex:
	bibtex $(NAME)

dvips:
	dvips -t letter $(NAME).dvi -o $(NAME).ps

ps2pdf:
	ps2pdf $(PS2PDFOPTS) $(NAME).ps
#	cp $(NAME).pdf paper2649_review_copy.pdf

xpdf:
	kpdf $(NAME).pdf &

xdvi:
	xdvi $(NAME).dvi &

gsv:
	gs $(NAME).ps

clean:
	/bin/rm *~ *.out *.log *.dvi *.aux *.toc *.pdf *.ps *.bbl *.blg


