OUTPUTDIR=tmp
DOCUMENT=questionnaire
MAIN   = $(DOCUMENT).pdf
TEXSRC =  questionnaire.tex

GRAPHSRC = 

SPELLCHECKED = $(SOURCES:%.tex=/tmp/%.spc)

.PHONY: default spellcheck clean edit show purge
.PRECIOUS: $(GRAPHSRC)

default: $(OUTPUTDIR)/$(MAIN)

%_dia.png: ../graphsrc/%.dia
	dia -e $@ $<

$(OUTPUTDIR)/%.pdf: $(TEXSRC) Makefile $(BIBTEX) 
	pdflatex -draftmode -file-line-error -halt-on-error -output-directory=$(OUTPUTDIR) $*
	pdflatex -output-directory=$(OUTPUTDIR) $*
	pdflatex -output-directory=$(OUTPUTDIR) $*

clean:
	rm -f *.log *.aux *.blg *.bbl *.zip *.dia~ *.spc
	rm -f tmp/$(DOCUMENT).log tmp/$(DOCUMENT).aux tmp/$(DOCUMENT).blg tmp/$(DOCUMENT).bbl tmp/*.spc tmp/$(DOCUMENT).pdf tmp/$(DOCUMENT).out tmp/$(DOCUMENT).toc
	rm -f graphsrc/*.dia~

purge: clean
	rm -f *.pdf *.ps *.bak

