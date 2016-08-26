rm = rm -rf
latex = lualatex
pdf_viewer = mupdf -r 160
presentation_pdf = presentation.pdf
figure_dir = fig


.SUFFIXES: .xcf .png
.xcf.png:
	convert -density 1024 -quality 100 ${.IMPSRC} ${.TARGET}

.SUFFIXES: .tex .pdf
.tex.pdf:
	: ${src::=${.IMPSRC:.tex=_tmp_by_make.tex}}
	cat ${.IMPSRC} | tr "、。" "，．" > ${src}
	${latex} --jobname=${.TARGET:.pdf=} ${src}
	${latex} --jobname=${.TARGET:.pdf=} ${src}
	${rm} ${src}

.PHONY: all
all: ${presentation_pdf}

.PHONY: clean
clean:
	${rm} *.pdf *.dvi *.aux *.log *.toc *.nav *.snm *.out doc_data.txt \
	      ${figure_dir}/*.png

.PHONY: view
view: ${presentation_pdf}
	${pdf_viewer} ${.ALLSRC}

${presentation_pdf}: beamerthemettipresentation.sty
