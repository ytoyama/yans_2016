rm = rm -rf
latex = lualatex
pdf_viewer = mupdf -r 88
image_viewer = feh -.
poster_pdf = poster.pdf
pdftk = pdftk
convert = convert


.SUFFIXES: .tex .pdf
.tex.pdf:
	: ${src::=${.IMPSRC:.tex=_tmp_by_make.tex}}
	cat ${.IMPSRC} | tr "、。" "，．" > ${src}
	${latex} --jobname=${.TARGET:.pdf=} ${src}
	${latex} --jobname=${.TARGET:.pdf=} ${src}
	${rm} ${src}

.PHONY: all
all: ${poster_pdf}

.PHONY: clean
clean:
	${rm} *.pdf *.dvi *.aux *.log *.toc *.nav *.snm *.out

.PHONY: view
view: ${poster_pdf}
	${pdf_viewer} ${.ALLSRC}

${poster_pdf}: beamerthemettiposter.sty
