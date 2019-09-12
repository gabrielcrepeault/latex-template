# ------------------------------------------------
# Makefile template used for LaTeX
# Gabriel Crépeault-Cauchon
# Last update : 11/09/2019
# ------------------------------------------------


# fichier Makefile pour LaTeX

# la fonction Sweave créé le fichier .tex
# la fonction Strangle créé le fichier .R qui extrait d'un Rnw les chunks
# la fonction pdflatex vient générer (comme à l'habitude) le pdf suite à la compilation d'un fichier .tex

# note : il est possible que votre compilateur LaTeX ne trouve pas instantanément le package Sweave.sty
# aller voir le site suivant : https://sapa-project.org/blog/2013/08/16/easy-sweaving-for-latex-and-r/
MASTER=111126819





all:
	R CMD Sweave *.Rnw
	R CMD Stangle *.Rnw
	pdflatex ${MASTER}.tex
	bibtex ${MASTER}
	pdflatex ${MASTER}.tex
	pdflatex ${MASTER}.tex
	open ${MASTER}.pdf

	rm -rf *.log *.nav *.out *.snm *.vrb *.toc Rplots* .RData
	# Afficher dans le viewer de TexMaker
	%.tex|txs:///view-pdf-internal

.PHONY: clean
clean:
	rm -rf *.log *.nav *.out *.snm *.vrb  *.aux *.bbl  *.blg *.lof *.lot *.toc Rplots* .RData
