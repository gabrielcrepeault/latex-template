# ===============================================================
# Fichier GNU Make pour compiler LaTeX, knitr et bibtex
# ===============================================================

# Déterminer les variables contenant les noms des différents fichiers de mon programme
MAINFILE = 111126819
RNWFILES = $(addsuffix .Rnw,$(filter-out $(basename ${MAINFILE}), $(basename $(wildcard *.Rnw))))
TEXFILES = $(addsuffix .tex,$(filter-out $(basename ${RNWFILES} ${MAINFILE}),$(basename $(wildcard *.tex))))


# Workflow de GNU Make
all: pdf

pdf: $(MAINFILE).pdf

tex: ${RNWFILES:.Rnw=.tex} 

%.tex: %.Rnw
	R -q -e "knitr::knit('$<')"

$(MAINFILE).pdf: $(MAINFILE).tex ${RNWFILES:.Rnw=.tex} ${TEXFILES}
	latexmk -pdf '$<'

clean:
	latexmk -c
	rm -f *~ \#* .Rhistory
	rm -f $(MAINFILE).bbl

view:
	open ${MAINFILE}.pdf