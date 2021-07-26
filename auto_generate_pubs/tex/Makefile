LATEX       = pdflatex
BASH        = bash -c
ECHO        = echo
RM          = rm -rf

TMP_SUFFS   = aux bbl blg log dvi ps eps out
RM_TMP      = ${RM} $(foreach suff, ${TMP_SUFFS}, *.${suff})

CHECK_RERUN = grep Rerun $*.log

ALL_FILES = pubs.pdf 

all: ${ALL_FILES}

%.pdf: %.tex cvstyle.tex pubs_firstsecond.tex pubs_nth.tex pubs_unref.tex ../data/pubs.json
	${LATEX} $<
	${LATEX} $<

cv_pubs.pdf: cv.tex pubs_*.tex cvstyle.tex ../data/pubs.json ../data/other_pubs.json
	${LATEX} -jobname=cv_pubs "\def\withpubs{}\input{cv}"
	${LATEX} -jobname=cv_pubs "\def\withpubs{}\input{cv}"

clean:
	${RM_TMP} ${ALL_FILES}
