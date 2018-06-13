# M is the number of the target module
# TGT shd be the base of the tex file (filename without .tex extension)
# Finally we create $(TGT)_Slides.tex and $(TGT)_Handout.tex
M=04
TGT=04DataRepresentation
# include full name of dependencies
DEP=title.tex \
	$(TGT).tex
RM=/bin/rm
BIBTEX=bibtex
DVIPS=dvips
DVIPDF=dvipdf
LATEX=pslatex
TEX=pslatex
SLIDES=$(TGT)_Slides
HANDOUTS=$(TGT)_Handout

slides: $(TGT)_Slides.pdf
handouts: $(TGT)_Handout.pdf
all: slides handouts

%.dvi: %.tex $(DEP)
	$(LATEX) $<
	$(LATEX) $< # second time to get page numbers right.
%.ps: %.dvi
	$(DVIPS) -o $@ $?
%.pdf: %.dvi %.ps
	$(DVIPDF) $<

.PHONY: clean clobber fresh
clean: 
	-$(RM) -f $(TGT).dvi $(TGT).aux $(TGT).log
	-$(RM) -f $(TGT).toc $(TGT).idx $(TGT).bbl
	-$(RM) -f $(TGT).toc $(TGT).ind $(TGT).blg 
	-$(RM) -f $(TGT).nav $(TGT).snm $(TGT).vrb
	-$(RM) -f $(TGT).out
	-$(RM) -f $(HANDOUTS).dvi $(HANDOUTS).aux $(HANDOUTS).log
	-$(RM) -f $(HANDOUTS).toc $(HANDOUTS).idx $(HANDOUTS).bbl
	-$(RM) -f $(HANDOUTS).toc $(HANDOUTS).ind $(HANDOUTS).blg 
	-$(RM) -f $(HANDOUTS).nav $(HANDOUTS).snm $(HANDOUTS).vrb
	-$(RM) -f $(HANDOUTS).out
	-$(RM) -f $(SLIDES).dvi $(SLIDES).aux $(SLIDES).log
	-$(RM) -f $(SLIDES).toc $(SLIDES).idx $(SLIDES).bbl
	-$(RM) -f $(SLIDES).toc $(SLIDES).ind $(SLIDES).blg 
	-$(RM) -f $(SLIDES).nav $(SLIDES).snm $(SLIDES).vrb
	-$(RM) -f $(SLIDES).out

clobber: clean
	-$(RM) -f $(TGT).ps $(TGT).pdf
	-$(RM) -f $(HANDOUTS).ps $(HANDOUTS).pdf
	-$(RM) -f $(SLIDES).ps $(SLIDES).pdf

fresh: clobber all
