# ============================================================
#  EchoRay Research Paper — Build System
#  Requires: pdflatex + bibtex  (TeX Live or MiKTeX)
# ============================================================

MAIN     := main
OUTDIR   := build
TEXFLAGS := -interaction=nonstopmode -output-directory=$(OUTDIR)

.PHONY: all clean view

all: $(OUTDIR)/$(MAIN).pdf

$(OUTDIR):
	mkdir -p $(OUTDIR)

$(OUTDIR)/$(MAIN).pdf: $(OUTDIR) $(MAIN).tex references.bib sections/*.tex
	pdflatex $(TEXFLAGS) $(MAIN).tex
	bibtex   $(OUTDIR)/$(MAIN)
	pdflatex $(TEXFLAGS) $(MAIN).tex
	pdflatex $(TEXFLAGS) $(MAIN).tex
	@echo "✅  Build complete: $(OUTDIR)/$(MAIN).pdf"

clean:
	rm -rf $(OUTDIR)

view: $(OUTDIR)/$(MAIN).pdf
	xdg-open $(OUTDIR)/$(MAIN).pdf 2>/dev/null || open $(OUTDIR)/$(MAIN).pdf
