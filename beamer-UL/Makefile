# Fichier Makefile pour compiler les fichiers .Rnw en .tex
# Gabriel Crépeault-Cauchon
# last modif : 17/09/2019

MAINFILE = template_beamer_UL
RNWFILES = $(addsuffix .Rnw,$(filter-out $(basename ${MAINFILE}), $(basename $(wildcard *.Rnw))))
TEXFILES = $(addsuffix .tex,$(filter-out $(basename ${RNWFILES} ${MAINFILE}),$(basename $(wildcard *.tex))))



all: pdf

pdf: $(MAINFILE).pdf

tex: ${RNWFILES:.Rnw=.tex} 

%.tex: %.Rnw
	R CMD Sweave --encoding="utf-8" '$<'

$(MAINFILE).pdf: $(MAINFILE).tex ${RNWFILES:.Rnw=.tex} ${TEXFILES}
	latexmk -pdf '$<'

clean:
	latexmk -c
	rm -f *~ \#* .Rhistory
	rm -f *.bbl
	rm -f *.nav
	rm -f *.synctex.gz
	rm -f *.snm

view:
	open ${MAINFILE}.pdf