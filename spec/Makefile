# vim:noet

BASENAME = vt-good-image-protocol

all: ${BASENAME}.pdf

clean:
	@rm -vf ${BASENAME}.pdf *.log *.aux *.toc

%.pdf: %.tex
	@pdflatex $^

.PHONY: all clean
