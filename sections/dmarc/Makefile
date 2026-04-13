## Variables
BUILD_DIR = build
LATEXMK = latexmk
BIBTEX = bibtex
BIBTEX_OPTS = -terse
LATEXMK_OPTS = -interaction=nonstopmode -halt-on-error -outdir=$(BUILD_DIR) -pdf -silent

## Sources and dependencies
SRC = main.tex
BUILD_DEP = $(wildcard *.tex) $(wildcard texenv/*.tex) $(wildcard figures/*) $(wildcard tables/*) references.bib

## Phony targets
#https://stackoverflow.com/questions/3148492/suppress-messages-in-make-clean-makefile-silent-remove
.SILENT .PHONY: all clean dirs

## Default target: build PDF
all: dirs main.pdf

## Create build directory
dirs:
	@mkdir -p $(BUILD_DIR)

## Compile and copy PDF to top level
main.pdf: $(SRC) $(BUILD_DEP)
	@$(LATEXMK) $(LATEXMK_OPTS) $(SRC)
	@$(LATEXMK) $(LATEXMK_OPTS) $(SRC)
	@$(BIBTEX) $(BIBTEX_OPTS) $(BUILD_DIR)/main
	@$(LATEXMK) $(LATEXMK_OPTS) $(SRC)
	@mv $(BUILD_DIR)/main.pdf $@

## Clean build artifacts and output
clean:
	@rm -rf $(BUILD_DIR) *.pdf

## Generate diff between two git commits
# Usage: make diff from=COMMIT1 to=COMMIT2
# Example: make diff from=HEAD~1 to=HEAD
diff:
ifndef from
	$(error 'from' commit hash is required. Usage: make diff from=COMMIT1 to=COMMIT2)
endif
ifndef to
	$(error 'to' commit hash is required. Usage: make diff from=COMMIT1 to=COMMIT2)
endif
	@echo "Generating diff from $(from) to $(to)..."
	git latexdiff --main $(SRC) --latexmk --latexopt "$(LATEXMK_OPTS)" $(from) $(to) --output main-diff.pdf
	@echo "Diff generated: main-diff.pdf"

live:
	latexmk -lualatex -shell-escape -f -pvc -interaction=nonstopmode $(SRC)
